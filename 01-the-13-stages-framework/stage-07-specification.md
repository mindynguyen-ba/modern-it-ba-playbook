# Stage 07: Specification — Detail Function, Model Process (BPMN), Screen & Data/State (FSM)

> **Vị trí trong vòng đời:** Phase 3 của Modern BA Operating Framework.  
> **Lăng kính cố vấn:** Karl Wiegers (Business Rigor) & Joy Beatty (System Dynamics).

---

## 🎯 1. Mục Tiêu Cốt Lõi (Business Objective)

Mô hình hóa chi tiết và trực quan toàn bộ hệ thống: BPMN 2.0 Collaboration, Finite State Machines (FSM), Hợp đồng màn hình (Screen ID Contracts) và Cấu trúc dữ liệu (ERD).

### Sản phẩm bàn giao đo đếm được (Concrete Deliverables)
- **BPMN 2.0 Collaboration Diagrams (5-Pool interaction order, Event-based & Timer Gateways)**
- **Finite State Machine (FSM) Lifecycle Diagrams (Tách biệt các failure stages)**
- **UI State Specifications (Screen Flow & State ID Contract {SCREEN}.S{NN})**
- **Data Model / ERD & Data Dictionary (Chuẩn hóa 3NF, Idempotency keys)**

---

## ⚠️ 2. Bẫy Ngây Thơ Cần Tránh (The Naive Trap)

> [!WARNING]
> **Anti-Pattern thường gặp:**  
> Vẽ flowchart sơ sài một chiều, kết nối mũi tên xuyên qua các hệ thống vô tội vạ; trạng thái FSM chỉ có 2 nhãn ngây thơ 'Success / Fail'; không bắt timeout và lỗi mạng.

Hậu quả thực tế: Khi BA mắc bẫy này, rủi ro không chỉ nằm ở việc làm sai tính năng, mà là làm lãng phí hàng trăm giờ phát triển của đội ngũ kỹ thuật để giải quyết một bài toán không có thật hoặc không mang lại giá trị kinh tế.

---

## 🧠 3. Tư Duy Cố Vấn (Senior Mental Model)

> [!NOTE]
> **Nguyên tắc chỉ đạo:**  
> Joy Beatty: Visual-First & State Dynamics. Logic hệ thống nằm ở sơ đồ trực quan, không nằm ở văn bản dài dòng. Bịt kín mọi failure modes: rớt mạng khi thanh toán, duplicate callback, cron job timeout, và phân tầng trạng thái lỗi độc lập.

Trong giai đoạn này, sự khác biệt giữa một Junior BA và một Senior/Lead Technical BA nằm ở khả năng **đặt câu hỏi phản biện** và **thiết lập ranh giới vững chắc**.

---

## 🛠️ 4. Quy Trình Thực Thi Thực Chiến (Execution Steps)

1. **Bước 1:** Vẽ BPMN Collaboration: Pool cho từng hệ thống độc lập, Sequence Flow nội bộ, Message Flow giữa các Pool.
2. **Bước 2:** Thiết kế FSM cho từng thực thể cốt lõi: Xác định State, Event, Guard Condition và Action.
3. **Bước 3:** Quy chuẩn Screen ID ({DOMAIN}-{NN}) và UI States ({SCREEN}.S{NN}) để QA/Dev trace chính xác.
4. **Bước 4:** Thiết lập Data Model: Khóa ngoại, ràng buộc quan hệ, trường Idempotency key chống trùng lặp.

---

## ✅ 5. Điều Kiện Nghiệm Thu Giai Đoạn (Verifiable Quality Gate)

Để hoàn thành Stage 07 và chuyển sang giai đoạn kế tiếp, bắt buộc phải thỏa mãn:

> [!IMPORTANT]
> **Definition of Done (DoD):**  
> Sơ đồ BPMN đạt 100% chuẩn syntax (không có Sequence Flow vượt Pool); FSM zero orphan states; Screen/UI states có contract rõ ràng.

---
*Điều hướng:* [Quay lại Master Matrix](README.md) · [Về Trang chủ](../../README.md)
