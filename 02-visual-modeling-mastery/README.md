# Visual Modeling Mastery — Joy Beatty's Domain

> *"If you can't draw it, you don't understand it."*  
> Mô hình hóa trực quan không phải là vẽ tranh minh họa, mà là phương tiện toán học hóa và cấu trúc hóa logic nghiệp vụ.

---

## 📑 Tài liệu trong chuyên mục

1. [`bpmn-2.0-collaboration-guide.md`](bpmn-2.0-collaboration-guide.md): Quy chuẩn vẽ BPMN 2.0 Collaboration chuyên nghiệp (Pool vs Lane, Message Flows, Event-based Gateways, Timers).
2. [`state-machine-design.md`](state-machine-design.md): Nguyên tắc thiết kế Finite State Machines (FSM), cô lập giai đoạn lỗi, chống mồ côi trạng thái.
3. [`integration-and-sequence-flows.md`](integration-and-sequence-flows.md): Đặc tả Sequence Diagrams, tương tác đồng bộ vs bất đồng bộ, ranh giới bên thứ 3 và vòng lặp Idempotency.

---

## 🎯 3 Nguyên Tắc Cốt Lõi Của Visual Modeling

1. **Ranh giới hệ thống là bất khả xâm phạm:** Không có mũi tên điều khiển (Sequence Flow) nào được phép bắn xuyên qua ranh giới của hai hệ thống độc lập. Mọi giao tiếp liên hệ thống bắt buộc phải là luồng tin nhắn (Message Flow).
2. **Không có trạng thái generic mập mờ:** Loại bỏ hoàn toàn các trạng thái kiểu `Failed` hay `Processing`. Trạng thái phải phản ánh chính xác trách nhiệm của thực thể (`PAYMENT_PENDING`, `ACTIVATION_FAILED`, `ACCESS_RESTRICTED`).
3. **Bịt kín các nhánh ngoại lệ:** Mọi cổng rẽ nhánh (Gateway) đều phải có đường thoát; mọi lời gọi bất đồng bộ đều phải có cơ chế Timeout hoặc Fallback.
