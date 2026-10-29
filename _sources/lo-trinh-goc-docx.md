**BA/PO PRACTICAL LEARNING ROADMAP**

Lộ trình học BA/PO\
trong 56 ngày

Từ Business Problem đến Requirement, Delivery và Product Value

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Mục tiêu cuối khóa</strong></p>
<p>Tự tiếp nhận một business request, tổ chức discovery, phân tích
AS-IS/TO-BE, viết requirement có thể build/test, phối hợp Business - Dev
- QC, quản lý backlog, hỗ trợ UAT/release và đo hiệu quả sau
go-live.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

| **Thời lượng**      | 8 tuần - 56 ngày                            |
|---------------------|---------------------------------------------|
| **Thời gian/ngày**  | 60-90 phút                                  |
| **Phương pháp**     | 30% lý thuyết - 70% thực hành               |
| **Case xuyên suốt** | Product - SKU - Supplier - Order - Delivery |

*Tài liệu được thiết kế như một giáo án thực chiến: mỗi ngày có mục
tiêu, nội dung, bài tập, đầu ra và tiêu chí hoàn thành. Không cần học
thuộc; mục tiêu là tạo ra artifact giống dự án thật.*

# 1. Cách sử dụng giáo án

Mỗi ngày học theo vòng lặp 4 bước: Learn -\> Analyze -\> Practice -\>
Review. Nếu bận, ưu tiên hoàn thành bài thực hành và đầu ra bắt buộc
thay vì đọc thêm lý thuyết.

| **Bước** | **Thời lượng** | **Cách học** |
|----|----|----|
| 1\. Learn | 15-20 phút | Học khái niệm và framework cốt lõi. |
| 2\. Analyze | 15 phút | Đọc ví dụ, xác định logic, rule và câu hỏi còn thiếu. |
| 3\. Practice | 30-40 phút | Tạo artifact: flow, user story, BR, AC, API spec, backlog... |
| 4\. Review | 10-15 phút | Đối chiếu checklist/đáp án, tự ghi gap và lesson learned. |

## Nguyên tắc học

- Không bắt đầu bằng solution. Luôn bắt đầu bằng problem và business
  value.

- Mỗi requirement phải đủ rõ để Dev hiểu một nghĩa và QC có thể test
  được.

- Luôn phân tích Happy Path, Alternative Path, Exception, Boundary và
  Recovery.

- Mỗi tuần phải tạo ít nhất một deliverable có thể dùng như tài liệu dự
  án thật.

- Không chỉ hỏi "Business muốn gì?"; phải tìm "Tại sao cần?" và "Đo
  thành công bằng gì?".

# 2. Bản đồ năng lực BA/PO

| **Nhóm năng lực** | **BA cần đạt** | **PO cần đạt** | **Deliverable tiêu biểu** |
|----|----|----|----|
| Business Analysis | Elicitation, AS-IS/TO-BE, root cause, scope, business rules | Problem framing, value, opportunity | Problem Statement, Scope, BPMN |
| Requirement Engineering | Use Case, User Story, AC, NFR, RTM | Backlog quality, acceptance, prioritization | BRD/FS, User Story, AC |
| System Analysis | Data, API, integration, sequence, error handling | Trade-off và impact awareness | ERD, API requirement, Sequence |
| Product | Hiểu user/problem và metric | Vision, MVP, roadmap, KPI, prioritization | Product Goal, MVP, Roadmap |
| Delivery | Refinement, UAT, release support | Backlog, sprint goal, accept/reject | DoR, UAT, Release checklist |
| Stakeholder | Interview, workshop, conflict handling | Alignment, decision, expectation | Stakeholder map, decision log |

# 3. Vòng đời một feature

### 01. Business Request

Ghi nhận nhu cầu nhưng chưa vội chốt solution.

### 02. Problem Discovery

Xác định problem, evidence, impact và mục tiêu.

### 03. Stakeholder Analysis

Xác định ai quyết định, ai sử dụng, ai bị ảnh hưởng.

### 04. AS-IS

Mô tả quy trình và dữ liệu hiện tại.

### 05. Root Cause

Phân biệt symptom và nguyên nhân gốc.

### 06. TO-BE

Thiết kế process/solution mục tiêu.

### 07. Scope

