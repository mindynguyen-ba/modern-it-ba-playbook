# Stage 08: Backlog Prep — Write INVEST User Stories & Testable Acceptance Criteria

> **Vị trí trong vòng đời:** Phase 3 của Modern BA Operating Framework.  
> **Lăng kính cố vấn:** Karl Wiegers (Business Rigor) & Joy Beatty (System Dynamics).

---

## 🎯 1. Mục Tiêu Cốt Lõi (Business Objective)

Chuyển dịch các đặc tả kỹ thuật thành các lát cắt backlog giá trị (User Stories) đạt chuẩn INVEST kèm Acceptance Criteria (AC) kiểm chứng được.

### Sản phẩm bàn giao đo đếm được (Concrete Deliverables)
- **User Story Inventory (Phân chia theo Epics / Capabilities)**
- **Testable Acceptance Criteria (Định dạng Given-When-Then / Rule-based)**
- **Definition of Ready (DoR) Checklist**

---

## ⚠️ 2. Bẫy Ngây Thơ Cần Tránh (The Naive Trap)

> [!WARNING]
> **Anti-Pattern thường gặp:**  
> Viết User Story như một bản mô tả kỹ thuật dài dòng, hoặc viết AC mơ hồ kiểu 'hệ thống phản hồi nhanh và chính xác', không thể viết test case.

Hậu quả thực tế: Khi BA mắc bẫy này, rủi ro không chỉ nằm ở việc làm sai tính năng, mà là làm lãng phí hàng trăm giờ phát triển của đội ngũ kỹ thuật để giải quyết một bài toán không có thật hoặc không mang lại giá trị kinh tế.

---

## 🧠 3. Tư Duy Cố Vấn (Senior Mental Model)

> [!NOTE]
> **Nguyên tắc chỉ đạo:**  
> Karl Wiegers: User Story là 'tấm vé cho một cuộc đối thoại' (placeholder for conversation). Acceptance Criteria chính là biên giới để xác định khi nào cuộc đối thoại đó được hiện thực hóa thành công. AC phải kiểm chứng được (Verifiable).

Trong giai đoạn này, sự khác biệt giữa một Junior BA và một Senior/Lead Technical BA nằm ở khả năng **đặt câu hỏi phản biện** và **thiết lập ranh giới vững chắc**.

---

## 🛠️ 4. Quy Trình Thực Thi Thực Chiến (Execution Steps)

1. **Bước 1:** Cắt nhỏ yêu cầu thành các vertical slices giá trị (không cắt theo layer kỹ thuật FE/BE).
2. **Bước 2:** Kiểm tra từng Story theo tiêu chuẩn INVEST (Independent, Negotiable, Valuable, Estimable, Small, Testable).
3. **Bước 3:** Viết AC bao phủ cả Happy Path, Alternate Path và Exception/Edge cases.
4. **Bước 4:** Review DoR cùng đội ngũ Scrum/Engineering trước khi đưa vào Sprint Backlog.

---

## ✅ 5. Điều Kiện Nghiệm Thu Giai Đoạn (Verifiable Quality Gate)

Để hoàn thành Stage 08 và chuyển sang giai đoạn kế tiếp, bắt buộc phải thỏa mãn:

> [!IMPORTANT]
> **Definition of Done (DoD):**  
> 100% User Stories đạt DoR; AC có số liệu hoặc điều kiện logic cụ thể để QA viết được Test Cases tự động.

---
*Điều hướng:* [Quay lại Master Matrix](README.md) · [Về Trang chủ](../../README.md)
