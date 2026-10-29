# Lộ trình BA/PO thực chiến — 56 ngày

> Từ Business Request đến Requirement, Delivery và Product Value.
> 8 tuần · 56 ngày · 60–90 phút/ngày · 30% lý thuyết, 70% thực hành.

## Học trên điện thoại

Mở **https://ntphuongdung1110-cmyk.github.io/BA-PO/** trên điện thoại:
- iPhone (Safari): nút Chia sẻ → **Thêm vào MH chính**.
- Android (Chrome): menu ⋮ → **Thêm vào màn hình chính** / **Cài đặt ứng dụng**.

App có: nút "Học tiếp", từng ngày học, lời giải ẩn, đánh dấu hoàn thành (lưu trên máy), đổi cỡ chữ, sáng/tối, học offline sau lần mở đầu.

## Mục tiêu đầu ra

Sau 56 ngày, bạn tự xử lý được một feature hoặc project từ đầu đến cuối:

**Tiếp nhận Request → Discovery → AS-IS → Root Cause → TO-BE → Scope → Requirement (BR/FR/NFR, Use Case, User Story, AC) → Data/API/UI → Refinement → Dev/QC support → UAT → Go-live → Đo KPI.**

Không chỉ biết viết User Story. Biết hỏi đúng, chọn đúng, đo được giá trị.

## Tài liệu này được tổng hợp từ đâu

| Nguồn | Lấy gì |
|---|---|
| Yêu cầu chương trình học (10 phase, format mỗi ngày, 30 template, Capstone) | Khung nội dung, danh sách năng lực, format bài học |
| Lộ trình 56 ngày bản Word (`_sources/lo-trinh-goc-docx.md`) | Nhịp học Learn → Analyze → Practice → Review, deliverable mỗi ngày, rubric 0–4, bài Admin sửa Order / Auto-cancel / Product hết stock, kế hoạch 30 ngày sau khoá |
| Dự án thật **Promotion Code Warehouse** | Ví dụ thật về data model, business rule có tham số, API 2 bước, idempotency, permission, đối soát, MVP, KPI |
| Dự án thật **Slide to Use + redeem code 3rd** | Ví dụ thật về problem statement, AS-IS/TO-BE, scope theo kênh, state, concurrency, requirement change, open items, stakeholder conflict |

Điểm khác so với bản Word: thêm Phase 6 API & Integration đầy đủ (7 ngày), Phase 7 UX/UI (4 ngày), Phase 10 Senior skills (2 ngày), bài tổng hợp Admin sửa Order (Day 27), Capstone đổi sang **đồng bộ Product Availability**, mỗi ngày có bảng **Junior vs Middle vs Senior** và ví dụ từ hai dự án thật.

## Cấu trúc repo

```
index.html                        ← web app học trên điện thoại (GitHub Pages)
README.md                         ← bạn đang ở đây (tổng quan 56 ngày)
00-case-study/
  01-physical-gift.md             ← case giả lập xuyên suốt (entity, trạng thái, actor)
  02-promotion-code.md      ← case thật 1
  03-slide-to-use.md        ← case thật 2
days/
  week-01.md … week-07.md         ← Day 1–49, mỗi ngày đủ 10 mục
capstone/
  capstone.md                     ← Day 50–56, có lời giải mẫu ẩn trong <details>
templates/
  templates.md                    ← 30 template thực hành
tracker/
  progress-tracker.md             ← bảng theo dõi 56 ngày + rubric tự chấm
_sources/
  lo-trinh-goc-docx.md            ← bản Word gốc (đã chuyển markdown)
```

## Cách học mỗi ngày

