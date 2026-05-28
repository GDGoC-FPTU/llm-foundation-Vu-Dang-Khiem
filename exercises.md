# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Các phản hồi thay đổi từ rất chặt chẽ và có tính xác thực cao ở temperature thấp sang sáng tạo và đa dạng hơn ở temperature cao. Ở `0.0` câu trả lời thường ngắn gọn, chuẩn xác và lặp lại; ở `0.5` có thêm chút biến thể; ở `1.0` nội dung sáng tạo, ngôn ngữ đa dạng hơn; ở `1.5` câu trả lời có thể dài, nhiều chi tiết tưởng tượng và đôi khi kém chính xác hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Em sẽ đặt temperature khoảng `0.0–0.3` (ví dụ `0.2`) để đảm bảo tính nhất quán và chính xác, giảm rủi ro thông tin sai lệch trong môi trường hỗ trợ khách hàng.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Giả sử 350 token chia đều thành ~175 token input và 175 token output mỗi cuộc gọi. Dựa trên bảng giá mẫu, chi phí trung bình mỗi cuộc gọi ~ $0.004375 cho GPT-4o và ~ $0.00013125 cho GPT-4o-mini. Với 30.000 cuộc gọi/ngày, GPT-4o ~ $131.25/ngày so với GPT-4o-mini ~ $3.94/ngày — tức GPT-4o đắt hơn khoảng **33 lần**.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> Xứng đáng: Ứng dụng y tế/luật hoặc hệ thống phân tích phức tạp cần độ chính xác và khả năng suy luận cao — chất lượng mô hình mạnh hơn có thể quyết định kết quả đúng/sai và mang lại giá trị lớn.  
> Chọn mini: Ứng dụng hỗ trợ khách hàng quy mô lớn (FAQ, phân loại, tóm tắt ngắn) nơi throughput và chi phí thấp quan trọng hơn, và chất lượng ngôn ngữ tiêu chuẩn là đủ.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi người dùng mong đợi phản hồi theo thời gian thực — ví dụ trợ lý giọng nói, trình soạn thảo giúp gợi ý khi gõ, hoặc chat tương tác dài nơi từng phần trả về cải thiện trải nghiệm và giảm độ trễ cảm nhận. Non-streaming phù hợp cho các tác vụ ngắn gọn hoặc batch (tổng hợp báo cáo, tóm tắt) nơi cần kết quả đầy đủ, nhất quán, hoặc khi hạ tầng/chi phí/độ phức tạp triển khai không cho phép streaming.


## Danh Sách Kiểm Tra Nộp Bài
- [ ] Tất cả tests pass: `pytest tests/ -v`
- [ ] `call_openai` đã triển khai và kiểm thử
- [ ] `call_openai_mini` đã triển khai và kiểm thử
- [ ] `compare_models` đã triển khai và kiểm thử
- [ ] `streaming_chatbot` đã triển khai và kiểm thử
- [ ] `retry_with_backoff` đã triển khai và kiểm thử
- [ ] `batch_compare` đã triển khai và kiểm thử
- [ ] `format_comparison_table` đã triển khai và kiểm thử
- [ ] `exercises.md` đã điền đầy đủ
- [ ] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
