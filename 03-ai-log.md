# 📄 03-ai-log.md — Nhật ký tương tác AI

> **Dự án:** Tự động hóa theo dõi, phân loại và cảnh báo review khách hàng của Vinpearl
> **Công cụ AI sử dụng:** Claude, ChatGPT, Gemini, NotebookLM *
> **Giai đoạn:** Phase 1 (SCAN), Phase 3 (Deep-Dive) và Phase 5 (Evaluate)

---

## 1. Tổng quan: tôi dùng AI như thế nào

Trong dự án này, tôi dùng AI như một công cụ hỗ trợ tìm kiếm và tổng hợp thông tin. Nhóm tự quyết định bài toán, số liệu giả định dựa trên số liệu thống kê công khai (nhớ NotebookLM research) và ranh giới vận hành. AI giúp tôi đặt câu hỏi phản biện, kiểm tra tính nhất quán giữa các phần của báo cáo và gợi ý cách diễn đạt rõ hơn.

Quy trình làm việc của tôi gồm ba vòng:
1. Tôi đưa bối cảnh và bản nháp cho AI.
2. AI đề xuất hoặc phản biện.
3. Tôi kiểm chứng lại, rồi lựa chọn giữ, sửa hoặc bỏ đề xuất đó.

---
## 2. AI đã giúp tôi những gì

- AI hỗ trợ tìm hiểu doanh nghiệp và hoàn thiện Phase 1 (SCAN): Ban đầu, tôi chưa nắm rõ hoạt động vận hành và các sản phẩm, dịch vụ của từng công ty thành viên Vingroup. Tôi sử dụng ChatGPT, Gemini, Claude để tìm hiểu mô hình kinh doanh, quy trình vận hành của Vinpearl, Vinhomes, Vinmec, VinFast và Xanh SM, từ đó xác định các công việc có tính chất lặp lại, tốn thời gian hoặc có thể ứng dụng AI cải thiện. AI cũng giúp tôi phân tích các vấn đề dưới góc nhìn 4 Lens và gợi ý những bottleneck tiềm năng. 

- Làm rõ Current-State Workflow (mục 3.1): Ban đầu nhóm chỉ mô tả quy trình là "nhân viên đọc review rồi tổng hợp, phân loại thành báo cáo". AI gợi ý tách thành 4 bước, mỗi bước có đủ các trường *Ai / Thời gian / Input / Output*. Nhờ vậy nhóm nhìn ra bước 2 và 3 (tổng cộng 2 phút 30 giây trên 4 phút) mới là điểm nghẽn, thay vì cảm tính cho rằng "cả quy trình đều chậm".

- Viết Problem Statement 6 trường (mục 3.2): AI giúp tôi phân biệt *Bottleneck* (điểm nghẽn trong quy trình) với *Business Impact* (ảnh hưởng đến doanh nghiệp). 

- Chuẩn bị cho Phase 5 (Evaluate): AI giúp tôi nhìn từng mục trong AI Readiness Checklist qua câu hỏi: *"Nếu AI sai thì ai phát hiện và phát hiện bằng cách nào?"* Câu hỏi này dẫn đến cơ chế **Fallback** và **HITL** trong luồng tương lai.

---
## 3. AI đã trả lời sai / hallucination ở đâu và cách tôi xử lý
### Tình huống 1 - AI bịa số liệu để "làm đẹp" Success Metric
- **Hiện tượng:** Khi tôi nhờ viết Success Metric, AI đưa ra những con số nghe rất thuyết phục, ví dụ "độ chính xác phân loại 95%" hoặc "giảm 80% chi phí nhân sự", kèm giọng điệu như đó là kết quả đã được chứng minh.
- **Vấn đề:** Nhóm chưa có dữ liệu thật hay baseline nào. Những con số này không có nguồn và thực chất là hallucination.
- **Cách tôi xử lý:** Tôi hỏi lại "con số này dựa trên nguồn nào?" và AI thừa nhận đó chỉ là ví dụ minh họa. Nhóm chỉ giữ mục tiêu có thể kiểm chứng và ghi rõ mốc **4 phút/review là giả định ban đầu**. 


### Tình huống 2 - AI đề xuất vượt ranh giới vận hành
- **Hiện tượng:** AI gợi ý hệ thống nên *tự động phản hồi review công khai* trên Booking.com, Agoda, Google Maps để tăng tốc độ xử lý.
- **Vấn đề:** Phản hồi công khai sai có thể gây khủng hoảng truyền thông. Việc quy trách nhiệm cho nhân viên là nhạy cảm và có thể dẫn đến sai sót trong quản trị nhân sự.
- **Cách tôi xử lý:** Tôi viết lại **Operational Boundary** theo hướng nêu rõ AI được làm gì (phân tích, phân loại, đánh giá mức độ nghiêm trọng, tạo cảnh báo, tổng hợp báo cáo) và **không được làm gì** (tự phản hồi công khai, kết luận trách nhiệm cá nhân, đề xuất kỷ luật). 

### Tình huống 3 - AI nghiêng về giải pháp phức tạp hơn là giải pháp phù hợp
- **Hiện tượng:** Câu trả lời đầu tiên của AI đề xuất xây dựng một AI Agent tự động thực hiện tất cả công việc.
- **Vấn đề:** Quy trình của Vinpearl có các bước cố định và rủi ro cao nếu AI tự quyết. Agent làm tăng chi phí và khó kiểm soát, nên không cần thiết ở giai đoạn này.
- **Cách tôi xử lý:** Tôi đưa thêm ràng buộc vào prompt (*"quy trình cố định, ưu tiên kiểm soát và giảm chi phí"*) và yêu cầu AI so sánh ưu/nhược điểm của từng lựa chọn. 

