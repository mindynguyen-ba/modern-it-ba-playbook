# AI Opportunity Assessment Framework

Khi làn sóng AI bùng nổ, 90% dự án thất bại vì cố gắng "nhồi nhét AI" vào những bài toán chỉ cần giải bằng một câu lệnh SQL hoặc một bảng Decision Table đơn giản.

---

## 1. Ma Trận Đánh Giá: AI vs Deterministic Logic

| Tiêu chí | Dùng Logic Truyền Thống (Rule/SQL) | Dùng AI / Machine Learning / LLM |
|---|---|---|
| **Độ chính xác yêu cầu** | 100% chính xác tuyệt đối (Tài chính, Tính cước, Phân quyền) | Chấp nhận tính xác suất (Gợi ý, Tóm tắt, Phân loại) |
| **Bản chất dữ liệu** | Dữ liệu có cấu trúc (Bảng, Số, Khóa ngoại) | Dữ liệu phi cấu trúc (Văn bản, Hình ảnh, Giọng nói) |
| **Tính giải trình (Auditability)** | Phải giải trình được từng bước (Audit log rõ ràng) | Hộp đen (Black-box), khó diễn giải nguyên nhân từng token |
| **Chi phí vận hành** | Rất thấp (CPU, Memory tiêu chuẩn) | Cao (GPU, Token API, Chi phí Finetuning/Vector DB) |
| **Độ trễ (Latency)** | < 50ms | 500ms - 5000ms |

---

## 2. Công Thức Đánh Giá AI ROI & Risk

$$	ext{AI Net Value} = (	ext{Cost Saved} + 	ext{Value Created}) - (	ext{Token Cost} + 	ext{Human-in-the-loop Review} + 	ext{Hallucination Liability})$$

* **Hallucination Risk (Rủi ro ảo giác):** Nếu AI trả lời sai, thiệt hại kinh tế hoặc pháp lý là bao nhiêu?
* **Human-in-the-loop:** Có cần con người duyệt lại kết quả trước khi áp dụng không? Nếu có, chi phí nhân sự duyệt có triệt tiêu lợi ích của AI không?
