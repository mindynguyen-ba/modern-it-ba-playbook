# Stage 09: Requirement Validation — Formal Requirement Inspection & Ambiguity Elimination

> **Vị trí trong vòng đời:** Phase 3 của Modern BA Operating Framework.  
> **Lăng kính cố vấn:** Karl Wiegers (Business Rigor) & Joy Beatty (System Dynamics).

---

## 🎯 1. Mục Tiêu Cốt Lõi (Business Objective)

Tổ chức rà soát phản biện nghiêm ngặt (Inspection) để phát hiện và triệt tiêu toàn bộ điểm mơ hồ, mâu thuẫn, thiếu sót trước khi chuyển giao lập trình.

### Sản phẩm bàn giao đo đếm được (Concrete Deliverables)
- **Requirement Inspection Log & Defect Density Report**
- **Ambiguity Checklist Sign-off**
- **Open Questions & Clarifications Register (Đã đóng 100% P1 blockers)**

---

## ⚠️ 2. Bẫy Ngây Thơ Cần Tránh (The Naive Trap)

> [!WARNING]
> **Anti-Pattern thường gặp:**  
> Gửi tài liệu qua email hoặc chat và nhờ mọi người 'xem giúp nhé'. Xem lướt bề nổi, không có checklist kiểm tra lỗi logic và sự mâu thuẫn giữa các tài liệu.

Hậu quả thực tế: Khi BA mắc bẫy này, rủi ro không chỉ nằm ở việc làm sai tính năng, mà là làm lãng phí hàng trăm giờ phát triển của đội ngũ kỹ thuật để giải quyết một bài toán không có thật hoặc không mang lại giá trị kinh tế.

---

## 🧠 3. Tư Duy Cố Vấn (Senior Mental Model)

> [!NOTE]
> **Nguyên tắc chỉ đạo:**  
> Karl Wiegers: Chi phí sửa lỗi requirement ở giai đoạn coding cao gấp 10 lần, và ở giai đoạn production cao gấp 100 lần. Requirement Inspection là hoạt động QA có ROI cao nhất trong toàn bộ vòng đời phát triển.

Trong giai đoạn này, sự khác biệt giữa một Junior BA và một Senior/Lead Technical BA nằm ở khả năng **đặt câu hỏi phản biện** và **thiết lập ranh giới vững chắc**.

---

## 🛠️ 4. Quy Trình Thực Thi Thực Chiến (Execution Steps)

1. **Bước 1:** Tổ chức phiên Formal Inspection với sự tham gia của Dev Lead, QA Lead và Product Owner.
2. **Bước 2:** Rà soát tài liệu theo Ambiguity Checklist (tìm từ ngữ mơ hồ: 'khoảng', 'nhanh chóng', 'tối ưu').
3. **Bước 3:** Đóng vai Tester và Hacker: Cố tình tìm các kịch bản phá vỡ logic nghiệp vụ.
4. **Bước 4:** Ghi nhận defect vào Inspection Log và cập nhật tài liệu cho đến khi đạt chuẩn.

---

## ✅ 5. Điều Kiện Nghiệm Thu Giai Đoạn (Verifiable Quality Gate)

Để hoàn thành Stage 09 và chuyển sang giai đoạn kế tiếp, bắt buộc phải thỏa mãn:

> [!IMPORTANT]
> **Definition of Done (DoD):**  
> Tài liệu đạt 0 blocker defects; 100% Open Questions cấp độ P1 được đóng bằng Decision hoặc Approved Baseline.

---
*Điều hướng:* [Quay lại Master Matrix](README.md) · [Về Trang chủ](../../README.md)