Chốt in-scope, out-of-scope, dependency, assumption.

### 08. Requirement

Viết flow, rule, AC, NFR, data/API/UI impact.

### 09. Refinement

Đồng bộ Business - BA/PO - Dev - QC.

### 10. Development

Hỗ trợ clarification và quản lý change.

### 11. Testing/UAT

Xác nhận sản phẩm đúng requirement và đúng business need.

### 12. Release

Go-live có checklist, rollback, monitoring, communication.

### 13. Measure & Improve

Đo KPI, adoption, failure rate và cải tiến.

# 4. Lộ trình học 56 ngày

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Nhịp học khuyến nghị</strong></p>
<p>Học 6 ngày + 1 ngày review mỗi tuần. Nếu bạn chỉ học được ngày làm
việc, có thể kéo mỗi tuần thành 7-9 ngày nhưng giữ nguyên thứ tự để kiến
thức nối tiếp nhau.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Tuần 1 - Foundation & BA/PO Mindset

| **Ngày** | **Chủ đề** | **Mục tiêu** | **Bài thực hành** | **Đầu ra** |
|----|----|----|----|----|
| Ngày 1 | BA vs PO vs PM vs SA | Hiểu trách nhiệm, ranh giới và điểm giao nhau. | Vẽ RACI cho một feature Create Order. | RACI 1 trang. |
| Ngày 2 | SDLC & Product Lifecycle | Hiểu BA/PO tham gia từ discovery đến post-release. | Map 10 hoạt động BA/PO vào các giai đoạn SDLC. | Lifecycle map. |
| Ngày 3 | Business Problem Thinking | Phân biệt request, requirement, problem và solution. | Chuyển 5 yêu cầu kiểu "Tôi muốn..." thành Problem Statement. | 5 Problem Statements. |
| Ngày 4 | Stakeholder Analysis | Xác định stakeholder, influence, interest, decision right. | Lập stakeholder map cho hệ thống Order. | Stakeholder map + RACI. |
| Ngày 5 | Requirement Elicitation | Dùng WHY/WHO/WHAT/WHEN/HOW/WHAT IF. | Soạn 20 câu hỏi cho yêu cầu "Admin sửa Order". | Question list. |
| Ngày 6 | Interview & Workshop | Biết mở, dẫn dắt, chốt và follow-up buổi discovery. | Viết agenda 45 phút và minutes mẫu. | Workshop agenda + MoM. |
| Ngày 7 | Weekly Review 1 | Tổng hợp kiến thức và sửa lỗi tư duy solution-first. | Mini case: yêu cầu Refresh Product. Phân tích problem, stakeholder, 15 câu hỏi. | Discovery pack v1. |

*Tự đánh giá tuần: \[ \] Tôi hiểu khái niệm \[ \] Tôi tạo được artifact
\[ \] Tôi giải thích được cho người khác \[ \] Tôi áp dụng được vào case
thật*

## Tuần 2 - Process Analysis & Business Rules

| **Ngày** | **Chủ đề** | **Mục tiêu** | **Bài thực hành** | **Đầu ra** |
|----|----|----|----|----|
| Ngày 8 | AS-IS Process | Mô tả quy trình hiện tại đủ actor, step, data, pain point. | Vẽ AS-IS Order -\> Supplier -\> Delivery. | AS-IS flow. |
| Ngày 9 | Swimlane Diagram | Thể hiện trách nhiệm và handoff giữa các bên. | Chuyển AS-IS sang swimlane 5 lane. | Swimlane diagram. |
| Ngày 10 | BPMN Basics | Hiểu event, task, gateway, pool/lane, message. | Model luồng cancel sub-order. | BPMN v1. |
| Ngày 11 | Root Cause Analysis | Dùng 5 Whys và Fishbone để tìm nguyên nhân gốc. | Phân tích order fail do stale product data. | RCA sheet. |
| Ngày 12 | TO-BE Design | Thiết kế future process dựa trên pain point và constraint. | Đề xuất TO-BE cho sync product availability. | TO-BE + rationale. |
| Ngày 13 | Business Rules | Viết rule atomic, testable, có condition/action. | Viết 15 rule cho cancel/edit order. | Business Rule Catalogue. |
| Ngày 14 | State Transition | Phân tích state, allowed transition, invalid transition. | Thiết kế state machine cho Sub-order. | State Transition Table. |

