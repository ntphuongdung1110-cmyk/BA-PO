# Case thực tế 1 — Promotion Code Warehouse (Phase 1 MVP)

> Nguồn: tài liệu một dự án thật (BRD Phase 1 MVP và ghi chú rà soát), đã ẩn danh tên công ty, sản phẩm và team. File này chỉ tóm tắt các điểm **có trong tài liệu**, dùng làm ví dụ thật cho các bài học. Phần nào là suy luận học tập sẽ ghi `[Giả định bài tập]`. Tham số trong ngoặc vuông `[ ]` là giá trị mặc định cấu hình được.

## 1. Bài toán

Công ty xây module Promotion Code để bán mã ưu đãi của merchant cho ngân hàng, bảo hiểm (qua API) và khách hàng Loyalty Hub. Điểm khác e-voucher hiện tại: **một mã của merchant có thể được phát và tính phí nhiều lần**. Nếu người dùng không vuốt mở mã trong [7] ngày, mã quay về kho và được phát cho người khác.

Mục tiêu Phase 1:
- Đưa mã từ file Excel của merchant vào kho, phát qua API và Loyalty Hub, đối soát được cuối tháng.
- Chứng minh mô hình phát lại mã chưa vuốt hoạt động an toàn trong pilot.
- Không ảnh hưởng luồng e-voucher đang chạy.

## 2. Ý tưởng mô hình dữ liệu (bài học Data Modeling)

Tách **Mã** (merchant giao) khỏi **Lượt phát** (mỗi lần mã được gán cho một người dùng). Một mã có nhiều lượt phát theo thời gian, nhưng tại một thời điểm **tối đa một lượt phát còn hiệu lực**.

| Đối tượng | Ý nghĩa |
|---|---|
| Merchant | Đối tác cấp mã |
| SKU | Một loại ưu đãi (điều kiện, kiểu hiển thị, barcode) |
| Lô | Một lần nhập file (người nhập, người duyệt, số mã hợp lệ / lỗi) |
| Mã | Mã vật lý (mã hoá khi lưu), HSD gốc, trạng thái, số lần đã phát |
| Lượt phát | Serial (Công ty tạo), ref ID (khách gửi), mã người dùng đã băm, các mốc thời gian, trạng thái, phí |
| Hạn mức | Số lượt khách được phát theo SKU, campaign |
| Bảng giá | Điều khoản tính phí theo hợp đồng |
| Dòng redeem | Một lượt merchant báo đã dùng, kết quả đối chiếu |

Kho của khách chỉ là **hạn mức**, không giữ mã vật lý.

## 3. Business Rule tiêu biểu (trích BRD mục 5)

| # | Rule |
|---|---|
| Nhập kho | Lô trên [5.000] mã cần Merchant Lead duyệt. Mã dưới [14] ngày HSD lúc nhập: cảnh báo, Lead quyết định |
| Phát mã | Chỉ phát mã còn ≥ [14] ngày HSD gốc. Ưu tiên mã gần hết hạn (FEFO) |
| Phát mã | Không phát khi khách hết hạn mức hoặc vượt hạn mức công nợ |
| Phát mã | API 2 bước: giữ chỗ → xác nhận. Không xác nhận sau [15] phút thì mã về kho, không tính phí |
| Phát mã | Loyalty Hub: trừ điểm và tạo lượt phát trong cùng một giao dịch; một bước lỗi thì cả hai huỷ |
| Chặn trùng | Cùng ref ID gửi lại → trả đúng lượt phát cũ, không tạo mới, không tính phí lần hai |
| Chặn trùng | Một mã không bao giờ có hai lượt phát còn hiệu lực cùng lúc |
| Vuốt | Mã chỉ trả về qua endpoint vuốt (reveal), không bao giờ trả lúc phát |
| Vuốt | Sau vuốt có [7] ngày để dùng, không vượt HSD gốc. Tặng người khác chỉ trước khi vuốt |
| Thu hồi | Job hằng ngày [00:30]: lượt chưa vuốt quá hạn → đóng, trả mã về kho, gửi webhook. Không hoàn phí |
| Thu hồi | Đã vuốt mà hết hạn dùng → Chờ merchant xác nhận. Phase 1 không tự phát lại |
| Giới hạn | Mỗi mã phát tối đa [3] lần |

## 4. API cho khách hàng (đề xuất trong BRD)

| Endpoint | Mục đích | Ghi chú |
|---|---|---|
| `GET /promo/catalog` | SKU khách được bán, giá, hạn mức còn lại | |
| `POST /promo/issuances` | Giữ chỗ một lượt phát | Vào: ref ID, SKU, campaign, mã người dùng đã băm. Ra: serial, link, hạn xác nhận. **Không trả mã** |
| `POST /promo/issuances/{serial}/confirm` | Xác nhận, từ đây tính phí | |
| `POST /promo/issuances/{serial}/reveal` | Người dùng vuốt mở mã | Trả mã, PIN, barcode/QR, hạn dùng |
| `POST /promo/issuances/{serial}/mark-used` | Người dùng bấm đã dùng | |
| `GET /promo/issuances/{serial}` | Tra cứu | |

