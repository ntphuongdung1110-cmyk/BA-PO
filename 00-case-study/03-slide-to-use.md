# Case thực tế 2 — Rebuild Voucher: Slide to Use + Flow redeem code 3rd

> Nguồn: tài liệu một dự án thật (BRD, bảng Open Items, ghi chú họp review mockup), đã ẩn danh tên công ty, sản phẩm và team. File này tóm tắt các điểm **có trong tài liệu**. Phần suy luận học tập ghi `[Giả định bài tập]`.

## 1. Bối cảnh

Người nhận voucher mở Voucher Link E hoặc App ví quà, chọn thương hiệu, rồi **tách** voucher theo số tiền cần mua. Thương hiệu nhận mã nội bộ thì cấp mã nội bộ ngay. Một nhóm thương hiệu đối tác chỉ nhận **mã do chính họ phát hành** (code 3rd). Công ty lấy code 3rd theo hai nguồn:

| Nguồn | Công ty phát sinh chi phí khi nào |
|---|---|
| Mua trước theo kho | Khi nhập kho, trước khi người nhận dùng |
| Cấp theo từng lượt qua API | Mỗi lần hệ thống yêu cầu một mã |

## 2. Vấn đề (ví dụ Problem Statement tốt)

1. **Mã đối tác được cấp trước khi người nhận cần.** Hệ thống lấy code 3rd ngay khi tách, kể cả khi người nhận chưa định ra cửa hàng. Người nhận không dùng thì mã không thu hồi được. Kho cạn nhanh hơn nhu cầu thật; với nguồn cấp theo lượt, Công ty trả tiền cho mã không tạo giao dịch.
2. **Người nhận phải tự chia mệnh giá.** Bảng gợi ý mệnh giá dựng từ danh sách cố định, không kiểm tồn kho → chọn xong mới báo không đủ mã, phải làm lại.

## 3. Hướng giải quyết (TO-BE)

Tách hai việc đang xảy ra cùng lúc thành hai thời điểm:
- **Khi tách:** chỉ nhập số tiền, hệ thống tự chia mệnh giá. Ghi nhận redeem và doanh thu cho brand đã chọn, **chưa lấy code 3rd**.
- **Khi ra cửa hàng:** bấm Dùng ngay, **trượt thanh Slide to Use** thì hệ thống mới lấy mã.

| Loại brand | Lúc tách | Lúc trượt |
|---|---|---|
| Brand thường (nhận mã nội bộ) | Sinh voucher con mã nội bộ | Hiện mã nội bộ |
| Brand Cả hai (code 3rd trước, hết thì mã nội bộ) | Ghi redeem, voucher giữ state 3 kèm **bảng tạm** | Còn code: code 3rd. Hết code: mã nội bộ |
| Brand Chỉ code 3rd | Ghi redeem, voucher giữ state 3 kèm bảng tạm | Còn code: code 3rd. Hết code: báo tạm hết mã |

## 4. Mục tiêu và chỉ số (ví dụ KPI tốt)

| # | Mục tiêu | Chỉ số |
|---|---|---|
| MT-1 | Chỉ lấy mã đối tác khi người nhận thật sự dùng | Tỷ lệ voucher đã tách nhưng chưa lấy mã sau 30/60/90 ngày; số mã không phải xuất kho |
| MT-2 | Đơn giản hoá thao tác tách | Tỷ lệ lượt tách hoàn tất / lượt mở màn tách, so với trước phát hành |
| MT-3 | Người nhận luôn có mã ở brand Cả hai | Tỷ lệ chuyển sang mã nội bộ; không phát sinh khiếu nại "không lấy được mã" |
| MT-4 | Mỗi voucher chỉ dùng một lần | Không voucher nào bị ghi nhận dùng hai lần hoặc có hai dòng doanh thu |

Số liệu nền (baseline) cho MT-1, MT-2 được mở thành Open Item riêng (OI-BRD-01) — **không có baseline thì không chứng minh được cải thiện**.

## 5. Scope theo từng kênh (ví dụ Scope tốt)

| Kênh | Phase này |
|---|---|
| Voucher Link E (ví), App ví quà | Thay đổi |
| Link V mono chưa auto convert | Thay đổi (thay nút Xác nhận chuyển đổi bằng Slide to Use) |
| Link V mono auto convert | Giữ nguyên |
| Link V multi | Thay đổi |
| API phát hành, Bulk Order | Thay đổi một phần (API vẫn trả code cho client) |
| API kiểm tra trạng thái, POS, Đối soát, Report | Thay đổi |
| kênh Gift, Loyalty/Loyalty Hub | Chờ team liên quan đánh giá |
| Nhắn tin đổi code | Giữ nguyên |