*Tự đánh giá tuần: \[ \] Tôi hiểu khái niệm \[ \] Tôi tạo được artifact
\[ \] Tôi giải thích được cho người khác \[ \] Tôi áp dụng được vào case
thật*

## Tuần 3 - Requirement Engineering

| **Ngày** | **Chủ đề** | **Mục tiêu** | **Bài thực hành** | **Đầu ra** |
|----|----|----|----|----|
| Ngày 15 | Scope & Assumption | Chốt in/out scope, dependency, assumption, constraint. | Viết scope cho Auto-cancel sau 30 phút. | Scope statement. |
| Ngày 16 | Business Requirement vs FR/NFR | Phân loại requirement đúng tầng. | Phân loại 20 requirement mẫu. | Requirement taxonomy. |
| Ngày 17 | User Story | Viết story tập trung user value, không nhét implementation. | Viết 8 stories cho Order Management. | Backlog v1. |
| Ngày 18 | Acceptance Criteria | Dùng Given/When/Then và boundary cases. | Mỗi story viết 3-5 AC. | AC pack. |
| Ngày 19 | Use Case | Viết actor, pre-condition, main/alternative/exception flow. | Use Case Create Order. | UC-Create-Order. |
| Ngày 20 | NFR | Phân tích performance, security, audit, availability, usability. | Viết 12 NFR cho Order API. | NFR list. |
| Ngày 21 | RTM & DoR | Trace requirement -\> build -\> test và kiểm tra ticket ready. | Tạo RTM 10 requirement + DoR checklist. | RTM + DoR. |

*Tự đánh giá tuần: \[ \] Tôi hiểu khái niệm \[ \] Tôi tạo được artifact
\[ \] Tôi giải thích được cho người khác \[ \] Tôi áp dụng được vào case
thật*

## Tuần 4 - System Analysis for BA

| **Ngày** | **Chủ đề** | **Mục tiêu** | **Bài thực hành** | **Đầu ra** |
|----|----|----|----|----|
| Ngày 22 | Data Modeling | Hiểu entity, attribute, PK/FK, cardinality. | Vẽ ERD Product-SKU-Supplier-Program-Order. | ERD v1. |
| Ngày 23 | Data Dictionary | Định nghĩa field rõ type, required, validation, source. | Tạo data dictionary cho Create Order. | Data dictionary. |
| Ngày 24 | SQL for BA | SELECT, JOIN, WHERE, GROUP BY, COUNT, CASE. | Viết 8 query điều tra order fail. | SQL practice. |
| Ngày 25 | REST API Basics | Hiểu method, path/query/header/body, status code. | Phân tích endpoint POST /orders. | API checklist. |
| Ngày 26 | API Requirement | Viết request/response, validation, error, idempotency. | Soạn API requirement Create Order. | API spec v1. |
| Ngày 27 | Sequence Diagram | Mô tả interaction Client-API-Service-Supplier-Delivery. | Vẽ sequence Create Order + Shipping. | Sequence diagram. |
| Ngày 28 | Exception & Integration | Timeout, retry, duplicate, partial failure, recovery. | Lập Exception Matrix 15 case. | Exception Matrix. |

*Tự đánh giá tuần: \[ \] Tôi hiểu khái niệm \[ \] Tôi tạo được artifact
\[ \] Tôi giải thích được cho người khác \[ \] Tôi áp dụng được vào case
thật*

## Tuần 5 - UX & Product Discovery

| **Ngày** | **Chủ đề** | **Mục tiêu** | **Bài thực hành** | **Đầu ra** |
|----|----|----|----|----|
| Ngày 29 | User Journey | Hiểu user goal, step, pain point, opportunity. | Vẽ journey Operator xử lý Order. | User Journey. |
| Ngày 30 | Wireframe for BA | Thiết kế UI đủ state, validation, permission, empty/error. | Wireframe Order List + Detail. | Low-fi wireframe. |
| Ngày 31 | Product Discovery | Problem -\> evidence -\> user -\> impact -\> opportunity. | Viết discovery brief cho lỗi stale product. | Discovery brief. |
| Ngày 32 | Persona / JTBD | Dùng persona vừa đủ và Job-to-be-Done. | Tạo 2 persona: Operator và Client Integrator. | Persona/JTBD. |
| Ngày 33 | Value Proposition | Xác định pain/gain và product value. | Đánh giá 3 solution sync product. | Value comparison. |
| Ngày 34 | Product Metrics | Chọn outcome metric thay vì chỉ output. | Định nghĩa KPI cho Order reliability. | Metric tree. |
| Ngày 35 | Weekly Review 5 | Kết nối BA artifact với product value. | Review một feature từ problem -\> metric -\> flow -\> AC. | Feature one-pager. |

