# Data Modeling & SQL Invariants

## 1. Chuẩn Hóa Cơ Sở Dữ Liệu (3NF) Cho BA

BA cần hiểu mô hình hóa dữ liệu để tránh tạo ra các cấu trúc bảng dị tật, dư thừa dữ liệu hoặc vi phạm tính toàn vẹn tham chiếu.

* **1NF (First Normal Form):** Mỗi cột chỉ chứa một giá trị nguyên tố (Atomic values), không chứa danh sách hay mảng giá trị gộp chung.
* **2NF (Second Normal Form):** Đạt 1NF và mọi thuộc tính không khóa phải phụ thuộc hoàn toàn vào toàn bộ khóa chính (Composite key dependency).
* **3NF (Third Normal Form):** Đạt 2NF và không có thuộc tính không khóa nào phụ thuộc bắc cầu vào khóa chính (No transitive dependency).

---

## 2. Phân Tách Transaction Tables vs Configuration Tables

* **Configuration Tables (Bảng cấu hình):** Lưu danh mục gói cước, tính năng, hạn ngạch quota, giá niêm yết. Dữ liệu này ít thay đổi, do Admin quản trị.
* **Transaction Tables (Bảng giao dịch):** Lưu lịch sử đổi gói, hóa đơn, lượt thanh toán. Bảng này tăng trưởng liên tục, có khóa ngoại tham chiếu đến bảng cấu hình, và **bắt buộc phải snapshot lại giá và thông tin tại thời điểm giao dịch**.

---

## 3. SQL Invariants — Tự Động Hóa Kiểm Chứng Chất Lượng Dữ Liệu

SQL Invariants là các câu truy vấn được BA viết ra để kiểm tra các quy tắc nghiệp vụ bất biến. **Mọi câu truy vấn Invariant đạt chuẩn đều phải trả về đúng 0 rows.** Nếu có bất kỳ dòng nào xuất hiện, hệ thống đã vi phạm logic nghiệp vụ!

### Ví dụ 1: Không có thanh toán mồ côi (No orphan payments)
```sql
-- Invariant: Mọi lượt thanh toán thành công đều phải gắn với một Hóa đơn hoặc Yêu cầu đổi gói
SELECT payment_id, amount, created_at 
FROM payment_attempts 
WHERE status = 'SUCCESS' 
  AND invoice_id IS NULL 
  AND change_request_id IS NULL;
```

### Ví dụ 2: Zero Data Loss sau khi Downgrade gói cước
```sql
-- Invariant: Không có dữ liệu khách hàng nào bị xóa mất khi hạ cấp gói cước
SELECT w.workspace_id, w.plan_code, COUNT(d.doc_id) as total_docs
FROM workspaces w
JOIN documents d ON w.workspace_id = d.workspace_id
WHERE w.plan_code = 'STARTER'
GROUP BY w.workspace_id, w.plan_code
HAVING total_docs < 0; -- Logic kiểm tra tính toàn vẹn
```
