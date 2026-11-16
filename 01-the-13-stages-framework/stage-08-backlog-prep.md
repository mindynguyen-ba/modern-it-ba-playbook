# Stage 08: Backlog Prep — Write INVEST User Stories & Testable Acceptance Criteria

> **Vị trí trong vòng đời:** Phase 3 của Modern BA Operating Framework.  
> **Lăng kính cố vấn:** Karl Wiegers (Business Rigor & Requirements Hierarchy) & Joy Beatty (System Dynamics & Visual Modeling).

---

## 🎯 1. Mục Tiêu Cốt Lõi (Business Objective)

Chuyển dịch các đặc tả kỹ thuật và mô hình phân tích thành các lát cắt backlog giá trị (**User Stories**) đạt chuẩn **INVEST**, kèm theo hệ thống tiêu chí nghiệm thu (**Acceptance Criteria - AC**) hai tầng có khả năng kiểm chứng nhị phân (Verifiable PASS/FAIL).

### Sản phẩm bàn giao đo đếm được (Concrete Deliverables)
- **User Story Inventory:** Phân rã theo Epics / Capabilities theo chiều dọc (Vertical Slices), gắn mã truy vết `US-xx`.
- **Two-Tier Acceptance Criteria:** 
  1. *Tier 1: Scenario-based AC* (Given-When-Then / BDD Gherkin) cho hành vi người dùng và tương tác giao diện.
  2. *Tier 2: Rule-based & System Invariants AC* cho tính toàn vẹn dữ liệu, API contracts, tính lũy nghiệm (idempotency) và xử lý ngoại lệ.
- **Definition of Ready (DoR) Checklist:** Bộ tiêu chí rà soát trước khi đưa Story vào Sprint Planning.

---

## ⚠️ 2. Bẫy Ngây Thơ Cần Tránh (The Naive Trap)

> [!WARNING]
> **Anti-Pattern thường gặp:**  
> - **Cắt lát ngang (Horizontal Slicing):** Tạo ra các Story riêng cho "Làm API backend", "Vẽ giao diện frontend", "Viết script database". Hậu quả: Không có giá trị độc lập nào được bàn giao cho người dùng cuối ở cuối Sprint.
> - **Template máy móc:** Điền bừa vào mẫu `As a... I want... So that...` nhưng bản chất bên trong là một Functional Requirement thô kệch hoặc một task kỹ thuật thuần túy.
> - **Acceptance Criteria cảm tính:** Dùng các tính từ mơ hồ không thể test (*"hệ thống phản hồi nhanh", "thao tác mượt mà", "hiển thị thông báo lỗi phù hợp"*).
> - **Bỏ quên Failure Modes:** Chỉ mô tả Happy Path, bỏ qua race conditions khi user click đúp, timeout khi gọi payment gateway, hoặc dữ liệu mâu thuẫn khi rớt mạng giữa chừng.

---

## 🧠 3. Bản Đọc Hiểu Thực Chiến: User Stories & Acceptance Criteria Chuyên Sâu

### 3.1 Karl Wiegers Lens: Phân tầng yêu cầu & Tách biệt Business Rules

#### Sự ngộ nhận lớn nhất: User Story không phải là Functional Requirement
User Story thuộc tầng **User Requirements** — nó đóng vai trò là một **lát cắt giá trị (vertical slice)** và là một **tấm vé cho cuộc đối thoại (a placeholder for conversation)** giữa BA, Product Owner, Engineering và QA.

```
[Business Requirement]  ──► Mục tiêu kinh doanh (Tăng tỷ lệ kích hoạt gói tự phục vụ)
         │
         ▼
  [User Requirement]    ──► Lát cắt giá trị / User Story (Admin tự thanh toán nâng gói trực tiếp)
         │
         ▼
[Functional Requirement] ──► Hệ thống làm gì (Tính pro-rata, gọi Payment Gateway, bật Entitlement)
```