*Tự đánh giá tuần: \[ \] Tôi hiểu khái niệm \[ \] Tôi tạo được artifact
\[ \] Tôi giải thích được cho người khác \[ \] Tôi áp dụng được vào case
thật*

## Tuần 6 - Product Owner & Agile Delivery

| **Ngày** | **Chủ đề** | **Mục tiêu** | **Bài thực hành** | **Đầu ra** |
|----|----|----|----|----|
| Ngày 36 | Backlog Management | Tạo, refine, split, order backlog. | Tách Epic Order Management thành stories. | Backlog v2. |
| Ngày 37 | Prioritization - MoSCoW/RICE | Ưu tiên theo value, reach, impact, confidence, effort. | Chấm điểm 8 features. | Prioritization matrix. |
| Ngày 38 | MVP | Phân biệt MVP với "phiên bản ít tính năng". | Thiết kế MVP cho Order Management. | MVP scope. |
| Ngày 39 | Roadmap | Xây roadmap theo outcome/theme, tránh cam kết giả. | Lập roadmap 3 tháng. | Outcome roadmap. |
| Ngày 40 | Estimation & Capacity | Hiểu story point/t-shirt size, dependency, capacity. | Lập kế hoạch sprint với capacity giả lập. | Sprint plan. |
| Ngày 41 | Refinement | Facilitate refinement: why, flow, rule, AC, dependency. | Chuẩn bị và tự review 3 tickets. | Refinement pack. |
| Ngày 42 | Sprint & Acceptance | Vai trò PO/BA trong planning, daily, review, accept/reject. | Tạo acceptance checklist cho 1 sprint. | Sprint acceptance sheet. |

*Tự đánh giá tuần: \[ \] Tôi hiểu khái niệm \[ \] Tôi tạo được artifact
\[ \] Tôi giải thích được cho người khác \[ \] Tôi áp dụng được vào case
thật*

## Tuần 7 - Testing, Release & Change

| **Ngày** | **Chủ đề** | **Mục tiêu** | **Bài thực hành** | **Đầu ra** |
|----|----|----|----|----|
| Ngày 43 | Test Thinking for BA | Suy nghĩ theo happy, alternative, exception, boundary. | Viết 25 scenario cho Create Order. | Scenario catalogue. |
| Ngày 44 | UAT Planning | Scope, data, scenario, entry/exit, sign-off. | Lập UAT Plan cho Order feature. | UAT plan. |
| Ngày 45 | Defect Triage | Phân biệt bug, change, misunderstanding, data/config issue. | Phân loại 12 issue giả lập. | Triage log. |
| Ngày 46 | Change Request | Impact analysis trên UI/API/DB/report/process/test. | Phân tích request "thêm 1 field". | Impact analysis. |
| Ngày 47 | Release Planning | Checklist config, migration, credential, rollback, communication. | Tạo release checklist. | Release checklist. |
| Ngày 48 | Monitoring & Incident | Định nghĩa log, alert, metric, operational response. | Thiết kế monitoring cho Order API. | Monitoring plan. |
| Ngày 49 | Post-release Review | Đo outcome, lesson learned, continuous improvement. | Viết PIR cho release giả lập. | Post-Implementation Review. |

*Tự đánh giá tuần: \[ \] Tôi hiểu khái niệm \[ \] Tôi tạo được artifact
\[ \] Tôi giải thích được cho người khác \[ \] Tôi áp dụng được vào case
thật*

## Tuần 8 - Capstone: Feature End-to-End

