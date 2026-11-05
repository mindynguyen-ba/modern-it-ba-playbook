# API Contracts & Idempotency Design

## 1. RESTful API Contract Standards cho BA

Một đặc tả API của BA không cần viết code chi tiết, nhưng phải chuẩn xác về mặt **Contract & Payload Semantics**:

1. **HTTP Verbs:**
   * `GET`: Chỉ đọc dữ liệu, an toàn và không làm thay đổi trạng thái (Safe & Idempotent).
   * `POST`: Tạo mới tài nguyên hoặc kích hoạt một hành động nghiệp vụ.
   * `PUT`: Thay thế toàn bộ tài nguyên.
   * `PATCH`: Cập nhật một phần tài nguyên.
   * `DELETE`: Xóa tài nguyên (Idempotent).

2. **Standard HTTP Status Codes:**
   * `200 OK`: Thành công với payload trả về.
   * `201 Created`: Tạo mới thành công (thường đi kèm `Location` header).
   * `202 Accepted`: Đã tiếp nhận yêu cầu bất đồng bộ, đang xử lý ngầm.
   * `400 Bad Request`: Payload sai định dạng hoặc vi phạm validate đầu vào.
   * `401 Unauthorized`: Chưa đăng nhập / token không hợp lệ.
   * `403 Forbidden`: Đã đăng nhập nhưng không có quyền hạn (RBAC violation).
   * `404 Not Found`: Không tìm thấy tài nguyên.
   * `409 Conflict`: Xung đột trạng thái nghiệp vụ (ví dụ: đang có yêu cầu khác đang chờ xử lý).
   * `422 Unprocessable Entity`: Cú pháp đúng nhưng vi phạm Business Rule.
   * `500 Internal Server Error`: Lỗi sập hệ thống nội bộ.

---

## 2. Cơ chế Idempotency Key

Trong các giao dịch tiền tệ hoặc đơn hàng, nếu người dùng bấm 2 lần do mạng lag, hoặc webhook bắn lại, hệ thống có thể bị trừ tiền 2 lần.

### Thiết kế chuẩn:
Header: `Idempotency-Key: <UUID v4>`
* Backend nhận request -> kiểm tra key trong Redis/Cache:
  * Nếu key chưa tồn tại -> Xử lý giao dịch, lưu kết quả kèm key (TTL 24h).
  * Nếu key đã tồn tại và đang xử lý -> Trả về `409 Conflict` hoặc chờ.
  * Nếu key đã tồn tại và đã xong -> Trả về ngay kết quả lưu trong cache, không tính toán lại.
