# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

### 📝 List bài toán của tôi:
| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Vinpearl** | Lặp lại | Nhân viên CSKH phải trả lời lặp đi lặp lại các câu hỏi của khách về giá vé, giờ mở cửa, dịch vụ và quy định tại các khu vui chơi. |
| 2 | **Vinhomes** | Tốn thời gian | Nhân viên quản lý mất nhiều thời gian đối chiếu công nợ, phí dịch vụ, phí gửi xe và xác nhận thanh toán của cư dân. |
| 3 | **Vinmec** | Lặp lại | Nhân viên phải nhập và cập nhật thủ công thông tin bệnh nhân từ giấy tờ, biểu mẫu vào hệ thống quản lý bệnh viện, gây mất thời gian. |
| 4 | **VinFast** | AI có thể tốt hơn | Tự động đề xuất lịch trình sạc tối ưu và trạm sạc trống phù hợp với loại cổng sạc (CCS2/GBT) của từng dòng xe điện (VF5, VF8, VF9). |
| 5 | **Vinpearl** | Pain từ người khác | Quét qua các review trên Booking.com, Agoda, Google Map của Vinpearl để lọc ra các phàn nàn khẩn cấp (ví dụ: *"phòng bẩn"*, *"nhân viên thái độ tệ"*) gửi về Manager. |
---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card): 

## Thẻ bài toán: Card #1 — Xây dựng trợ lý CSKH tự động trả lời các câu hỏi thường gặp của khách hàng về giá vé, giờ mở cửa, dịch vụ và quy định tại các khu vui chơi Vinpearl. 

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Xây dựng trợ lý CSKH tự động trả lời các câu hỏi  | 
|thường gặp của khách hàng về giá vé, giờ mở cửa, dịch vụ và  |
|quy định tại các khu vui chơi Vinpearl.                      │
│                                                             │
│ Ai đang đau?  Nhân viên chăm sóc khách hàng (CSKH), Khách   |
|hàng cần tìm hiểu thông tin trước hoặc trong chuyến đi.      │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1.Khách hàng gửi câu hỏi qua website, hotline hoặc fanpage│
│   → 2. Nhân viên CSKH tiếp nhận và xác định nội dung cần hỗ trợ.│
│   → 3. Nhân viên tra cứu thông tin trong tài liệu, bảng giá hoặc hệ thống nội bộ   │
│   → 4. Nhân viên soạn câu trả lời và gửi lại khách hàng.    │
│                                                             │
│ Bước nào tốn nhất? Bước 3-4 (⏱ 5-10 phút/lượt)             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3-4              │
│ (Tự động hóa truy xuất thông tin từ kho dữ liệu chính thức   |
|của Vinpearl -> Draft tin nhắn trả lời cho khách)             │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian phản hồi từ 5–10 phút xuống dưới 1 phút/câu hỏi.|
| Tỷ lệ câu hỏi phổ biến được AI xử lý ≥ 70%.                  |
│                                                              │
│ Quick Architecture: [x] LLM Feature (Tự động soạn chỉ dẫn)   │
└───────────────────────────────────────────────────────────── ┘
```
## Thẻ bài toán: Card #2 — Xây dựng hệ thống hỗ trợ tự động đọc, tổng hợp và đối chiếu công nợ, phí dịch vụ, phí gửi xe với dữ liệu thanh toán của cư dân nhằm giảm thao tác kiểm tra thủ công và hạn chế sai sót.

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Xây dựng hệ thống hỗ trợ tự động đọc, tổng hợp và |
|đối chiếu công nợ, phí dịch vụ, phí gửi xe với dữ liệu thanh |
|toán của cư dân nhằm giảm thao tác kiểm tra thủ công và hạn chế sai sót.│
│                                                             │
│ Ai đang đau?  Nhân viên kế toán, Nhân viên quản lý vận hành,|
|Bộ phận phụ trách công nợ cư dân.                            │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1.Nhân viên thu thập dữ liệu phí dịch vụ, phí gửi xe và danh sách công nợ từ các hệ thống.│
│   → 2. Nhân viên kiểm tra sao kê hoặc dữ liệu thanh toán.│
│   → 3. Nhân viên đối chiếu số tiền, mã căn hộ, thông tin cư dân và kỳ thanh toán.   │
│   → 4. Nhân viên cập nhật trạng thái thanh toán, tổng hợp các giao dịch còn thiếu hoặc có sai lệch.   │
│                                                             │
│ Bước nào tốn nhất? Bước 3-4 (⏱ 12 phút/lượt)                │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3-4              │
│ (OCR trích xuất thông tin từ chứng từ/sao kê -> AI hỗ trợ nhận diện và chuẩn hóa mã căn hộ, nội dung chuyển khoản. |
|-> Rule Engine đối chiếu số tiền,|mã căn hộ, kỳ thanh toán và 
|khoản phí; các trường hợp sai lệch hoặc thiếu thông tin được chuyển cho nhân viên kiểm tra.)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian đối chiếu và nhập liệu từ 12 phút xuống còn 5 - 7 phút|
│                                                              │
│ Quick Architecture: [x] Rule + OCR                           │
└───────────────────────────────────────────────────────────── ┘
```

