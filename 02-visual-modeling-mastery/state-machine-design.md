# Finite State Machine (FSM) Design Principles

Finite State Machine (FSM) là công cụ toán học tối thượng để BA mô tả chính xác vòng đời của các thực thể kinh doanh (Đơn hàng, Hợp đồng, Gói cước, Tài khoản).

---

## 1. Phân Tách Giai Đoạn Lỗi (Failure Stage Isolation)

Một lỗi rất phổ biến của BA non tay là gom tất cả các trường hợp thất bại vào một trạng thái duy nhất: `FAILED`. Điều này làm tê liệt đội ngũ phát triển vì họ không biết phải khôi phục hệ thống như thế nào.

### So sánh Naive FSM vs Senior FSM

#### ❌ Naive Approach (Ngây thơ):
`INITIATED` -> `PROCESSING` -> `FAILED` (Không rõ lỗi do thẻ hết tiền, mạng rớt hay server sập).

#### ✅ Senior Approach (Chuẩn mực):
Tách rời trạng thái lỗi theo stage chịu trách nhiệm:
1. `PAYMENT_PENDING`: Đang chờ xác nhận từ cổng thanh toán.
2. `PAYMENT_FAILED`: Thẻ bị từ chối / hết hạn $	o$ Khách hàng có thể đổi thẻ khác và thử lại.
3. `ACTIVATION_PENDING`: Đã trừ tiền thành công, đang cấp quyền tài khoản.
4. `ACTIVATION_FAILED`: Lỗi mạng nội bộ khi cấp quyền $	o$ Hệ thống tự động retry hoặc Admin can thiệp thủ công, **TUYỆT ĐỐI KHÔNG ĐƯỢC TRỪ TIỀN LẦN HAI**.
5. `APPLIED`: Hoàn tất chu trình.

---

## 2. Các Ràng Buộc Bất Biến (State Invariants)

1. **No Orphan States (Không có trạng thái mồ côi):** Mọi trạng thái (trừ End State) đều phải có ít nhất một transition hợp lệ đi ra ngoài.
2. **Terminal State Invariance:** Một khi thực thể đã rơi vào trạng thái kết thúc (`CANCELLED`, `CLOSED`, `EXPIRED`), không có bất kỳ event nào được phép hồi sinh lại thực thể đó. Phải tạo mới một thực thể khác.
3. **Idempotent Transitions:** Nếu một event kích hoạt lặp lại (ví dụ: webhook gửi 2 lần cùng một kết quả), FSM phải giữ nguyên trạng thái hiện tại và trả về phản hồi thành công, không được thực hiện lại hành động nghiệp vụ (no side-effects).