| Bước | Thời lượng | Làm gì |
|---|---|---|
| 1. Learn | 15–20 phút | Đọc *Mục tiêu*, *Kiến thức cần học*, *Khi nào dùng* |
| 2. Analyze | 15 phút | Đọc *Ví dụ thực tế*, bảng *Junior vs Middle vs Senior*, *Sai lầm thường gặp* |
| 3. Practice | 30–40 phút | Làm *Bài tập thực hành* **trước khi** mở lời giải. Ghi ra file của bạn |
| 4. Review | 10–15 phút | So với *Lời giải tham khảo*, tick *Checklist*, ghi gap vào tracker |

Nhịp tuần: 6 ngày học + 1 ngày có phần **Review tuần**. Chỉ học được ngày làm việc thì kéo mỗi tuần thành 7–9 ngày, nhưng giữ thứ tự.

**Nguyên tắc:**
1. Không bắt đầu bằng solution. Bắt đầu bằng problem và business value.
2. Mỗi requirement phải đủ rõ để Dev hiểu một nghĩa và QC test được.
3. Luôn nghĩ Happy path, Alternative, Exception, Boundary, Recovery.
4. Không biết thì ghi Open Item, không đoán.
5. Mỗi tuần ra ít nhất một artifact dùng được như tài liệu dự án thật.

## Ba mức tư duy

| Tình huống | Junior | Middle | Senior BA/PO |
|---|---|---|---|
| "Business muốn Export Excel" | Ghi lại: cần nút Export | Hỏi export field nào, filter nào | Hỏi tại sao cần export, ai dùng file, để đối soát hay báo cáo, có cách khác Excel không (report có sẵn, API, dashboard) |
| "Cho Admin sửa Order" | Thêm nút Sửa | Hỏi sửa field nào, ở status nào | Hỏi vì sao Order sai từ đầu, sửa xong ảnh hưởng Supplier, Delivery, đối soát thế nào, ai duyệt, log gì |
| "Mã đối tác hết nhanh" (Slide to Use) | Đề xuất nhập kho nhiều hơn | Đề xuất cảnh báo tồn kho | Nhận ra mã bị lấy *trước khi* khách cần → tách "giữ quyền" và "lấy mã" thành hai thời điểm |
| "KPI là tỷ lệ redeem" (Promotion Code) | Ghi KPI vào BRD | Hỏi công thức tính | Hỏi dữ liệu redeem lấy ở đâu; phát hiện hệ thống chỉ biết mã rời kho → KPI hiện không đo được |

## A. Tổng quan chương trình 56 ngày

### Tuần 1 — Foundation & Discovery ([days/week-01.md](days/week-01.md))

| Day | Topic | Skill | Exercise | Deliverable |
|---|---|---|---|---|
| 1 | BA, PO và các vai trò BA vs PO vs PM vs SA vs DEV vs QA | Định vị vai trò, RACI | RACI cho Re-delivery tự động | RACI 1 trang |
| 2 | SDLC & Product Lifecycle | Map hoạt động BA/PO theo giai đoạn | Map vòng đời cho lỗi Order trùng do timeout | Lifecycle map: 12 hoạt động BA/PO gắn vào giai đoạn |
| 3 | Agile & Scrum cho BA/PO | Role, event, artifact | Phân vai PO/BA trong sprint thông báo giao thất bại | Bảng "BA/PO làm gì trong từng event" + xử lý 4 tình huống sprint |
| 4 | Business Thinking & Product Thinking | Phân biệt Request / Problem / Need / Requirement / Solution | Phân rã 5 request thành Problem / Need / Requirement / Solution | Bảng phân rã 5 request thành Problem / Need / Requirement / Solution |
| 5 | Business Request → Problem Statement | Problem framing, evidence, impact | Viết Problem Statement cho 3 request có dữ liệu thô | 3 Problem Statement đạt chuẩn |
| 6 | Elicitation: Interview, Workshop, Observation, Document Analysis | Chọn kỹ thuật đúng tình huống | Elicitation Plan cho đối soát Supplier lệch số | Elicitation Plan cho bài toán đối soát Supplier lệch số |
| 7 | Discovery Questions (5W1H + WHAT IF) · Review tuần 1 | Đặt câu hỏi đúng trọng tâm | 25 câu hỏi cho "Recipient tự đổi quà" | Bộ 25 câu hỏi discovery + Discovery Pack v1 |

