# Requirement Inspection & Ambiguity Checklist

Dùng biểu mẫu này trong các phiên Formal Requirement Review với Dev & QA Lead.

---

## Danh Mục Kiểm Tra Tính Mơ Hồ (Ambiguity Checklist)

| STT | Dấu hiệu lỗi | Câu hỏi rà soát | Kết quả (PASS/FAIL) |
|---|---|---|---|
| 1 | **Từ ngữ định tính mơ hồ** | Có xuất hiện các từ: *nhanh chóng, tối ưu, dễ dùng, thân thiện, khoảng, chừng* không? | |
| 2 | **Ranh giới không xác định** | Có các điều kiện mở: *v.v., và các trường hợp khác, nếu cần thiết* không? | |
| 3 | **Trạng thái mồ côi (Orphan)** | Có trạng thái nào được tạo ra mà không có đường chuyển tiếp kết thúc không? | |
| 4 | **Thiếu cơ chế Timeout** | Các lời gọi tích hợp bên ngoài có quy định rõ thời gian timeout (giây) và số lần retry không? | |
| 5 | **Trộn lẫn Rule vào Spec** | Có quy tắc kinh doanh nào bị viết cứng vào hành vi giao diện không? | |
| 6 | **Khả năng kiểm chứng (Verifiability)** | QA có thể viết được kịch bản test cụ thể với kết quả Pass/Fail rõ ràng không? | |
| 7 | **Tính truy vết (Traceability)** | User Story này có liên kết trực tiếp với Business Objective nào không? | |
