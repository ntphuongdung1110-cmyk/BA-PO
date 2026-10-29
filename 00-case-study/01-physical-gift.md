# Case xuyên suốt — Hệ thống Physical Gift / E-commerce (PG)

> Đây là case **giả lập** dùng cho toàn khóa. Mọi bài học, ví dụ, bài tập đều dùng chung tên entity, trạng thái và actor trong file này. Khi một bài cần thêm chi tiết, bài đó ghi rõ `[Giả định bài tập]`.

## 1. Bối cảnh

Công ty vận hành nền tảng quà tặng hiện vật (Physical Gift). Khách hàng doanh nghiệp (Client) mở **Program** quà tặng cho nhân viên hoặc khách hàng của họ. Người nhận (Recipient) chọn quà trong Program. Hệ thống tạo **Order**, tách thành nhiều **Sub-order** theo **Supplier**, gửi Supplier qua API. Supplier đóng gói, bàn giao cho **Delivery Service** (đơn vị vận chuyển). Cuối tháng đối soát với Supplier và Client.

```
Product → SKU → Supplier → Inventory → Program → Customer Account
        → Order → Sub-order → Delivery → Re-delivery → Reconciliation → Reporting
```

## 2. Quan hệ dữ liệu cốt lõi

| Quan hệ | Ý nghĩa |
|---|---|
| Product 1–N SKU | Một Product (VD: "Bình giữ nhiệt Lock&Lock") có nhiều SKU (màu, dung tích) |
| SKU N–N Supplier | Một SKU có thể được nhiều Supplier cung cấp → bảng nối `supplier_sku` (giá vốn, ưu tiên, active) |
| Supplier + SKU 1–1 Inventory | Tồn kho tính theo cặp (Supplier, SKU) |
| Program N–N SKU | Một Program bán nhiều SKU, một SKU nằm trong nhiều Program → bảng `program_sku` (giá/điểm riêng) |
| Customer Account 1–N Program | Một Client có nhiều Program |
| Order 1–N Sub-order | Một Order tách theo Supplier |
| Sub-order N–1 Supplier | Mỗi Sub-order thuộc đúng một Supplier |
| Sub-order 1–N Order Item | Mỗi dòng hàng là một SKU + số lượng |
| Sub-order 1–N Shipment | Lần giao đầu + các lần Re-delivery |

## 3. Entity và field chính

| Entity | Field chính |
|---|---|
| `product` | product_id, name, category, brand, status (ACTIVE / INACTIVE) |
| `sku` | sku_id, product_id, variant, list_price, weight, status (ACTIVE / INACTIVE / DISCONTINUED) |
| `supplier` | supplier_id, name, integration_type (API / MANUAL), confirm_sla_minutes, status |
| `supplier_sku` | supplier_id, sku_id, cost_price, priority, is_active |
| `inventory` | supplier_id, sku_id, available_qty, reserved_qty, updated_at |
| `customer_account` | account_id, name, type (CLIENT), credit_limit, api_key_id, status |
| `program` | program_id, account_id, name, start_at, end_at, budget, status (DRAFT / ACTIVE / PAUSED / ENDED) |
| `program_sku` | program_id, sku_id, price_or_point, is_visible |
| `order` | order_id, program_id, account_id, client_ref_id, recipient_name, phone, address, total_amount, status, created_at |
| `sub_order` | sub_order_id, order_id, supplier_id, status, shipping_status, sent_at, confirmed_at |
| `order_item` | item_id, sub_order_id, sku_id, qty, unit_price |
| `shipment` | shipment_id, sub_order_id, carrier, tracking_no, attempt_no, status, failed_reason |
| `reconciliation` | recon_id, period, party_type (SUPPLIER / CLIENT), party_id, status, total_amount |
| `audit_log` | log_id, entity, entity_id, action, before, after, actor, reason, created_at |

## 4. Trạng thái chuẩn (dùng thống nhất toàn khóa)

**Order.status:** `CREATED → CONFIRMED → PARTIALLY_SHIPPED → COMPLETED`, nhánh `CANCELLED`.

**Sub-order.status (xử lý với Supplier):** `PENDING → SENT_TO_SUPPLIER → SUPPLIER_CONFIRMED`, nhánh `SUPPLIER_REJECTED`, `CANCELLED`.

**Sub-order.shipping_status (vận chuyển):** `NOT_SHIPPED → PICKED_UP → IN_TRANSIT → DELIVERED`, nhánh `DELIVERY_FAILED → (Re-delivery) PICKED_UP` hoặc `RETURNED`.

Order.status là trạng thái **tổng hợp** từ các Sub-order. Junior hay quên điều này và cho Order tự đổi trạng thái độc lập.

## 5. Actor

| Actor | Vai trò |
|---|---|
| Client (B2B) | Tạo Program, gọi API tạo Order, xem báo cáo |
| Recipient | Người nhận quà, chọn quà, nhận hàng |
| Operator (Ops) | Theo dõi Order, xử lý ngoại lệ, re-delivery |
| Admin | Cấu hình Product, SKU, Supplier, Program, phân quyền |
| Supplier | Nhận Sub-order, confirm/reject, đóng gói |
| Delivery Service | Lấy hàng, giao hàng, gửi webhook trạng thái |
| Finance / Kế toán | Đối soát Supplier, Client, công nợ |
| CS (CSKH) | Trả lời khiếu nại của Recipient/Client |
| Sales / AM | Quản lý quan hệ Client, theo dõi Program |
| Management | Duyệt ưu tiên, ngân sách, KPI |

## 6. Integration

| Luồng | Hướng | Cơ chế |
|---|---|---|
| Tạo Order | Client → PG | `POST /orders` (có `client_ref_id` để chống trùng) |
| Lấy danh sách quà | Client → PG | `GET /programs/{id}/products` |
| Gửi Sub-order | PG → Supplier | `POST` sang API Supplier, Supplier callback confirm/reject |
| Cập nhật vận chuyển | Delivery Service → PG | Webhook `shipment.status_changed` |
| Thông báo cho Client | PG → Client | Webhook `order.status_changed` |
| Đồng bộ tồn kho | Supplier → PG | Định kỳ hoặc webhook (đề bài Capstone) |

## 7. Pain point đã biết (dùng cho bài tập)

1. Client hiển thị Product đã INACTIVE hoặc hết hàng → Recipient chọn xong mới báo lỗi (Capstone).
2. Supplier không confirm Sub-order trong SLA → Order treo.
3. Giao thất bại, Ops re-delivery thủ công qua Excel.
4. Admin muốn sửa Order sau khi tạo (đổi địa chỉ, đổi SKU).
5. Cuối tháng đối soát Supplier lệch số do Sub-order huỷ muộn.
6. Client gọi API tạo Order hai lần khi timeout → hai Order.
