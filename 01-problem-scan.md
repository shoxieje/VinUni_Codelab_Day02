## 🏛️ Bối cảnh: Tôi là ai?

Tôi là **Đỗ Minh Thanh**, AI Engineer tại **Vin Smart Future**. Nhóm chúng tôi được giao nhiệm vụ phối hợp với các công ty thành viên Vingroup để tìm kiếm những cơ hội tối ưu hóa vận hành bằng trí tuệ nhân tạo.

Thông qua khảo sát tại **Vinhomes, Vinmec, Vinpearl, Xanh SM và VinFast**, tôi nhận thấy nhiều quy trình vẫn phụ thuộc vào thao tác thủ công: cư dân phải đến Ban Quản lý làm thủ tục, bác sĩ phải tổng hợp thông tin bệnh án từ nhiều nguồn, nhân viên phải rà soát phản hồi khách hàng trên nhiều nền tảng, tài xế tự lựa chọn lịch sạc và chủ xe gặp khó khăn khi hiểu các cảnh báo kỹ thuật.

Những bất cập này làm tăng thời gian xử lý, gây áp lực cho đội ngũ vận hành và ảnh hưởng đến trải nghiệm khách hàng. Các bài toán tôi mang vào buổi Lab hôm nay xuất phát từ chính những quan sát thực tế đó.

---

# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội (Nhóm)

Dùng **4 Lenses** quét qua vận hành của các công ty thành viên Vingroup.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của nhóm:

| **#** | **Subsidiary** | **Lens** | **Mô tả ngắn bài toán** |
| --- | --- | --- | --- |
| 1 | **Vinhomes** | Lặp lại | Cư dân phải đến trực tiếp Ban Quản lý để đăng ký thi công nội thất, vé gửi xe tháng hoặc cấp thẻ cư dân. → **AI Chatbot hỗ trợ đăng ký và thực hiện thủ tục trực tuyến 24/7.** |
| 2 | **Vinhomes** | Tốn thời gian | Cư dân không biết cần chuẩn bị giấy tờ gì, dễ nộp thiếu hoặc sai hồ sơ, phải bổ sung nhiều lần. → **AI sử dụng RAG để tra cứu quy định, hướng dẫn chuẩn bị hồ sơ và tự động tạo biểu mẫu theo yêu cầu.** |
| 3 | **Vinmec** | Pain từ người khác | Khi lập bệnh án, nhân viên y tế phải tổng hợp lời kể của bệnh nhân và kết quả xét nghiệm từ nhiều phòng ban. → **AI hỗ trợ tổng hợp thông tin, tạo bản nháp bệnh án để bác sĩ kiểm tra và hoàn thiện.** |
| 4 | **Vinpearl** | Tốn thời gian | Phản hồi của khách hàng phân tán trên Booking.com, Agoda và Google Maps, khiến việc rà soát và phát hiện phàn nàn khẩn cấp mất nhiều thời gian. → **AI tổng hợp, phân loại và cảnh báo các phàn nàn cần xử lý sớm.** |
| 5 | **Xanh SM** | Tốn thời gian | Tài xế tự chọn trạm và giờ sạc theo cảm tính, khiến xe dồn về cùng trạm V-Green vào cuối ca hoặc giờ nghỉ trưa. Nhiều xe sạc vào giờ cao điểm điện, trong khi xe gần hết pin vẫn nhận cuốc xa. → **AI hỗ trợ điều phối trạm và thời điểm sạc dựa trên mức pin, nhu cầu vận hành và tình trạng trạm.** |
| 6 | **VinFast** | AI-upgrade | Khách hàng không hiểu mã lỗi hoặc cảnh báo trên xe, gặp khó khăn trong việc xác định tình trạng và cách xử lý. → **AI giải thích mã lỗi bằng ngôn ngữ dễ hiểu và hướng dẫn bước xử lý phù hợp theo tài liệu kỹ thuật.** |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

Chọn **top 3 bài toán từ danh sách SCAN**: **#2 (Vinhomes — Hướng dẫn hồ sơ)**, **#4 (Vinpearl — Xử lý phàn nàn đa nền tảng)**, **#5 (Xanh SM — Điều phối sạc pin)**.

### 🃏 Thẻ bài toán tiêu biểu: Card #4 — Vinpearl Tổng hợp và điều phối xử lý phàn nàn khách hàng