| **Ngày** | **Chủ đề** | **Mục tiêu** | **Bài thực hành** | **Đầu ra** |
|----|----|----|----|----|
| Ngày 50 | Capstone - Discovery | Nhận đề: Auto-cancel Sub-order nếu Supplier không xử lý 30 phút. | Viết problem, objective, stakeholder, 20 câu hỏi. | Discovery pack. |
| Ngày 51 | Capstone - Process | Model AS-IS, RCA, TO-BE và state transition. | Hoàn thiện 4 artifact process. | Process pack. |
| Ngày 52 | Capstone - Requirement | Viết scope, rules, user stories, use case, AC, NFR. | Requirement pack. | FS v1. |
| Ngày 53 | Capstone - System | Phân tích data, API, sequence, timeout/retry, audit. | System analysis pack. | Technical BA pack. |
| Ngày 54 | Capstone - Product | Chọn MVP, priority, KPI và rollout. | Tạo product decision sheet. | MVP + KPI. |
| Ngày 55 | Capstone - Delivery | Chuẩn bị refinement, UAT, release, monitoring. | Tạo delivery pack. | Delivery pack. |
| Ngày 56 | Final Review | Tự review như Senior BA/PO và chấm theo rubric. | Sửa gap, viết retrospective và plan 30 ngày tiếp theo. | Capstone final + self-assessment. |

*Tự đánh giá tuần: \[ \] Tôi hiểu khái niệm \[ \] Tôi tạo được artifact
\[ \] Tôi giải thích được cho người khác \[ \] Tôi áp dụng được vào case
thật*

# 5. Bộ template BA/PO nên dùng

## 5.1 Problem Statement Template

- Context: Hiện tại quy trình/hệ thống vận hành như thế nào?

- Problem: Vấn đề cụ thể là gì?

- Evidence: Dữ liệu hoặc tình huống nào chứng minh vấn đề?

- Impact: Ảnh hưởng tới user/business/operation ra sao?

- Goal: Kết quả mong muốn là gì?

- Success Metric: Đo thành công bằng chỉ số nào?

## 5.2 Discovery Question Checklist

| **Nhóm** | **Câu hỏi gợi ý** |
|----|----|
| WHY | Tại sao cần? Vấn đề gì đang xảy ra? Nếu không làm thì impact gì? |
| WHO | Ai sử dụng? Ai quyết định? Ai bị ảnh hưởng? Ai vận hành? |
| WHAT | Cần thay đổi capability/data/process nào? |
| WHEN | Trigger lúc nào? Status nào? Cut-off/timing/SLA? |
| HOW | Flow hiện tại? Kênh UI/API/batch? Có manual step? |
| WHAT IF | Nếu timeout, duplicate, invalid data, partial failure, concurrent update? |
| DATA | Nguồn dữ liệu? Owner? Validation? Audit? Retention? |
| SUCCESS | KPI nào chứng minh giải pháp tạo value? |

## 5.3 Functional Specification Skeleton

- 1\. Background / Business Context

- 2\. Problem Statement & Objective

- 3\. Stakeholders

- 4\. Scope: In / Out

- 5\. Assumptions / Dependencies / Constraints

- 6\. AS-IS Process

- 7\. TO-BE Process

- 8\. User Stories / Use Cases

- 9\. Business Rules

- 10\. Acceptance Criteria

- 11\. Data / API / UI Impact

- 12\. Error & Exception Handling

- 13\. NFR

- 14\. Permission / Audit / Security

- 15\. UAT / Release / Monitoring

- 16\. Open Questions & Decision Log

## 5.4 Business Rule Template

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Rule format</strong></p>
<p>BR-XXX-001<br />
IF &lt;condition&gt;<br />
AND &lt;condition&gt;<br />
THEN &lt;system/business action&gt;<br />
ELSE &lt;alternative action if needed&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## 5.5 Acceptance Criteria Template

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Given / When / Then</strong></p>
<p>Given &lt;pre-condition&gt;<br />
When &lt;action/trigger&gt;<br />
Then &lt;expected result&gt;<br />
And &lt;additional observable result&gt;</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# 6. Bài tập thực hành có lời giải

## Bài 1 - Admin chỉnh sửa Order sau khi đã tạo

Đề bài: Business yêu cầu "Cho phép Admin chỉnh sửa Order sau khi Order
đã tạo". Hãy phân tích như BA trước khi viết solution.

### Yêu cầu đầu ra

