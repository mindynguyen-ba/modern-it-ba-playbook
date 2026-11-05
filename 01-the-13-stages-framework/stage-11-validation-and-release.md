# Stage 11: Validation & Release — Business UAT Scenarios & Data Invariant Sign-offs

> **Vị trí trong vòng đời:** Phase 4 của Modern BA Operating Framework.  
> **Lăng kính cố vấn:** Karl Wiegers (Business Rigor) & Joy Beatty (System Dynamics).

---

## 🎯 1. Mục Tiêu Cốt Lõi (Business Objective)

Thực hiện nghiệm thu nghiệp vụ (UAT) trên môi trường Staging/UAT, kiểm chứng tính toàn vẹn dữ liệu qua SQL Invariants và bảo vệ chất lượng phát hành.

### Sản phẩm bàn giao đo đếm được (Concrete Deliverables)
- **UAT Scenarios Register (Must-run business scenarios)**
- **Data Invariant Validation Scripts (SQL checks cho Zero-loss & Idempotency)**
- **Release Sign-off & Business Readiness Checklist**

---

## ⚠️ 2. Bẫy Ngây Thơ Cần Tránh (The Naive Trap)

> [!WARNING]
> **Anti-Pattern thường gặp:**  
> Đổ hết trách nhiệm nghiệm thu cho QA; coi UAT là test chức năng thông thường. Chỉ bấm thử vài click trên UI mà không kiểm tra dữ liệu ngầm dưới database.

Hậu quả thực tế: Khi BA mắc bẫy này, rủi ro không chỉ nằm ở việc làm sai tính năng, mà là làm lãng phí hàng trăm giờ phát triển của đội ngũ kỹ thuật để giải quyết một bài toán không có thật hoặc không mang lại giá trị kinh tế.

---

## 🧠 3. Tư Duy Cố Vấn (Senior Mental Model)

> [!NOTE]
> **Nguyên tắc chỉ đạo:**  
> Karl Wiegers: QA kiểm tra xem 'phần mềm có chạy đúng như spec viết không' (Verification). BA và Business User kiểm tra xem 'phần mềm có thực sự giải quyết đúng vấn đề nghiệp vụ không' (Validation). Chạy SQL Invariants để chứng minh không có bản ghi nào bị rác hoặc mất mát.

Trong giai đoạn này, sự khác biệt giữa một Junior BA và một Senior/Lead Technical BA nằm ở khả năng **đặt câu hỏi phản biện** và **thiết lập ranh giới vững chắc**.

---

## 🛠️ 4. Quy Trình Thực Thi Thực Chiến (Execution Steps)

1. **Bước 1:** Thiết kế bộ kịch bản UAT dựa trên End-to-End User Journeys và Failure Recovery.
2. **Bước 2:** Phối hợp với Business Stakeholders thực hiện nghiệm thu trên môi trường mô phỏng thực tế.
3. **Bước 3:** Chạy các câu lệnh SQL Invariants để kiểm tra tính toàn vẹn dữ liệu (tất cả query phải trả về 0 row vi phạm).
4. **Bước 4:** Ký biên bản UAT Sign-off và xác nhận sẵn sàng cho kế hoạch phát hành (Go-Live).

---

## ✅ 5. Điều Kiện Nghiệm Thu Giai Đoạn (Verifiable Quality Gate)

Để hoàn thành Stage 11 và chuyển sang giai đoạn kế tiếp, bắt buộc phải thỏa mãn:

> [!IMPORTANT]
> **Definition of Done (DoD):**  
> 100% UAT Scenarios mức độ Must PASS; Toàn bộ câu lệnh SQL Invariant kiểm tra tính toàn vẹn trả về 0 rows vi phạm.

---
*Điều hướng:* [Quay lại Master Matrix](README.md) · [Về Trang chủ](../../README.md)
