# Two-Tier User Story & Acceptance Criteria Template

> **Phù hợp cho:** Agile / Scrum Teams, Technical BA, Product Owners thiết kế backlog đạt chuẩn Definition of Ready (DoR).

---

## 📌 1. User Story Header & Traceability

| Thuộc tính | Giá trị mẫu / Hướng dẫn |
|---|---|
| **Story ID** | `US-xx` (ví dụ: `US-03`) |
| **Epic / Capability** | `CAP-xx` — Tên Capability tương ứng |
| **Business Objective (BO)** | Trace tới `BO-xx` (ví dụ: `BO-01: Tăng 20% doanh thu tự phục vụ`) |
| **Governing Business Rules** | Danh sách mã `BR-xxx` chi phối (ví dụ: `BR-UPG-01`, `BR-UPG-02`) |
| **Primary Actor** | Persona cụ thể có thẩm quyền (ví dụ: *Account Owner*, *Billing Admin*) |
| **FSM State Reference** | Thực thể và trạng thái liên quan (ví dụ: `SCR: DRAFT -> PAYMENT_PENDING -> APPLIED`) |

---

## 📝 2. User Story Statement

```text
As a [Specific Actor / Persona],
I want [User-Observable Action / Capability],
So that [Clear Business Value / Personal Benefit].
```

> **Nguyên tắc:** Lát cắt dọc (Vertical Slice) mang lại giá trị độc lập, không viết story cắt ngang theo tầng kỹ thuật (FE/BE/DB).

---

## 🎯 3. Two-Tier Acceptance Criteria (AC)

### Tier 1: Scenario-based (BDD Gherkin — Behavioral & UX Contracts)
*Dành cho Product, QA Automation (Playwright/Cypress/Cucumber) và Frontend Developers.*

```gherkin
Scenario: [Tên kịch bản Happy Path]
  Given [Tiền đề: Trạng thái ban đầu của hệ thống và người dùng]
  When [Hành động duy nhất của người dùng hoặc sự kiện kích hoạt]
  Then [Trạng thái mới của thực thể]
  And [Phản hồi quan sát được trên giao diện / thông báo]
  And [Tác vụ background hoàn tất: email, event bus, webhook].

Scenario: [Tên kịch bản Alternate / Validation Path]
  Given [Tiền đề tương ứng]
  When [Người dùng nhập dữ liệu không hợp lệ hoặc hành động bị chặn]
  Then [Hệ thống giữ nguyên trạng thái an toàn ban đầu]
  And [Hiển thị thông báo hướng dẫn khắc phục cụ thể].
```

---

### Tier 2: Rule-based & System Invariants (Technical Contracts)
*Dành cho Backend Developers, System Architects và Integration QA.*

| Mã AC | Phạm vi kỹ thuật | Ràng buộc bất biến (System Invariant) & Xử lý Failure Mode |
|---|---|---|
| **AC-INV-01** | **Idempotency & Race Condition** | Endpoint `POST /...` bắt buộc kiểm tra `Idempotency-Key`. Nếu nhận request trùng trong vòng $X$ giây, trả về cached response ban đầu; cấm tạo bản ghi giao dịch lần 2. |
| **AC-INV-02** | **Partial Failure & Downstream Timeout** | Khi downstream service (ví dụ: Payment/Entitlement) timeout quá $Y$ giây hoặc trả về HTTP 5xx: Chuyển entity sang trạng thái `{STAGE}_FAILED`, đẩy message vào Dead Letter Queue (DLQ) để retry $Z$ lần theo Exponential Backoff, tuyệt đối không trừ tiền lại. |
| **AC-INV-03** | **Data Loss Prevention** | Khi entity hạ cấp hoặc hết hạn: Chuyển dữ liệu vượt hạn mức sang chế độ `Read-Only`, cấm tự ý xóa dữ liệu của khách hàng. |
| **AC-INV-04** | **Concurrency Boundary** | Mỗi tài khoản chỉ được phép có tối đa 01 Change Request ở trạng thái chưa hoàn tất (Active/Pending). Trả về HTTP 409 Conflict nếu có request tạo mới đồng thời. |

---

## ✅ 4. Definition of Ready (DoR) Gate Checklist

- [ ] Story đạt chuẩn INVEST (Independent, Negotiable, Valuable, Estimable, Small, Testable).
- [ ] Bóc tách Business Rules thành mã `BR-xxx`, không hardcode vào AC.
- [ ] Có đầy đủ cả Tier 1 (BDD Scenarios) và Tier 2 (Technical Invariants).
- [ ] Mọi failure mode trọng yếu (Idempotency, Timeout, Downstream Error) đều có trạng thái xử lý rõ ràng.
- [ ] Tech Lead và QA Lead đã thống nhất nghiệm thu DoR trước khi vào Sprint.