- Problem Statement

- Danh sách stakeholder

- 15 câu hỏi discovery

- Business Rules cần xác minh

- Risk/Impact Matrix

### Lời giải tham khảo

Problem: Một số Order có dữ liệu sai sau khi được tạo; Operation hiện
phải cancel/re-create hoặc xử lý thủ công, gây chậm và có nguy cơ lệch
dữ liệu giữa Order, Supplier, Delivery và Finance.

Câu hỏi trọng tâm: ai được sửa; sửa field nào; status nào; sửa trước/sau
khi gửi Supplier; ảnh hưởng stock, price, payment, invoice, shipment;
cần approval không; có audit log không; notification/sync downstream ra
sao; xử lý concurrent update thế nào.

Business Rule mẫu: BR-ORD-001 - Chỉ role ADMIN_ORDER được sửa.
BR-ORD-002 - Chỉ cho phép sửa khi Order=PENDING. BR-ORD-003 - Thay
quantity phải re-check available stock. BR-ORD-004 - Mọi thay đổi phải
lưu before/after value, user, timestamp và reason.

Risk chính: inventory inconsistency, supplier mismatch, shipping
mismatch, reconciliation error, unauthorized change, race condition.

## Bài 2 - Auto-cancel Sub-order sau 30 phút

Đề bài: Nếu Supplier không xử lý Sub-order sau 30 phút thì hệ thống tự
cancel.

### Lời giải phân tích

- Timer bắt đầu từ thời điểm Sub-order được tạo hay thời điểm gửi
  Supplier thành công?

- 30 phút là elapsed time hay business time?

- Áp dụng cho status nào? PENDING/SENT/WAITING_SUPPLIER?

- Nếu Supplier confirm ở 29:59 nhưng callback tới sau 30:00 thì xử lý
  race condition thế nào?

- Auto-cancel Sub-order hay Parent Order?

- Có hoàn stock, refund, release reservation không?

- Có notification cho Operation/Client/Supplier không?

- Nếu scheduler/job bị down thì cơ chế catch-up thế nào?

- Có retry gọi Supplier cancel API không? Bao nhiêu lần?

- Audit log và metric nào cần ghi?

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Rule mẫu</strong></p>
<p>IF subOrder.status = PENDING AND currentTime - supplierSentAt &gt;=
30 minutes AND no supplier confirmation exists THEN system shall cancel
the sub-order, release reserved inventory, write audit log and emit
cancellation event.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Bài 3 - Product hết stock nhưng Client vẫn hiển thị

Đề bài: Client lấy danh sách Product không thường xuyên nên user có thể
chọn Product đã hết stock.

### Lời giải tham khảo

Root cause không phải "Client quên refresh" mà là thiếu cơ chế đồng bộ
availability đủ tin cậy. Các option: manual refresh, polling định kỳ,
webhook/event, real-time stock check khi order. BA/PO cần so sánh
latency, traffic, complexity, backward compatibility và failure recovery
trước khi chốt solution.

Success metric gợi ý: tỷ lệ order fail do unavailable product \< 1%;
thời gian propagation thay đổi stock \< 2 phút; webhook delivery success
\> 99.5%.

# 7. Rubric tự chấm năng lực cuối khóa

| **Năng lực** | **Junior** | **Middle** | **Senior target** |
|----|----|----|----|
| Problem Analysis | Ghi lại request | Tìm problem và impact | Dùng evidence, root cause, metric và trade-off |
| Requirement | Viết mô tả chức năng | Có flow/rule/AC | Atomic, testable, traceable, đủ exception/NFR |
| Stakeholder | Trao đổi theo yêu cầu | Chủ động workshop và follow-up | Facilitate conflict, decision và expectation |
| System Analysis | Hiểu UI/field | Hiểu API/data/flow | Phân tích integration, race, retry, idempotency, audit |
| Product Thinking | Nhận feature | Biết priority/MVP | Quyết định dựa trên value, data, risk, opportunity cost |
| Delivery | Hỗ trợ clarification | Theo refinement/UAT | Quản lý change, release, monitoring, post-release outcome |

## Cách chấm

- 0 điểm: Chưa làm được.

- 1 điểm: Làm được khi có template/hướng dẫn.