```text
┌──────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #4                                            │
│                                                                  │
│ Bài toán:                                                        │
│ Phàn nàn của khách hàng xuất hiện bằng nhiều ngôn ngữ trên       │
│ Booking.com, Agoda và Google Maps. Nhân viên phải kiểm tra       │
│ từng nền tảng, dịch nội dung, phân loại dịch vụ và chuyển        │
│ cho bộ phận phụ trách, dễ bỏ sót trường hợp khẩn cấp.            │
│                                                                  │
│ Công ty thành viên: [x] Vinpearl                                 │
│                                                                  │
│ Ai đang đau?                                                     │
│ - Khách hàng: Phàn nàn chưa được tiếp nhận và xử lý kịp thời.    │
│ - Nhân viên CSKH: Phải rà soát nhiều kênh và dịch thủ công.      │
│ - Bộ phận vận hành: Nhận thông tin chậm hoặc thiếu chi tiết.     │
│                                                                  │
│ Workflow thủ công hiện tại (5 bước):                             │
│ 1. Nhân viên kiểm tra review trên từng nền tảng.                 │
│ → 2. Đọc và dịch các phản hồi bằng tiếng nước ngoài.             │
│ → 3. Xác định dịch vụ bị phàn nàn và mức độ khẩn cấp.            │
│ → 4. Tổng hợp nội dung, chuyển cho bộ phận phụ trách.            │
│ → 5. Theo dõi tiến độ, nhắc xử lý và cập nhật kết quả.           │
│                                                                  │
│ Bước nào tốn thời gian/lỗi nhất?                                 │
│ Bước 1–4: Thông tin phân tán, nhiều ngôn ngữ, phải phân loại     │
│ và chuyển việc thủ công. Thời gian hiện tại cần đo khi khảo sát. │
│                                                                  │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                            │
│ - Bước 2: Nhận diện ngôn ngữ, dịch và tóm tắt phản hồi.          │
│ - Bước 3: Gắn nhãn dịch vụ, nhận diện mức độ khẩn cấp.           │
│ - Bước 4: Soạn nội dung phiếu xử lý cho bộ phận phụ trách.       │
│                                                                  │
│ Tự động hóa hỗ trợ:                                              │
│ - Bước 1: Bot theo dõi, tổng hợp review từ các kênh có           │
│   tích hợp được cấp quyền về một nơi.                            │
│ - Bước 4–5: Tạo phiếu xử lý, giao việc theo quy tắc,             │
│   nhắc hạn và chuyển cấp khi quá hạn.                            │
│                                                                  │
│ Đo thành công bằng gì? (Mục tiêu đề xuất)                        │
│ - Thời gian từ khi hệ thống tiếp nhận review đến khi tạo         │
│   phiếu xử lý: không quá 3 phút.                                 │
│ - Độ chính xác gắn nhãn dịch vụ: đạt ít nhất 90%.                │
│ - Phát hiện ít nhất 95% phàn nàn khẩn cấp trên tập đánh giá      │
│   đã được nhân viên gắn nhãn.                                    │
│                                                                  │
│ Quick Architecture:                                              │
│ [x] LLM: Dịch, tóm tắt, gắn nhãn và nhận diện khẩn cấp.          │
│ [x] Rule + Workflow: Tổng hợp dữ liệu, giao việc, nhắc hạn       │
│     và chuyển cấp.                                               │
│ [x] Human review: Kiểm tra trường hợp khẩn cấp hoặc AI           │
│     chưa đủ chắc chắn trước khi quyết định xử lý.                │
└──────────────────────────────────────────────────────────────────┘
```

### 🔎 Bốn bottleneck trọng tâm

| **Bottleneck** | **Hướng giải quyết** |
| --- | --- |
| **Nhiều ngôn ngữ** | AI nhận diện ngôn ngữ, dịch sang tiếng Việt và giữ bản gốc để đối chiếu. |
| **Đa nền tảng** | Bot theo dõi các kênh được tích hợp, tổng hợp phản hồi về một danh sách chung và loại bỏ bản trùng. |
| **Gắn nhãn dịch vụ** | AI phân loại phản hồi theo phòng ở, lễ tân, nhà hàng, vệ sinh, tiện ích… Một phản hồi có thể có nhiều nhãn. |
| **Phối hợp giữa các bộ phận** | Tự động tạo phiếu xử lý, giao đúng bộ phận, theo dõi trạng thái, nhắc hạn và chuyển cấp. |

### 🗳️ Quyết định lựa chọn của nhóm

Nhóm quyết định chọn bài toán **“Card #4 — Vinpearl Tổng hợp và điều phối xử lý phàn nàn khách hàng”** để thực hiện **Deep-Dive**.

**Lý do lựa chọn:** Bài toán có bốn bottleneck rõ ràng, kết nối từ tiếp nhận thông tin đến giao việc và theo dõi xử lý. AI có thể hỗ trợ trực tiếp các bước cần hiểu ngôn ngữ và nội dung, trong khi quy tắc nghiệp vụ đảm nhiệm giao việc và nhắc hạn. Nhóm có thể thử nghiệm trước trên một tập review đã thu thập để đo chất lượng dịch, gắn nhãn và phát hiện khẩn cấp.

**Lý do chưa chọn các thẻ khác:**

- **Card #2 — Vinhomes Hướng dẫn hồ sơ:** Cần tập hợp và chuẩn hóa quy định, biểu mẫu, phiên bản tài liệu theo từng khu đô thị trước khi xây dựng hệ thống RAG.
- **Card #5 — Xanh SM Điều phối sạc pin:** Cần dữ liệu mức pin, vị trí xe, tình trạng trạm và nhu cầu chuyến đi được cập nhật liên tục. Việc thử nghiệm phụ thuộc nhiều hơn vào tích hợp hệ thống vận hành.

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