#### Tách biệt tuyệt đối: Business Rules $\neq$ Acceptance Criteria
- **Business Rule (Quy tắc nghiệp vụ):** Chính sách kinh doanh bất biến của tổ chức, độc lập với phần mềm (ví dụ: *"Khách nợ cước được hưởng 30 ngày (720 giờ) ân hạn trước khi bị hạn chế quyền truy cập"*).
- **Acceptance Criteria (Tiêu chí nghiệm thu):** Ranh giới kỹ thuật để xác định phần mềm đã thỏa mãn User Story và tuân thủ Business Rule đó trong một phạm vi cụ thể (ví dụ: *"Khi cron job kiểm tra hoá đơn quá 720 giờ kể từ due date, chuyển trạng thái subscription sang RESTRICTED"*).

#### Chuẩn INVEST dưới góc nhìn kỹ thuật
- **Independent:** Tối thiểu hóa phụ thuộc; nếu 2 story phụ thuộc lẫn nhau, hãy gộp lại hoặc định nghĩa boundary contract rõ ràng.
- **Negotiable:** Không biến Story thành hợp đồng cứng nhắc; mở đường cho giải pháp kỹ thuật tối ưu giữa BA và Dev.
- **Valuable:** Phải mang lại giá trị có thể quan sát được cho Actor chính.
- **Estimable:** Đội ngũ kỹ thuật đủ thông tin về phạm vi và rủi ro để ước lượng Story Points.
- **Small (Vertical Slice):** Cắt dọc từ UI $\to$ Logic $\to$ Data $\to$ 3rd-party callback. Đủ nhỏ để hoàn thành trong 1 Sprint.
- **Testable (Verifiable):** AC phải trả về kết quả nhị phân: **PASS** hoặc **FAIL**.

---

### 3.2 Joy Beatty Lens: Nguồn gốc AC từ FSM, Decision Table & Xử lý Failure Modes

#### Đừng viết AC bằng cảm tính: Hãy dẫn xuất từ Visual Models
Một bộ AC xuất sắc không bao giờ đến từ suy đoán tự phát. Nó được chiếu trực tiếp từ hai mô hình nền tảng:
1. **Finite State Machine (FSM):** Mọi chuyển trạng thái (State Transition), điều kiện kích hoạt (Event) và lính canh (Guard Condition) đều biến thành một AC.
2. **Decision Table:** Mọi cột trong bảng quyết định (tổ hợp $2^n$ điều kiện) đều tương ứng với một Scenario hoặc Rule trong AC.

```
[Mô hình FSM / State Transition] ────────┐
                                         ├─► [Acceptance Criteria (Tier 1: BDD + Tier 2: Invariants)]
[Bảng quyết định / Decision Table] ──────┘
```

#### Cấu trúc AC hai tầng (Two-Tier AC Architecture)
1. **Tier 1: Scenario-based (Given-When-Then / Gherkin)**
   - Phù hợp cho luồng tương tác người dùng, kiểm thử hành vi end-to-end (BDD).
   - *Quy tắc:* Mỗi scenario chỉ kiểm tra một hành vi duy nhất; không gom lỗi validation chung vào happy path.
2. **Tier 2: Rule-based & System Invariants (Technical Contracts)**
   - Phù hợp cho backend logic, data integrity, idempotent processing, timeout handling và boundary isolation.

#### Bịt kín 3 hố đen kỹ thuật (Technical Failure Modes)
1. **Idempotency & Race Condition:**  
   Người dùng click đúp nút thanh toán hoặc cổng thanh toán gửi webhook lặp $\to$ AC bắt buộc quy định: *Sử dụng `Idempotency-Key`, kiểm tra trùng lặp trong cache (Redis) và tuyệt đối không tạo giao dịch trừ tiền thứ hai.*
2. **Downstream Timeout & Partial Failure:**  
   Cổng thanh toán trừ tiền thành công nhưng service kích hoạt quyền (Entitlement Service) bị timeout hoặc trả về lỗi 500 $\to$ AC bắt buộc quy định: *Giao dịch chuyển sang trạng thái `ACTIVATION_FAILED`, kích hoạt cơ chế retry tự động theo Exponential Backoff qua Message Queue (RabbitMQ/Kafka), tuyệt đối không trừ tiền lại.*