### Tuần 2 — Stakeholder & Process ([days/week-02.md](days/week-02.md))

| Day | Topic | Skill | Exercise | Deliverable |
|---|---|---|---|---|
| 8 | Stakeholder Mapping & RACI | Power/Interest, decision right | Stakeholder map cho Re-delivery trên hệ thống | Stakeholder Register + Power/Interest Grid + RACI |
| 9 | Communication Strategy & Workshop | Agenda, facilitation, MoM | Kế hoạch chốt 3 câu hỏi mở Re-delivery | Communication Plan + Workshop Agenda + MoM + Follow-up |
| 10 | AS-IS & Pain Point | Mô tả quy trình hiện tại | AS-IS Sub-order quá SLA từ lời kể Ops | AS-IS Flow + Pain Point Register |
| 11 | Root Cause: 5 Whys, Fishbone | Tách symptom và root cause | RCA đối soát lệch do huỷ muộn | RCA Sheet (5 Whys + Fishbone + kết luận) |
| 12 | Gap Analysis & TO-BE | Thiết kế quy trình mục tiêu | TO-BE Re-delivery có giới hạn số lần | Gap Table + TO-BE Flow + Rationale |
| 13 | Flowchart & Swimlane | Handoff giữa các bên | Swimlane 5 làn cho Re-delivery | Swimlane 5 lane + Step Table |
| 14 | BPMN cơ bản · Review tuần 2 | Event, task, gateway, message | BPMN Supplier huỷ sau khi confirm | BPMN v1 + Review tuần 2 |

### Tuần 3 — Requirement Engineering ([days/week-03.md](days/week-03.md))

| Day | Topic | Skill | Exercise | Deliverable |
|---|---|---|---|---|
| 15 | Scope, Assumption, Constraint, Dependency | Chốt biên phạm vi | Scope cho Re-delivery tự động | Scope Statement cho feature Auto-cancel Sub-order |
| 16 | BR / UR / FR / NFR | Phân tầng requirement | Phân tầng requirement chống tạo Order trùng | Requirement Hierarchy (BR → UR → FR/NFR) |
| 17 | Business Rule Catalogue | Rule atomic, testable, có tham số | Rule Catalogue từ biên bản workshop Re-delivery | Business Rule Catalogue 10–12 rule có ID, tham số, nguồn, owner |
| 18 | Use Case | Main / Alternative / Exception flow | Use Case Create Order qua API | Use Case Specification UC-SUB-01 |
| 19 | User Story & Story Splitting | INVEST, tách story | Tách Epic Admin sửa Order thành story | Backlog v1: 6–8 User Story đã tách |
| 20 | Acceptance Criteria & Given/When/Then | Boundary, negative case | G/W/T cho 2 tiêu chí nghiệm thu Promotion Code | AC Pack cho 3 story + bộ G/W/T Promotion Code |
| 21 | DoR, DoD, RTM · Review tuần 3 | Trace requirement → test | RTM + DoR cho Re-delivery tự động | DoR/DoD checklist + RTM 10 dòng |

### Tuần 4 — System Analysis ([days/week-04.md](days/week-04.md))

