# Stage 01: Discovery — Clarify Request, AS-IS Evidence & Root Cause Analysis

> **Vị trí trong vòng đời:** Phase 1 của Modern BA Operating Framework.  
> **Lăng kính cố vấn:** Karl Wiegers (Business Rigor) & Joy Beatty (System Dynamics).

---

## 🎯 1. Mục Tiêu Cốt Lõi (Business Objective)

Làm rõ căn nguyên của vấn đề nghiệp vụ, thu thập bằng chứng thực tế của hiện trạng (AS-IS), và chứng minh vấn đề đó có đáng để đầu tư giải quyết hay không.

### Sản phẩm bàn giao đo đếm được (Concrete Deliverables)
- **Problem Brief (Đặc tả vấn đề không chứa giải pháp)**
- **AS-IS Assessment & Evidence Log (Đo lường hiện trạng qua số liệu thật)**
- **Root Cause Map (Sơ đồ 5 Whys / Fishbone phân rã nguyên nhân gốc rễ)**

---

## ⚠️ 2. Bẫy Ngây Thơ Cần Tránh (The Naive Trap)

> [!WARNING]
> **Anti-Pattern thường gặp:**  
> Vừa nghe stakeholder mô tả là nhảy ngay vào thiết kế màn hình hoặc kết luận 'hệ thống cần tính năng X'. Coi lời than phiền của user là vấn đề cốt lõi.

Hậu quả thực tế: Khi BA mắc bẫy này, rủi ro không chỉ nằm ở việc làm sai tính năng, mà là làm lãng phí hàng trăm giờ phát triển của đội ngũ kỹ thuật để giải quyết một bài toán không có thật hoặc không mang lại giá trị kinh tế.

---

## 🧠 3. Tư Duy Cố Vấn (Senior Mental Model)

> [!NOTE]
> **Nguyên tắc chỉ đạo:**  
> Karl Wiegers: Phân biệt rạch ròi Symptom (triệu chứng bề nổi) khỏi Root Cause (căn nguyên). Nếu chỉ chữa triệu chứng, vấn đề sẽ tái phát dưới hình thái khác.

Trong giai đoạn này, sự khác biệt giữa một Junior BA và một Senior/Lead Technical BA nằm ở khả năng **đặt câu hỏi phản biện** và **thiết lập ranh giới vững chắc**.

---

## 🛠️ 4. Quy Trình Thực Thi Thực Chiến (Execution Steps)

1. **Bước 1:** Thu thập Trigger & Request ban đầu từ stakeholder chính.
2. **Bước 2:** Quan sát và trích xuất số liệu vận hành thực tế của AS-IS (latency, tỷ lệ lỗi, chi phí nhân sự).
3. **Bước 3:** Thực hiện kỹ thuật 5 Whys để đào sâu xuống lớp nguyên nhân quy trình hoặc dữ liệu.
4. **Bước 4:** Viết Problem Statement theo cấu trúc: [Đối tượng] gặp [Vấn đề] dẫn đến [Hậu quả] với mức độ thiệt hại [Số liệu].

---

## ✅ 5. Điều Kiện Nghiệm Thu Giai Đoạn (Verifiable Quality Gate)

Để hoàn thành Stage 01 và chuyển sang giai đoạn kế tiếp, bắt buộc phải thỏa mãn:

> [!IMPORTANT]
> **Definition of Done (DoD):**  
> Problem Statement được Business Sponsor ký nhận; văn bản không chứa bất kỳ thuật ngữ giải pháp hay công nghệ nào.

---
*Điều hướng:* [Quay lại Master Matrix](README.md) · [Về Trang chủ](../../README.md)