3. **Data Preservation & Reversibility:**  
   Hạ gói (Downgrade) hoặc tài khoản bị giới hạn $\to$ AC bắt buộc quy định: *Chuyển sang chế độ Read-only đối với dữ liệu vượt quota, cấm tự tiện xóa dữ liệu (No-data-loss Invariant).*

---

## 🔍 4. Case Study Minh Họa: Naive BA vs Senior Technical BA

### ❌ Trường hợp ngây thơ (Naive BA)
> **User Story:** Là người dùng, tôi muốn nâng cấp gói tài khoản để sử dụng nhiều tính năng hơn.  
> **Acceptance Criteria:**  
> - Hiển thị danh sách các gói cước để người dùng chọn.  
> - Bấm thanh toán thành công thì được nâng gói.  
> - Nếu có lỗi thì hiển thị thông báo lỗi phù hợp.

*Hậu quả thực tế:* Dev không biết tính toán cước chênh lệch (pro-rata) ra sao; QA không biết test case timeout như thế nào; Backend không thiết kế idempotency dẫn đến trừ tiền 2 lần khi mạng chập chờn.

---

### ✅ Trường hợp thực chiến (Senior Technical BA)

> **Story ID:** `US-03` — *Self-Service Paid Upgrade: Immediate Payment & Activation*  
> **Traceability:** Traces to `BO-01` (Doanh thu self-service); Governed by `BR-UPG-01` (Immediate charge, pro-rata calculation) & `BR-UPG-02` (Single active change request).  
> **User Story:**  
> *Là Account Owner của workspace,*  
> *tôi muốn xác nhận thanh toán khoản phí chênh lệch (pro-rata) của gói cước mới ngay tại phiên làm việc,*  
> *để workspace được tự động mở rộng quyền hạn và tính năng nâng cao ngay lập tức mà không cần nhân viên hỗ trợ can thiệp.*

#### Two-Tier Acceptance Criteria:

##### Tier 1: Scenario-based (Behavioral & UX Contracts)
```gherkin
Scenario: Upgrade thanh toán và kích hoạt thành công (Happy Path)
  Given Workspace đang ở gói "Standard" và Account Owner đang ở màn hình Checkout
  When Account Owner bấm "Xác nhận & Thanh toán" với thẻ tín dụng hợp lệ
  Then Hệ thống tạo bản ghi Payment Attempt với unique idempotency_key
  And Chuyển trạng thái Subscription Change Request (SCR) từ DRAFT sang PAYMENT_PENDING
  And Sau khi Payment Gateway phản hồi webhook HTTP 200 SUCCESS:
      - Cập nhật trạng thái SCR sang APPLIED
      - Cập nhật Current Plan của Workspace thành "Pro"
      - Cấp phát dung lượng và tính năng mới ngay lập tức
      - Gửi email hoá đơn điện tử (PDF kèm mã giao dịch) đến Account Owner
      - Điều hướng người dùng về Workspace Dashboard với thông báo chúc mừng.

Scenario: Xử lý thẻ bị từ chối (Alternate Path)
  Given Account Owner đang thực hiện thanh toán cho SCR ở trạng thái PAYMENT_PENDING
  When Payment Gateway trả về mã lỗi "card_declined"
  Then Hệ thống chuyển trạng thái SCR sang PAYMENT_FAILED
  And Giữ nguyên gói "Standard" hiện tại của Workspace
  And Hiển thị lý do từ chối thẻ từ cổng thanh toán kèm nút "Thử lại bằng phương thức khác"
  And Tuyệt đối không khoá hay làm gián đoạn quyền truy cập hiện có của workspace.
```

