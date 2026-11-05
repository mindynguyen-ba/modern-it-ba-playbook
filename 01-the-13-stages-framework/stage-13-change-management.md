# Stage 13: Change Management — Baseline Invariance, Impact Analysis & Change Request Governance

> **Vị trí trong vòng đời:** Phase 4 của Modern BA Operating Framework.  
> **Lăng kính cố vấn:** Karl Wiegers (Business Rigor) & Joy Beatty (System Dynamics).

---

## 🎯 1. Mục Tiêu Cốt Lõi (Business Objective)

Quản trị các yêu cầu thay đổi phát sinh sau khi baseline đã đóng, đánh giá tác động toàn diện và duy trì tính nhất quán của hệ thống tài liệu đặc tả.

### Sản phẩm bàn giao đo đếm được (Concrete Deliverables)
- **Change Request (CR) Log & Evaluation Forms**
- **Impact Analysis Matrix (Scope, Architecture, Cost, Timeline, Risk)**
- **Updated Baseline Version & Traceability Audit**

---

## ⚠️ 2. Bẫy Ngây Thơ Cần Tránh (The Naive Trap)

> [!WARNING]
> **Anti-Pattern thường gặp:**  
> Ai yêu cầu đổi gì cũng gật đầu đồng ý ngay (Scope Creep); hoặc tự tiện sửa trực tiếp vào file spec cũ mà không lưu vết lý do tại sao thay đổi.

Hậu quả thực tế: Khi BA mắc bẫy này, rủi ro không chỉ nằm ở việc làm sai tính năng, mà là làm lãng phí hàng trăm giờ phát triển của đội ngũ kỹ thuật để giải quyết một bài toán không có thật hoặc không mang lại giá trị kinh tế.

---

## 🧠 3. Tư Duy Cố Vấn (Senior Mental Model)

> [!NOTE]
> **Nguyên tắc chỉ đạo:**  
> Karl Wiegers: Thay đổi là tất yếu, nhưng thay đổi không kiểm soát là thảm họa. Baseline là bất biến cho đến khi có Change Request chính thức được phê duyệt. Mọi thay đổi đều phải trả giá bằng thời gian, tiền bạc hoặc cắt giảm phạm vi khác.

Trong giai đoạn này, sự khác biệt giữa một Junior BA và một Senior/Lead Technical BA nằm ở khả năng **đặt câu hỏi phản biện** và **thiết lập ranh giới vững chắc**.

---

## 🛠️ 4. Quy Trình Thực Thi Thực Chiến (Execution Steps)

1. **Bước 1:** Tiếp nhận yêu cầu thay đổi và cấp mã định danh CR-xxx.
2. **Bước 2:** Thực hiện Impact Analysis: Phân tích ảnh hưởng tới User Stories, Process, State, Database và Timeline.
3. **Bước 3:** Đưa ra khuyến nghị: Chấp thuận, Từ chối, hoặc Dời sang Phase sau.
4. **Bước 4:** Sau khi CR được duyệt, cập nhật đồng bộ toàn bộ tài liệu spec, ma trận traceability và thông báo cho dev/QA.

---

## ✅ 5. Điều Kiện Nghiệm Thu Giai Đoạn (Verifiable Quality Gate)

Để hoàn thành Stage 13 và chuyển sang giai đoạn kế tiếp, bắt buộc phải thỏa mãn:

> [!IMPORTANT]
> **Definition of Done (DoD):**  
> Mọi thay đổi trong sprint/release đều có CR tương ứng; tài liệu đặc tả được cập nhật phiên bản mới nhất kèm vết tích truy vết.

---
*Điều hướng:* [Quay lại Master Matrix](README.md) · [Về Trang chủ](../../README.md)