## Thẻ bài toán: Card #5 — Xây dựng hệ thống AI tự động phân tích review của khách hàng trên Booking.com, Agoda và Google Maps để phát hiện, phân loại các phàn nàn nghiêm trọng và gửi cảnh báo đến Manager phụ trách.

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #5                                       │
│                                                             │
│ Bài toán: Xây dựng hệ thống AI tự động phân tích review của |
|khách hàng trên Booking.com, Agoda và Google Maps để phát hiện,|
|phân loại các phàn nàn nghiêm trọng và gửi cảnh báo đến Manager phụ trách.|
│                                                             │
│ Ai đang đau?  Bộ phận chăm sóc khách hàng, Bộ phận quản lý chất lượng dịch vụ,|
|Manager các lĩnh vực trong khách sạn (vệ sinh, nhân sự, ...) │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Nhân viên truy cập các nền tảng Booking.com, Agoda và Google Maps để theo dõi review.│
│   → 2. Nhân viên đọc và tổng hợp nội dung phản hồi của khách hàng.│
│   → 3. Nhân viên phân loại phản hồi theo chủ đề, cảm xúc và mức độ nghiêm trọng.│
│   → 4. Nhân viên tổng hợp các vấn đề đáng chú ý và gửi báo cáo cho Manager các bên để xử lý.│
│                                                             │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 4 phút/lượt)                │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3              │
│ (LLM/NLP phân tích nội dung review, nhận diện cảm xúc và chủ đề như vệ sinh phòng, thái độ nhân viên, chất lượng đồ ăn, cơ sở vật chất.|
|-> Phân loại vấn đề -> Rule Engine đánh giá mức độ ưu tiên và gửi cảnh báo đến Manager khi phát hiện khiếu nại nghiêm trọng.)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian phân tích từ 4 phút xuống dưới 10-15 giây/review|
| Tỷ lệ review được phân loại tự động ≥ 90%.
│                                                              │
│ Quick Architecture: [x] LLM + Classification                 │
└───────────────────────────────────────────────────────────── ┘
```

---

# 🗳️ Quyết định lựa chọn:
Quyết định chọn bài toán **Card #5** — Xây dựng hệ thống AI tự động phân tích review của khách hàng trên Booking.com, Agoda và Google Maps để phát hiện, phân loại các phàn nàn nghiêm trọng và gửi cảnh báo đến Manager phụ trách.

## Lý do lựa chọn và loại bỏ các thẻ khác:

* **Card #5 (Vinpearl AI phân tích đánh giá khách hàng.):** Bài toán rõ ràng với dữ liệu đầu vào là các đánh giá của khách hàng, đầu ra là kết quả phân loại và cảnh báo. Có thể xây dựng quy trình từ thu thập dữ liệu, phân tích đánh giá đến gửi cảnh báo mà không cần thay đổi quá nhiều quy trình vận hành hiện tại. Có thể đánh giá bằng thời gian xử lý, độ chính xác phân loại và khả năng phát hiện phàn nàn nghiêm trọng.

* **Card #1 (Vinhomes CSKH):** Cần có nguồn dữ liệu chính thức, đầy đủ và thường xuyên cập nhật về giá vé, giờ mở cửa, dịch vụ và chính sách. Nếu dữ liệu không được cập nhật kịp thời, AI có thể cung cấp thông tin sai lệch cho khách hàng.

* **Card #2 (Vinhomes Tự động đối soát công nợ cư dân):** Cần quyền truy cập vào dữ liệu tài chính, thông tin cư dân và các hệ thống nội bộ. Việc đối soát yêu cầu độ chính xác cao, sai sót có thể ảnh hưởng trực tiếp đến dữ liệu thanh toán. AI chỉ nên hỗ trợ trích xuất và chuẩn hóa dữ liệu; việc đối chiếu cần dựa trên Rule Engine để đảm bảo tính chính xác.
---