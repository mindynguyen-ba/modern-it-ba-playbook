# Stage 05: Requirement Analysis — Classify Requirements, Isolate Business Rules & Decision Tables

> **Vị trí trong vòng đời:** Phase 2 của Modern BA Operating Framework.  
> **Lăng kính cố vấn:** Karl Wiegers (Business Rigor) & Joy Beatty (System Dynamics).

---

## 🎯 1. Mục Tiêu Cốt Lõi (Business Objective)

Phân loại yêu cầu thành Business / User / Functional requirements, bóc tách Business Rules thành thực thể độc lập và mô hình hóa logic điều kiện bằng Decision Tables.

### Sản phẩm bàn giao đo đếm được (Concrete Deliverables)
- **Business Rules Catalogue (Mã hóa BR-xxx độc lập)**
- **Decision Tables (Ma trận logic điều kiện bao phủ 100% trường hợp)**
- **Requirements Classification Matrix (Business -> User -> Functional)**

---

## ⚠️ 2. Bẫy Ngây Thơ Cần Tránh (The Naive Trap)

> [!WARNING]
> **Anti-Pattern thường gặp:**  
> Gộp chung Business Rules vào Functional Requirements hoặc code logic. Hậu quả: Khi chính sách nghiệp vụ thay đổi, không ai biết phải sửa ở đâu và làm vỡ toàn bộ hệ thống.

Hậu quả thực tế: Khi BA mắc bẫy này, rủi ro không chỉ nằm ở việc làm sai tính năng, mà là làm lãng phí hàng trăm giờ phát triển của đội ngũ kỹ thuật để giải quyết một bài toán không có thật hoặc không mang lại giá trị kinh tế.

---

## 🧠 3. Tư Duy Cố Vấn (Senior Mental Model)

> [!NOTE]
> **Nguyên tắc chỉ đạo:**  
> Karl Wiegers: Business Rules là bất biến theo chính sách của tổ chức (ví dụ: 'Khách nợ cước quá 30 ngày phải bị khóa tài khoản'). Phần mềm chỉ là phương tiện thực thi rule đó. Tách rời Business Rules giúp hệ thống có thể thay đổi công nghệ mà không làm vỡ nghiệp vụ.

Trong giai đoạn này, sự khác biệt giữa một Junior BA và một Senior/Lead Technical BA nằm ở khả năng **đặt câu hỏi phản biện** và **thiết lập ranh giới vững chắc**.

---

## 🛠️ 4. Quy Trình Thực Thi Thực Chiến (Execution Steps)

1. **Bước 1:** Trích xuất tất cả chính sách, công thức tính toán và ràng buộc nghiệp vụ thành mã BR-xxx.
2. **Bước 2:** Phân tích các tổ hợp điều kiện phức tạp (nếu có 3 điều kiện nhị phân -> phải có 2^3 = 8 trường hợp).
3. **Bước 3:** Lập bảng Decision Table: Condition Stub, Condition Entries, Action Stub, Action Entries.
4. **Bước 4:** Loại bỏ các trường hợp bất khả thi hoặc gộp các trường hợp cùng hành động (don't care conditions).

---

## ✅ 5. Điều Kiện Nghiệm Thu Giai Đoạn (Verifiable Quality Gate)

Để hoàn thành Stage 05 và chuyển sang giai đoạn kế tiếp, bắt buộc phải thỏa mãn:

> [!IMPORTANT]
> **Definition of Done (DoD):**  
> Mọi Business Rule đều có mã định danh độc lập; Bảng Decision Table bao phủ 100% tổ hợp điều kiện logic, không có ô trống.

---
*Điều hướng:* [Quay lại Master Matrix](README.md) · [Về Trang chủ](../../README.md)
