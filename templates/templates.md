# 30 Template thực hành BA/PO

> Mỗi template có: **khi dùng**, **khung**, và **ví dụ điền mẫu** ngắn (case Physical Gift, hoặc case thật Promotion Code / Slide to Use).
> Copy khung, giữ ID, thay nội dung. Ô nào chưa biết thì ghi `TBD → OI-xx`, không đoán.

## Mục lục

| # | Template | Dùng ở Day |
|---|---|---|
| 1 | [Problem Statement](#1-problem-statement) | 5, 50 |
| 2 | [Business Context](#2-business-context) | 5, 50 |
| 3 | [Stakeholder List](#3-stakeholder-list) | 8, 50 |
| 4 | [Discovery Question List](#4-discovery-question-list) | 7, 50 |
| 5 | [AS-IS](#5-as-is) | 10, 51 |
| 6 | [Pain Point](#6-pain-point) | 10, 51 |
| 7 | [Root Cause Analysis](#7-root-cause-analysis) | 11, 51 |
| 8 | [TO-BE](#8-to-be) | 12, 51 |
| 9 | [Scope](#9-scope) | 15, 52 |
| 10 | [Assumption](#10-assumption) | 15 |
| 11 | [Constraint](#11-constraint) | 15 |
| 12 | [Dependency](#12-dependency) | 15, 49 |
| 13 | [Business Requirement](#13-business-requirement) | 16 |
| 14 | [Functional Requirement](#14-functional-requirement) | 16 |
| 15 | [Non-functional Requirement](#15-non-functional-requirement) | 16 |
| 16 | [Business Rule Catalogue](#16-business-rule-catalogue) | 17, 52 |
| 17 | [Use Case](#17-use-case) | 18 |
| 18 | [User Story](#18-user-story) | 19, 54 |
| 19 | [Acceptance Criteria](#19-acceptance-criteria) | 20, 54 |
| 20 | [Functional Specification](#20-functional-specification) | 21, 54 |
| 21 | [API Requirement](#21-api-requirement) | 34, 53 |
| 22 | [Data Dictionary](#22-data-dictionary) | 23, 54 |
| 23 | [Error Code Matrix](#23-error-code-matrix) | 34, 53 |
| 24 | [Permission Matrix](#24-permission-matrix) | 25 |
| 25 | [Impact Analysis](#25-impact-analysis) | 45, 55 |
| 26 | [Requirement Traceability Matrix](#26-requirement-traceability-matrix) | 21 |
| 27 | [UAT Scenario](#27-uat-scenario) | 46, 55 |
| 28 | [Go-live Checklist](#28-go-live-checklist) | 47, 55 |
| 29 | [Product KPI](#29-product-kpi) | 42, 56 |
| 30 | [Post-release Review](#30-post-release-review) | 47, 56 |

---

## 1. Problem Statement

**Khi dùng:** ngay sau khi nhận request, trước khi bàn solution.

```
Context:        Hiện tại quy trình/hệ thống vận hành thế nào?
Problem:        Vấn đề cụ thể là gì? (1–2 câu, không chứa solution)
Who:            Ai bị ảnh hưởng?
Evidence:       Số liệu / ticket / ví dụ chứng minh
Impact:         Mất gì? (tiền, thời gian, khách, rủi ro)
Goal:           Kết quả mong muốn (đo được)
Success Metric: Chỉ số + baseline + target + thời hạn
Not a goal:     Điều không nhắm tới lần này
```

**Ví dụ (Slide to Use, rút gọn từ BRD):**
- Context: Khi người nhận tách voucher tại brand chỉ nhận mã đối tác, hệ thống lấy mã đối tác ngay.
- Problem: Mã đối tác được cấp trước khi người nhận cần. Không dùng thì không thu hồi được.
- Impact: Kho cạn nhanh hơn nhu cầu thật; với nguồn cấp theo lượt, Công ty trả tiền cho mã không tạo giao dịch.
- Success Metric: Tỷ lệ voucher đã tách nhưng chưa lấy mã sau 30/60/90 ngày; baseline: `TBD → OI-BRD-01`.

**Kiểm tra:** Problem có chứa chữ "cần làm nút/màn hình…" không? Có → bạn đang viết solution.

## 2. Business Context

```
Business model liên quan:   (ai trả tiền ai, khi nào)
Sản phẩm / kênh hiện có:
Quy mô:                     (số order/ngày, số client, số supplier…)
Quy định / hợp đồng liên quan:
Thay đổi gần đây:           (vì sao vấn đề nổi lên bây giờ)
Tài liệu tham chiếu:
```

## 3. Stakeholder List

| ID | Stakeholder | Vai trò trong feature | Quan tâm điều gì | Power (H/M/L) | Interest (H/M/L) | Decision right | Cách tương tác | Tần suất |
|---|---|---|---|---|---|---|---|---|
| SH-01 | Operation Lead | User chính màn Order | Ít thao tác tay | M | H | Duyệt flow vận hành | Workshop | Hằng tuần |
| SH-02 | Kế toán | Đối soát | Số liệu khớp, có log | H | M | Duyệt cách ghi doanh thu | Review tài liệu | Theo mốc |

## 4. Discovery Question List

| ID | Nhóm | Câu hỏi | Hỏi ai | Vì sao hỏi (ảnh hưởng gì) | Trả lời | Trạng thái |
|---|---|---|---|---|---|---|
| Q-01 | WHY | Nếu không làm thì mất gì mỗi tháng? | Sponsor | Quyết định ưu tiên | | Open |
| Q-02 | WHO | Ai được làm, ai duyệt? | Ops Lead | Permission | | Open |
| Q-03 | WHAT | Thay đổi field/data nào? | Ops | Data impact | | Open |
| Q-04 | WHEN | Ở status nào được phép? | Ops, Tech | State rule | | Open |
| Q-05 | WHERE | Kênh nào: UI, API, batch? | Tech | Scope | | Open |
| Q-06 | HOW | Hiện đang làm tay thế nào? | Ops | AS-IS | | Open |
| Q-07 | WHAT IF | Timeout / gửi trùng / 2 người cùng sửa? | Tech | Exception | | Open |
| Q-08 | DATA | Nguồn dữ liệu, owner, audit? | DA, Tech | Data | | Open |
| Q-09 | SUCCESS | Đo thành công bằng gì? | Sponsor | KPI | | Open |

## 5. AS-IS

```
Tên quy trình:
Trigger:              (cái gì bắt đầu quy trình)
Actor / hệ thống:
Các bước:             (đánh số; mỗi bước: ai – làm gì – trên công cụ gì – dữ liệu vào/ra – thời gian)
Kết thúc:
Ngoại lệ đang gặp:
Công cụ ngoài hệ thống: (Excel, Slack, email…)
Số liệu:              (volume, thời gian xử lý, tỷ lệ lỗi)
Sơ đồ:                (link/mermaid)
```

| Bước | Actor | Hành động | Công cụ | Input | Output | Thời gian | Pain point |
|---|---|---|---|---|---|---|---|
| 1 | Delivery Service | Báo giao thất bại | Webhook | shipment_id | DELIVERY_FAILED | – | Không có lý do chuẩn hoá |
| 2 | Ops | Gọi Recipient xác nhận lại địa chỉ | Điện thoại | SĐT | Địa chỉ mới | 10' | Làm tay, không log |

## 6. Pain Point

| ID | Pain point | Ai chịu | Tần suất | Mức độ (1–5) | Evidence | Bước AS-IS | Ghi chú |
|---|---|---|---|---|---|---|---|
| PP-01 | Re-delivery làm qua Excel | Ops | 30 ca/ngày `[Giả định]` | 4 | File Excel tháng 9 | 2–4 | Không đối soát được số lần giao |

## 7. Root Cause Analysis

**5 Whys**

| Why | Câu hỏi | Trả lời | Evidence |
|---|---|---|---|
| 1 | Vì sao Recipient chọn được quà hết hàng? | Client hiển thị danh sách cũ | Log order fail |
| 2 | Vì sao danh sách cũ? | Client chỉ gọi lấy danh sách 1 lần/ngày | Log API |
| 3 | Vì sao 1 lần/ngày? | Không có cơ chế báo thay đổi | Tài liệu API |
| 4 | … | | |
| 5 | Root cause: | | |

**Fishbone:** People · Process · System · Data · Partner · Policy → nguyên nhân con dưới mỗi nhánh.

**Kết luận:** Root cause → Bằng chứng → Đề xuất hướng xử lý → Root cause nào **không** xử lý lần này và vì sao.

## 8. TO-BE

```
Mục tiêu TO-BE (gắn Problem Statement):
Thay đổi chính so với AS-IS: (bảng bên dưới)
Bước bị loại bỏ / tự động hoá:
Rule mới:
Vai trò thay đổi:
Rủi ro chuyển đổi:
```

| AS-IS | TO-BE | Pain point giải quyết | Ai bị ảnh hưởng |
|---|---|---|---|
| Lấy mã đối tác lúc tách | Lấy mã lúc khách trượt Slide to Use | Mã bị lấy khi chưa cần | Khách, Kế toán, POS |

## 9. Scope

| Hạng mục | In scope | Out of scope | Lý do / Phase sau |
|---|---|---|---|
| Kênh | Link E, App | Mini app Zalo | Không làm phase này |
| Brand | Cả hai, Chỉ code 3rd | Tự chuyển nguồn theo ngưỡng | Đã bỏ |

Thêm: **Giữ nguyên (không đổi hành vi)** — liệt kê riêng để QC chạy regression.

## 10. Assumption

| ID | Giả định | Nếu sai thì sao | Ai xác nhận | Hạn | Trạng thái |
|---|---|---|---|---|---|
| AS-01 | Supplier gửi callback trong 30 phút | Order treo, cần job quét | Supplier Manager | dd/mm | Open |

## 11. Constraint

| ID | Ràng buộc | Loại (Thời gian / Ngân sách / Kỹ thuật / Pháp lý / Hợp đồng) | Ảnh hưởng tới thiết kế |
|---|---|---|---|
| CO-01 | Không lưu SĐT dạng gốc | Pháp lý | Chỉ lưu hash, CS tra theo serial |

## 12. Dependency

| ID | Phụ thuộc | Bên cung cấp | Cần gì | Hạn cần | Rủi ro nếu trễ | Owner theo dõi | Trạng thái |
|---|---|---|---|---|---|---|---|
| DE-01 | Kế toán chốt cách huỷ dòng doanh thu | Kế toán | Quyết định | dd/mm | Chặn 1 nhánh chức năng | PO | Waiting |

## 13. Business Requirement

| ID | Business Requirement | Mục tiêu business | Metric | Owner | Priority |
|---|---|---|---|---|---|
| BR-01 | Giảm order thất bại do Recipient chọn quà không còn bán | Giảm khiếu nại, giảm thao tác Ops | Tỷ lệ order fail do unavailable < 1% | Head of Ops | Must |

**Quy tắc:** BR nói **điều business cần đạt**, không nói màn hình hay API.

## 14. Functional Requirement

| ID | Trace BR | Hệ thống phải… | Điều kiện | Kết quả quan sát được | Priority |
|---|---|---|---|---|---|
| FR-01 | BR-01 | Gửi event `sku.availability_changed` cho Client đã đăng ký | Khi SKU đổi status hoặc available_qty về 0 | Client nhận event trong ≤ 2 phút | Must |

**Cấu trúc câu:** `Hệ thống phải <động từ> <đối tượng> khi <điều kiện>`. Một FR một hành vi.

## 15. Non-functional Requirement

| ID | Nhóm | Requirement (đo được) | Cách kiểm |
|---|---|---|---|
| NFR-01 | Performance | `POST /orders` p95 ≤ 800 ms ở 50 req/s | Load test |
| NFR-02 | Availability | Uptime API ≥ 99,9%/tháng | Monitoring |
| NFR-03 | Security | Payload webhook ký HMAC-SHA256 | Test chữ ký sai bị từ chối |
| NFR-04 | Audit | Mọi thay đổi Order ghi before/after, actor, reason | Kiểm bảng audit |
| NFR-05 | Concurrency | 2 thao tác đồng thời trên một voucher chỉ ra một kết quả | Test song song |

Nhóm gợi ý: Performance, Scalability, Availability, Reliability, Security, Privacy, Audit, Usability, Accessibility, Compatibility, Maintainability, Data retention.

## 16. Business Rule Catalogue

| BR ID | Tên | Rule (IF / AND / THEN / ELSE) | Tham số | Nguồn | Owner | Áp dụng ở | Trạng thái |
|---|---|---|---|---|---|---|---|
| BR-ORD-002 | Sửa Order theo status | IF order.status = CREATED AND chưa có sub_order SENT_TO_SUPPLIER THEN cho sửa địa chỉ ELSE báo "Order đã gửi Supplier, không sửa được" | – | Ops workshop dd/mm | Ops Lead | UI, API | Approved |
| BR-PRM-06 | Giữ chỗ hết hạn | IF lượt phát ở trạng thái giữ chỗ AND quá [15] phút chưa confirm THEN trả mã về kho, không tính phí | [15] phút | BRD Promotion Code | PO | API, Job | Approved |

**Rule tốt:** atomic (một ý), có điều kiện rõ, có ELSE khi cần, có tham số tách riêng, có nguồn.

## 17. Use Case

```
UC ID / Tên:
Actor chính:             Actor phụ:
Mục tiêu:
Trigger:
Pre-condition:
Post-condition (thành công):
Post-condition (thất bại):
Main Flow:
  1. …
  2. …
Alternative Flow:
  A1 (tại bước n): …
Exception Flow:
  E1 (tại bước n): …
Business Rules áp dụng:  BR-…
Non-functional:          NFR-…
Open Items:
```

## 18. User Story

```
Story ID:     US-xx
Title:
As a <vai trò cụ thể>
I want <khả năng>
So that <giá trị business đo được>

Context / Why:
Business Rules:     BR-…
Acceptance Criteria: AC-… (template 19)
Out of scope:
UI / Mockup:
API / Data impact:
Dependencies:
Open questions:
Estimate:
```

**INVEST check:** Independent · Negotiable · Valuable · Estimable · Small · Testable.

## 19. Acceptance Criteria

```gherkin
AC-01: <tên kịch bản>
Given <trạng thái/điều kiện ban đầu cụ thể, có dữ liệu>
  And <điều kiện thêm>
When <một hành động hoặc trigger>
Then <kết quả quan sát được>
  And <dữ liệu/log/event thay đổi thế nào>
```

**Ví dụ (Promotion Code, chuyển từ tiêu chí nghiệm thu BRD):**

```gherkin
AC-03: Gọi phát mã trùng ref ID
Given khách hàng đã gọi POST /promo/issuances với ref_id "RH-001" và nhận serial S1
When khách hàng gọi lại POST /promo/issuances với cùng ref_id "RH-001"
Then hệ thống trả về serial S1
  And không tạo lượt phát mới
  And không tính phí lần hai
```

Mỗi story nên có: 1 happy, ≥ 1 alternative, ≥ 1 negative/exception, boundary nếu có số.

## 20. Functional Specification

```
0. Thông tin tài liệu: version, trạng thái, tác giả, reviewer, ticket, ngày
1. Background / Business Context
2. Problem Statement & Objective
3. Stakeholders
4. Scope: In / Out / Giữ nguyên
5. Assumptions / Dependencies / Constraints
6. AS-IS Process
7. TO-BE Process (sơ đồ)
8. User Stories / Use Cases
9. Business Rules (catalogue)
10. Acceptance Criteria
11. Data Impact (dictionary, migration)
12. API Impact (endpoint, contract, error)
13. UI Impact (màn, field, state, mockup)
14. Error & Exception Handling
15. NFR
16. Permission / Audit / Security
17. Report / Đối soát
18. UAT / Release / Monitoring
19. Open Items & Decision Log (ID, câu hỏi, cần ai, trạng thái, ngày đóng, kết luận, rule liên quan)
20. Glossary
21. Change History
```

## 21. API Requirement

```
Endpoint:          METHOD /path
Mục đích (business):
Caller:            Ai gọi
Auth:              Cách xác thực / phân quyền / chữ ký
Idempotency:       Khoá chống trùng (header/field), thời gian giữ
Rate limit:
Request:
  Path params:     tên – kiểu – bắt buộc – mô tả
  Query params:
  Headers:
  Body:            (bảng field + JSON mẫu)
Validation rules:
Response thành công: status + JSON mẫu
Response lỗi:      → Error Code Matrix (template 23)
Side effects:      Dữ liệu nào đổi, event nào phát
Timeout & retry:   Phía gọi nên retry thế nào
Backward compatibility:
Open items:
```

## 22. Data Dictionary

| Entity | Field | Kiểu | Độ dài | Bắt buộc | Unique | Mặc định | Validation | Nguồn | Ví dụ | Mô tả nghiệp vụ | PII |
|---|---|---|---|---|---|---|---|---|---|---|---|
| order | client_ref_id | string | 64 | Y | Y (theo account) | – | `[A-Za-z0-9-_]` | Client gửi | RH-2026-0001 | Khoá chống tạo trùng | N |
| order | phone | string | 15 | Y | N | – | 10–11 số | Client | 09xxxxxxxx | SĐT người nhận | Y |

## 23. Error Code Matrix

| Error code | HTTP | Khi nào xảy ra | Message cho caller | Message cho end-user | Caller nên làm gì | Retry? | Log/Alert |
|---|---|---|---|---|---|---|---|
| ORDER_DUPLICATE_REF | 409 | client_ref_id đã tồn tại với payload khác | "client_ref_id already used" | – | Kiểm tra lại ref | Không | Log |
| SKU_UNAVAILABLE | 422 | SKU INACTIVE hoặc hết hàng | "SKU not available" | "Quà đã hết, vui lòng chọn quà khác" | Refresh catalog | Không | Metric |
| SUPPLIER_TIMEOUT | 504 | Supplier không phản hồi trong [10]s | "Upstream timeout" | – | Retry với cùng idempotency key | Có, backoff | Alert nếu > 5%/5' |

## 24. Permission Matrix

| Chức năng / Hành động | Admin | Ops | Ops Lead | Kế toán | CS | Sales/AM | Ghi chú |
|---|---|---|---|---|---|---|---|
| Xem Order | ✔ | ✔ | ✔ | ✔ | ✔ | Chỉ client mình | |
| Sửa địa chỉ Order | ✔ | ✔ | ✔ | – | – | – | Ghi audit |
| Huỷ Sub-order đã gửi Supplier | – | – | ✔ | – | – | – | Cần lý do |
| Xem số tiền đối soát | ✔ | – | ✔ | ✔ | – | – | |

Thêm cột **Data scope** (xem tất cả / theo client / theo supplier) và **Che dữ liệu** (VD: che một phần mã, SĐT).

## 25. Impact Analysis

```
Change ID / Tên thay đổi:
Người yêu cầu / Ngày:
Mô tả thay đổi:
Lý do (problem/value):
```

| Khu vực | Có ảnh hưởng? | Chi tiết | Effort | Rủi ro | Owner |
|---|---|---|---|---|---|
| UI | | | | | |
| API (contract, client tích hợp) | | | | | |
| Database / migration dữ liệu cũ | | | | | |
| Business Rule hiện hành | | | | | |
| Report / Đối soát | | | | | |
| Quy trình vận hành / CS | | | | | |
| Permission / Audit | | | | | |
| Test (case mới, regression) | | | | | |
| Tài liệu / Hợp đồng / Thể lệ | | | | | |
| Timeline / Scope khác | | | | | |

**Khuyến nghị:** Làm ngay / Làm phase sau / Không làm — kèm lý do và người quyết định.

## 26. Requirement Traceability Matrix

| BR | FR / Story | Business Rule | AC | Test Case | UAT Scenario | Dev ticket | Trạng thái |
|---|---|---|---|---|---|---|---|
| BR-01 | US-03 | BR-ORD-002 | AC-03.1–3.4 | TC-031–036 | UAT-07 | #12345 | Passed |

Dùng RTM để trả lời hai câu: *Requirement này đã được test chưa?* và *Test case này chứng minh requirement nào?*

## 27. UAT Scenario

| UAT ID | Trace (BR/US) | Kịch bản business | Actor | Pre-condition & dữ liệu | Các bước | Kết quả mong đợi | Kết quả thực tế | Pass/Fail | Người ký |
|---|---|---|---|---|---|---|---|---|---|
| UAT-07 | US-03 | Ops sửa địa chỉ Order trước khi gửi Supplier | Ops | Order CREATED, chưa gửi Supplier | 1. Mở Order 2. Sửa địa chỉ 3. Lưu | Địa chỉ mới hiển thị, audit log có before/after | | | |

**UAT kèm:** Entry criteria · Exit criteria · Danh sách dữ liệu test · Lịch · Người tham gia · Quy tắc phân loại lỗi · Mẫu sign-off.

## 28. Go-live Checklist

| # | Hạng mục | Chi tiết | Owner | Hạn | Done |
|---|---|---|---|---|---|
| 1 | Scope release chốt | Danh sách ticket, version | PO | | [ ] |
| 2 | UAT sign-off | Biên bản | Business | | [ ] |
| 3 | Config production | Tham số [ ], feature flag | Dev | | [ ] |
| 4 | Migration dữ liệu cũ | Script + dry-run | Dev | | [ ] |
| 5 | Credential / whitelist / webhook URL | Cho client, supplier | Dev, AM | | [ ] |
| 6 | Rollback plan | Điều kiện kích hoạt, các bước, người quyết | Tech Lead | | [ ] |
| 7 | Monitoring & alert | Metric, ngưỡng, kênh báo | Dev, Ops | | [ ] |
| 8 | Communication | Thông báo client, CS script, hướng dẫn Ops | PO, CS | | [ ] |
| 9 | Hypercare | Lịch trực 3–7 ngày đầu | PO | | [ ] |
| 10 | Đo baseline KPI | Số liệu trước go-live | PO, DA | | [ ] |

## 29. Product KPI

| KPI | Loại (Outcome / Output / Guardrail) | Công thức | Nguồn dữ liệu | Baseline | Target | Tần suất đo | Owner |
|---|---|---|---|---|---|---|---|
| Tỷ lệ order fail do SKU unavailable | Outcome | order fail lý do SKU_UNAVAILABLE / tổng order | Bảng order + error log | TBD | < 1% | Tuần | PO |
| Thời gian lan truyền thay đổi availability | Output | p95 (client nhận event − SKU đổi) | Log webhook | – | ≤ 2 phút | Ngày | Tech Lead |
| Khiếu nại CS về quà hết hàng | Guardrail | Số ticket tag "out-of-stock" | CS tool | TBD | Giảm 50% | Tháng | CS Lead |

**Câu hỏi bắt buộc cho mỗi KPI:** dữ liệu này hiện có trong hệ thống không? (bài học Promotion Code: KPI redeem không đo được vì chỉ biết mã rời kho.)

## 30. Post-release Review

```
Release / Feature:
Ngày go-live:              Kỳ đánh giá:
Mục tiêu ban đầu (link Problem Statement):
Kết quả KPI:               (bảng baseline → target → thực tế)
Điều chạy tốt:
Điều chưa tốt:
Incident / bug sau release: (số lượng, mức độ, root cause)
Requirement bị hiểu sai / thiếu:
Quyết định tiếp theo:      Giữ / Cải tiến / Rollback / Mở rộng
Action items:              (việc – owner – hạn)
Bài học cho quy trình BA/PO:
```