| Day | Topic | Skill | Exercise | Deliverable |
|---|---|---|---|---|
| 22 | Entity, Attribute, PK, FK, 1-1 / 1-N / N-N | Data modeling | Mô hình dữ liệu chuyển Supplier khi bị từ chối | Entity list + bảng quan hệ có cardinality cho Physical Gift |
| 23 | ERD & Data Dictionary | Định nghĩa field | ERD + Dictionary cho ghi chú giao hàng | ERD v1 (mermaid) + Data Dictionary cho Create Order |
| 24 | State Transition | State, event, guard | State machine Re-delivery tối đa 2 lần | State diagram + Transition Table cho Sub-order và shipping_status |
| 25 | Permission & Audit Log | Phân quyền, truy vết | Permission + Audit cho điều chỉnh đối soát | Permission Matrix + Audit Log Requirement |
| 26 | SQL cho BA | Điều tra dữ liệu, đối soát | SQL điều tra Order COMPLETED sai + đối soát redeem | Bộ 10 query điều tra + 1 query đối soát redeem |
| 27 | Bài tổng hợp: Admin sửa Order | End-to-end analysis | Admin sửa Order: phân tích đủ 13 phần | Bộ phân tích end-to-end (Problem → Test Scenario) |
| 28 | REST API cơ bản · Review tuần 4 | Method, resource, status code | Thiết kế API huỷ Order cho Client | API Checklist cho `POST /orders` + bài review tuần |

### Tuần 5 — API & Integration ([days/week-05.md](days/week-05.md))

| Day | Topic | Skill | Exercise | Deliverable |
|---|---|---|---|---|
| 29 | Header, Body, Query/Path Param, Pagination | Đọc và viết API contract | Đặc tả API tra cứu Sub-order quá SLA | Bảng mô tả field request/response cho `GET /programs/{id}/products` |
| 30 | Authentication, Authorization, Signature | Bảo mật tích hợp | Rà bảo mật callback của Supplier | Ma trận AuthN/AuthZ cho API Client + checklist chữ ký webhook |
| 31 | Idempotency & Duplicate Request | Chống tạo trùng | Chống trùng khi PG gửi lại Sub-order | Bộ Business Rule chống trùng cho `POST /orders` + G/W/T |
| 32 | Timeout, Retry, Concurrency | Xử lý lỗi mạng và tranh chấp | Race condition ngân sách Program | Bảng timeout/retry PG → Supplier + NFR concurrency |
| 33 | Webhook, Event, Callback & Sequence Diagram | Tích hợp bất đồng bộ | Webhook vận chuyển đến sai thứ tự | Sequence diagram Create Order → Supplier → Delivery |
| 34 | Error Handling & API Requirement | Error code matrix | Error Code Matrix từ log lỗi Supplier | API Requirement v1 cho `POST /orders` kèm Error Code Matrix |
| 35 | User Journey & Wireframe · Review tuần 5 | UX góc nhìn BA | Journey + wireframe Ops theo dõi Sub-order quá SLA | User Journey Operator xử lý giao thất bại + low-fi wireframe |

### Tuần 6 — UX/UI & Product Owner ([days/week-06.md](days/week-06.md))

| Day | Topic | Skill | Exercise | Deliverable |
|---|---|---|---|---|
| 36 | Field Definition & Validation | Đặc tả field | Field spec form Tạo Program | Field Specification Table |
| 37 | Empty, Loading, Error, Permission, Confirmation state | Đủ trạng thái UI | UI State Matrix màn Order Detail | UI State Matrix cho màn Order Detail |
| 38 | Search, Filter, Sort, Pagination, Import, Export | Màn danh sách | Spec import Re-delivery hàng loạt | List Screen Spec + Import Spec |
| 39 | Product Vision, Goal, Discovery, Persona/JTBD | Định hướng sản phẩm | Vision + Persona cho Re-delivery | Product Vision Board + 2 Persona/JTBD |
| 40 | Value Proposition, Opportunity, Solution Options, MVP | Chọn giải pháp | So sánh giải pháp + chọn MVP Re-delivery | Solution Options Matrix + MVP Scope |
| 41 | MoSCoW, RICE, Backlog, Roadmap | Ưu tiên | Chấm RICE 8 feature + roadmap | RICE Matrix 8 feature + Outcome Roadmap |
| 42 | KPI & Product Metric · Review tuần 6 | Metric tree, baseline | Metric tree cho outcome giảm RETURNED | Metric Tree + Metric Definition Sheet |

### Tuần 7 — Delivery & Senior Skills ([days/week-07.md](days/week-07.md))