##### Tier 2: Rule-based & System Invariants (Technical Contracts)
* **AC-INV-01 (Idempotency Contract):** Request thanh toán `POST /change-requests/{id}/payment` bắt buộc kèm header `Idempotency-Key: {uuid}`. Nếu nhận request trùng lặp trong vòng 300 giây, trả về cached response ban đầu, cấm gọi sang Payment Gateway lần 2.
* **AC-INV-02 (Downstream Failure Isolation):** Nếu trừ tiền thành công nhưng Entitlement Service timeout quá 5 giây hoặc trả về HTTP 5xx:
  * Trạng thái SCR bắt buộc chuyển sang `ACTIVATION_FAILED` (không được để ở `PAYMENT_PENDING` hoặc chuyển sang `APPLIED`).
  * Hệ thống tự động đẩy job vào Dead Letter Queue (DLQ) để retry 3 lần theo cơ chế Exponential Backoff.
  * Hiển thị banner cảnh báo: *"Thanh toán đã được ghi nhận. Hệ thống đang hoàn tất thiết lập tài nguyên trong ít phút."* kèm mã tra cứu `SCR-ID`.

---

## 🛠️ 5. Quy Trình Thực Thi Thực Chiến (Execution Steps)

1. **Bước 1 — Vertical Slicing:** Cắt nhỏ Epic thành các User Story theo lát cắt dọc giá trị end-to-end; kiểm tra 6 tiêu chuẩn INVEST.
2. **Bước 2 — Derive from FSM & Decision Tables:** Đối chiếu sơ đồ chuyển trạng thái và bảng quyết định từ Stage 05 & 07 để xác định đầy đủ các nhánh Happy Path, Alternate Path và Exception.
3. **Bước 3 — Author Two-Tier AC:** Soạn thảo Tier 1 (BDD Gherkin) cho UX/QA và Tier 2 (Invariants & Failure Modes) cho Backend/Architecture.
4. **Bước 4 — Ambiguity & Verifiability Inspection:** Rà soát từng câu chữ trong AC; loại bỏ toàn bộ tính từ chủ quan; đảm bảo 100% điều kiện có thể kiểm chứng được tự động.
5. **Bước 5 — Definition of Ready (DoR) Gate:** Tiến hành session Backlog Refinement cùng Tech Lead, Dev và QA để thống nhất ranh giới và chốt Story Points.

---

## ✅ 6. Điều Kiện Nghiệm Thu Giai Đoạn (Verifiable Quality Gate)

Để hoàn thành Stage 08 và chuyển sang giai đoạn kế tiếp, bắt buộc phải thỏa mãn:

> [!IMPORTANT]
> **Definition of Done (DoD) cho Stage 08:**  
> 1. **100% User Stories đạt chuẩn INVEST** và được cắt theo chiều dọc (Zero horizontal technical stories).
> 2. **100% User Stories sở hữu Two-Tier AC** (Scenario-based + Rule-based System Invariants).
> 3. **Tất cả Failure Modes trọng yếu** (Idempotency, Timeout, Downstream Failure, Data Loss Prevention) đều được định nghĩa trạng thái xử lý rõ ràng.
> 4. **QA và Engineering Lead ký duyệt DoR**, xác nhận AC đủ điều kiện để viết Test Automation Scripts nhị phân (PASS/FAIL).

---

## 🎯 7. Mentor Challenge: Hai Câu Hỏi Tự Phản Biện

1. *"Nếu người dùng bị rớt mạng ngay tại tích tắc sau khi bấm Xác nhận (tiền đã trừ tại ngân hàng nhưng trình duyệt chưa nhận được kết quả), User Story và AC của bạn đã quy định hệ thống xử lý tình huống này như thế nào để khách hàng không hoảng loạn và không bị trừ tiền 2 lần?"*
2. *"Đội QA có thể lấy trực tiếp bộ AC của bạn để viết bộ Data Matrix kiểm thử tự động với các giá trị đầu vào/đầu ra cụ thể mà không cần phải gõ cửa hỏi lại bạn bất kỳ câu nào không?"*

---
*Điều hướng:* [Quay lại Master Matrix](README.md) · [Về Trang chủ](../../README.md)
