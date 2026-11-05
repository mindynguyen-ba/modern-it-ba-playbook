# Decision Table Template (Bảng Quyết Định Logic)

Decision Table là công cụ bắt buộc khi một tính năng có từ 2 điều kiện nghiệp vụ trở lên giao thoa với nhau.

---

## Cấu Trúc Bảng Chuẩn

| Mã Điều Kiện / Hành Động | Tên Điều Kiện / Hành Động | R01 | R02 | R03 | R04 |
|---|---|---|---|---|---|
| **C01 (Condition)** | Trạng thái tài khoản = ACTIVE | Y | Y | N | N |
| **C02 (Condition)** | Số dư nợ > 0 | N | Y | N | Y |
| **A01 (Action)** | Cho phép nâng cấp gói cước ngay | **X** | - | - | - |
| **A02 (Action)** | Chuyển hướng sang trang trả nợ cước | - | **X** | - | **X** |
| **A03 (Action)** | Hiển thị thông báo tài khoản bị khóa | - | - | **X** | - |

---

## Quy Tắc Kiểm Tra Tính Toàn Vẹn:
1. Số lượng cột quy tắc (Rules) tối thiểu phải bằng $2^n$ (với $n$ là số điều kiện nhị phân Y/N).
2. Không có hai cột nào có cùng tập hợp điều kiện nhưng hành động khác nhau (tránh Contradiction).
3. Mọi cột đều phải có ít nhất một hành động được đánh dấu (tránh Incompleteness).