| Day | Topic | Skill | Exercise | Deliverable |
|---|---|---|---|---|
| 43 | Refinement, Sprint Planning, Estimation | Chuẩn bị ticket ready | Refinement story Re-delivery nháp | Refinement Pack cho 3 story + câu hỏi mở |
| 44 | Dev Support, QC Support, Bug Triage | Phân loại issue | Triage 12 issue khi test Re-delivery | Triage Log 12 issue có phân loại và hành động |
| 45 | Change Request & Impact Analysis | Quản lý thay đổi | Impact Analysis CR đổi hạn thu hồi Promotion Code | Impact Analysis + Decision Log cho 1 Change Request |
| 46 | UAT | Plan, scenario, sign-off | UAT Plan cho Slide to Use | UAT Plan + 8 UAT Scenario + biên bản sign-off |
| 47 | Release, Go-live, Rollback, Monitoring, PIR | Ra mắt an toàn | Release + migration Re-delivery | Release Checklist + Rollback Plan + Monitoring Plan |
| 48 | Conflict, Scope Creep, Trade-off, Decision Making | Ra quyết định | Xử lý conflict Ops vs Finance về chuyển Supplier | Decision Record cho 1 xung đột thật |
| 49 | Risk, Dependency, Negotiation, Executive Communication · Review tuần 7 | Giao tiếp cấp cao | Risk register + Executive Summary Promotion Code | Risk & Dependency Register + Executive Summary 1 trang |

### Tuần 8 — Capstone ([capstone/capstone.md](capstone/capstone.md))

**Đề:** Tự động đồng bộ Product Availability từ Product Management sang Client bên ngoài, để Client không hiển thị Product inactive hoặc out-of-stock.

| Day | Topic | Skill | Exercise | Deliverable |
|---|---|---|---|---|
| 50 | Problem, Stakeholder, Discovery | Problem framing | Problem statement + 20 câu hỏi | Discovery pack |
| 51 | AS-IS, RCA, TO-BE | Process analysis | 3 artifact process | Process pack |
| 52 | Solution Options, MVP, Scope, Business Rule | Product decision | Option matrix + BR catalogue | Decision sheet |
| 53 | Flow, API/Webhook, Error Handling | Integration design | Sequence + API spec + error matrix | Integration spec |
| 54 | Data, User Story, Acceptance Criteria | Requirement | Dictionary + stories + AC | FS v1 |
| 55 | Impact Analysis, UAT, Release | Delivery | Impact + UAT + release plan | Delivery pack |
| 56 | KPI, Final Review, kế hoạch 30 ngày | Measure & reflect | Metric tree + tự chấm rubric | Capstone final |

## Template

30 template ở [templates/templates.md](templates/templates.md): Problem Statement → Business Context → Stakeholder → Discovery → AS-IS → Pain Point → RCA → TO-BE → Scope → Assumption → Constraint → Dependency → BR → FR → NFR → BR Catalogue → Use Case → User Story → AC → FS → API Requirement → Data Dictionary → Error Code Matrix → Permission Matrix → Impact Analysis → RTM → UAT Scenario → Go-live Checklist → Product KPI → Post-release Review.

## Theo dõi tiến độ

[tracker/progress-tracker.md](tracker/progress-tracker.md) — tick từng ngày, tự chấm 0–4, ghi gap.

## Dấu hiệu bạn đã tiến bộ

Bạn không còn hỏi "Business muốn build gì?" trước tiên. Bạn bắt đầu bằng: *Problem là gì, evidence đâu, impact bao nhiêu, ai bị ảnh hưởng, rule và exception nào, và làm sao đo value sau khi release?*

---

*Ghi chú về case thật: hai case lấy từ tài liệu dự án thật, đã ẩn danh tên công ty, sản phẩm và team. Chỉ trích các điểm có trong tài liệu; phần mở rộng để làm bài tập được đánh dấu `[Giả định bài tập]`.*