Webhook gửi khách: `issuance.reminder` (D-3, D-1), `issuance.revealed`, `issuance.reclaimed`, `issuance.used`, `issuance.expired`.

## 5. Phân quyền (BRD mục 10)

| Vai trò | Quyền |
|---|---|
| Merchant Executive | Nhập lô, đề xuất hạn mức, nhập file redeem, chuẩn bị danh sách chờ merchant xác nhận |
| Merchant Lead | Duyệt lô lớn, duyệt trả mã về kho thủ công, xử lý tranh chấp |
| Kế toán | Chỉ xem; xuất báo cáo nghiệm thu, phải trả merchant, doanh thu |
| Sales / AM | Chỉ xem hạn mức, lượt phát của khách mình phụ trách |
| CSKH | Tra cứu theo serial hoặc ref ID, không thấy toàn bộ mã |

Bảo mật: mã mã hoá khi lưu, admin luôn che một phần mã; mỗi lần reveal ghi thời điểm và thiết bị; không lưu số điện thoại/CIF gốc, chỉ lưu băm; mọi thao tác admin ghi log ai, lúc nào, trước và sau.

## 6. Đối soát redeem với merchant (BRD mục 7)

| Kết quả | Điều kiện | Xử lý |
|---|---|---|
| Hợp lệ | Mã do Công ty phát, đã vuốt, redeem trong hạn dùng, chưa từng thanh toán | Đưa vào phải trả merchant, đóng mã |
| Tranh chấp: chưa vuốt | Redeem khi lượt phát chưa vuốt | Nghi lộ mã, khoá mã, báo Lead |
| Tranh chấp: ngoài hạn | Redeem sau hạn dùng | Chưa trả, chờ giải trình |
| Tranh chấp: trùng | Mã đã được thanh toán | Không trả lần hai |
| Không tồn tại | Mã không có trong kho | Loại bỏ |

## 7. Bài học thật cho BA/PO (từ vòng rà soát 18/09/2026)

Các phát hiện này là **ví dụ rất tốt cho Senior thinking**:

1. **Rule hiện hành chặn tính năng mới.** User Guide ghi "số lượng phân bổ không được lớn hơn Khả dụng", trong khi over-issue cần phát nhiều lượt hơn số mã. Không nới rule cũ thì đợt sau không chạy được — và việc này chưa có trong estimate. → Bài học: Impact Analysis phải rà cả rule đang chạy, không chỉ rule mới.
2. **KPI không đo được bằng hệ thống hiện tại.** KPI là tỷ lệ redeem thật tại merchant, nhưng với mã merchant cấp, Công ty chỉ biết mã đã rời kho. → Bài học: chọn KPI phải hỏi "dữ liệu ở đâu ra?".
3. **Hai nguồn tài liệu mâu thuẫn về mô hình doanh thu** (theo mã được dùng vs theo mã phát ra). → Bài học: Requirement Conflict, phải chọn nguồn có thẩm quyền.
4. **FIFO vs FEFO** chưa chốt giữa brief BOD và tài liệu kho. → Bài học: Decision Log.
5. **Trần phát hành đã tồn tại một phần** dưới tên khác. → Bài học: Document Analysis trước khi đề xuất build mới, tránh build trùng.
6. **Giả định nền bị sản xuất phá vỡ:** giả định "một chương trình một nguồn mã", nhưng thực tế đã có brand chạy nhiều nguồn mã + fallback. → Bài học: Observation hệ thống thật, không tin giả định.

## 8. Tiêu chí nghiệm thu MVP (trích BRD mục 12)

- File 10.000 mã có lẫn trùng và sai mẫu: báo đúng số dòng lỗi, chỉ nhập mã hợp lệ sau khi duyệt.
- Gọi phát mã 2 lần cùng ref ID: chỉ 1 lượt phát và 1 lần tính phí.
- Giữ chỗ không xác nhận sau 15 phút: mã về kho, không tính phí.
- Phản hồi phát mã không chứa giá trị mã; mã chỉ xuất hiện sau reveal.
- Lượt chưa vuốt sau 7 ngày: mã về kho, webhook `issuance.reclaimed` gửi đi, mã được phát lại với serial mới.
- Loyalty Hub: đổi điểm lỗi giữa chừng thì không trừ điểm và không tạo lượt phát.
- Luồng e-voucher hiện tại không bị ảnh hưởng (chạy lại regression).