Ngoài phạm vi: tự chuyển nguồn code theo ngưỡng tồn kho (đã bỏ), quy tắc brand được dùng voucher đã tách (thuộc ticket khác), mini app Zalo.

## 6. NFR đáng học

| # | Yêu cầu | Bài học |
|---|---|---|
| NFR-1 | Trượt nhiều lần, hoặc trên hai thiết bị cùng lúc, chỉ ra một kết quả và rút tối đa một code | Concurrency + idempotency ở UI action |
| NFR-2 | Kiểm bảng tạm và trừ voucher tại POS là một thao tác nguyên tử | Atomicity, race condition |
| NFR-3 | Ghi log lịch sử mọi thay đổi của bảng tạm và dòng doanh thu | Audit log cho CS và đối soát |
| NFR-4 | Các kênh giữ nguyên không đổi hành vi, QC chạy regression từng kênh | Regression scope |

## 7. Requirement Change thật (bài học Change Management)

- **14/10/2026:** chốt theo ADR — tách tại brand Cả hai thì voucher giữ "Còn dùng được", tạo bản ghi lấy mã với nhiều trạng thái.
- **15/10/2026 (lần 1):** đổi lại — áp cho brand Chỉ code 3rd + Cả hai, dùng state 3 + bảng tạm; Link V ngoài phạm vi.
- **15/10/2026 (lần 2):** brand Cả hai hết code → xoá bảng tạm **và huỷ dòng doanh thu lúc tách**; doanh thu ghi khi khách dùng mã nội bộ.
- **20/10/2026:** họp review mockup mở rộng phạm vi sang Link V (mono chưa auto convert, multi), API trạng thái, Report.

→ Ba lần đổi trong hai ngày, rồi mở rộng scope sau một tuần. Mỗi lần đổi đều kéo theo: cập nhật ADR, 4–5 FS, mockup, open items, và **một câu hỏi mới cho Kế toán** (huỷ dòng doanh thu bằng đánh dấu hay bút toán đảo — OI-S43). Đây là ví dụ thật của Impact Analysis và Decision Log.

## 8. Open Items tiêu biểu (ví dụ Discovery Question tốt)

| # | Câu hỏi | Vì sao quan trọng |
|---|---|---|
| OI-S43 | Kế toán có chấp nhận huỷ dòng doanh thu lúc tách và ghi lại khi khách dùng mã nội bộ? Huỷ bằng đánh dấu hay bút toán đảo? | Chặn một nhánh chức năng |
| OI-S15 | Brand Chỉ code 3rd hết kho kéo dài, voucher tới hạn: gia hạn, hoàn hay để hết hạn? | Khách bị tính redeem mà không nhận được mã |
| OI-S16 | Quy tắc tự chia mệnh giá: ít mã nhất, ưu tiên mệnh giá lớn, hay theo tồn kho? | Chưa có rule thì QC không viết được expected result |
| OI-S34 | Custom API của một số đối tác và POS khác có đi qua cùng logic kiểm tra không? | Sót kênh = rủi ro redeem voucher đã tính redeem |
| OI-S42 | Thời gian redeem cho đối soát client là ngày tách hay ngày lấy mã? | Kỳ đối soát lệch khi tách và trượt khác tháng |
| OI-S10 / S54 | Voucher phát hành trước ngày bật tính năng áp luồng mới hay cũ? | Rủi ro dữ liệu chuyển tiếp (migration) |
| OI-S06 | Đường thay thế cho thanh trượt (giữ nút 1 giây / nút phụ sau 5 giây)? | Trợ năng (accessibility) |
| OI-S23 | App bản cũ hiển thị voucher chưa hiện mã thế nào, có bắt buộc cập nhật App? | Backward compatibility |

Các câu "Đã đóng" trong bảng OI có ghi **ngày đóng + kết luận + rule liên quan** (VD: "Đã đóng 22/10/2026: được, voucher chưa gắn brand (BR-V16)"). Đây là cách viết Decision Log nên học theo.

## 9. Stakeholder thật của dự án

PO Voucher (chốt phạm vi), Tech Lead (giải pháp bảng tạm, POS), App ví quà (thời điểm phát hành), Kế toán (ghi và huỷ doanh thu), Design (UI thanh trượt, câu chữ), MC/CS (hướng dẫn khách, merchant), BA/QC, các team Team kênh A và Team kênh B (đánh giá kênh của họ).