- 2 điểm: Tự làm được với case quen thuộc.

- 3 điểm: Tự làm được với case mới và giải thích được trade-off.

- 4 điểm: Có thể review/coaching người khác và cải tiến cách làm của
  team.

Mục tiêu sau 56 ngày: tối thiểu 2 điểm ở tất cả nhóm và 3 điểm ở
Requirement, Process, Stakeholder, System Analysis hoặc Product Thinking
tùy định hướng nghề nghiệp.

# 8. Bảng theo dõi tiến độ

| **Ngày** | **Hoàn thành** | **Artifact** | **Điểm tự chấm (0-4)** | **Ghi chú / Gap** |
|----|----|----|----|----|
| 1 | \[ \] |  |  |  |
| 2 | \[ \] |  |  |  |
| 3 | \[ \] |  |  |  |
| 4 | \[ \] |  |  |  |
| 5 | \[ \] |  |  |  |
| 6 | \[ \] |  |  |  |
| 7 | \[ \] |  |  |  |
| 8 | \[ \] |  |  |  |
| 9 | \[ \] |  |  |  |
| 10 | \[ \] |  |  |  |
| 11 | \[ \] |  |  |  |
| 12 | \[ \] |  |  |  |
| 13 | \[ \] |  |  |  |
| 14 | \[ \] |  |  |  |
| 15 | \[ \] |  |  |  |
| 16 | \[ \] |  |  |  |
| 17 | \[ \] |  |  |  |
| 18 | \[ \] |  |  |  |
| 19 | \[ \] |  |  |  |
| 20 | \[ \] |  |  |  |
| 21 | \[ \] |  |  |  |
| 22 | \[ \] |  |  |  |
| 23 | \[ \] |  |  |  |
| 24 | \[ \] |  |  |  |
| 25 | \[ \] |  |  |  |
| 26 | \[ \] |  |  |  |
| 27 | \[ \] |  |  |  |
| 28 | \[ \] |  |  |  |
| 29 | \[ \] |  |  |  |
| 30 | \[ \] |  |  |  |
| 31 | \[ \] |  |  |  |
| 32 | \[ \] |  |  |  |
| 33 | \[ \] |  |  |  |
| 34 | \[ \] |  |  |  |
| 35 | \[ \] |  |  |  |
| 36 | \[ \] |  |  |  |
| 37 | \[ \] |  |  |  |
| 38 | \[ \] |  |  |  |
| 39 | \[ \] |  |  |  |
| 40 | \[ \] |  |  |  |
| 41 | \[ \] |  |  |  |
| 42 | \[ \] |  |  |  |
| 43 | \[ \] |  |  |  |
| 44 | \[ \] |  |  |  |
| 45 | \[ \] |  |  |  |
| 46 | \[ \] |  |  |  |
| 47 | \[ \] |  |  |  |
| 48 | \[ \] |  |  |  |
| 49 | \[ \] |  |  |  |
| 50 | \[ \] |  |  |  |
| 51 | \[ \] |  |  |  |
| 52 | \[ \] |  |  |  |
| 53 | \[ \] |  |  |  |
| 54 | \[ \] |  |  |  |
| 55 | \[ \] |  |  |  |
| 56 | \[ \] |  |  |  |

# 9. Sau 56 ngày: lộ trình 30 ngày tiếp theo

Không cần học thêm quá nhiều khái niệm. Chuyển sang luyện bằng case thật
và review chất lượng artifact.

- Tuần 1: Chọn một feature thật đã làm trước đây, viết lại từ Problem
  Statement đến AC.

- Tuần 2: Chọn một flow API/integration, bổ sung sequence, error matrix,
  idempotency, retry, audit.

- Tuần 3: Chọn một backlog thật, áp dụng priority + MVP + metric và giải
  thích trade-off.

- Tuần 4: Tự tổ chức một mock refinement/UAT/release review và ghi lại
  lesson learned.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr>
<th><p><strong>Dấu hiệu bạn đã tiến bộ</strong></p>
<p>Bạn không còn hỏi "Business muốn build gì?" trước tiên. Bạn bắt đầu
bằng "Problem là gì, evidence đâu, impact bao nhiêu, ai bị ảnh hưởng,
rule/exception nào, và làm sao đo value sau khi release?"</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>
