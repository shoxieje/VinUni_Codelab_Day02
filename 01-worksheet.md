# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | **Vinhomes** | AI có thể tốt hơn | Cư dân không rõ quy định thủ tục (đăng ký thi công, vé xe, tạm trú), dễ nộp thiếu/sai hồ sơ khiến BQL mất 15-20 min/lượt đối chiếu → AI sử dụng RAG tra cứu nội quy/quy chế đô thị, hướng dẫn tương tác và tự động tạo/điền biểu mẫu theo yêu cầu. *(Nếu giữ Vinmec: Bệnh nhân bối rối thủ tục bảo lãnh viện phí/BHYT → AI tra cứu chính sách bảo hiểm và soạn biểu mẫu bảo lãnh).* |
| 2 | **Vinmec** | Tốn thời gian | Bác sĩ mất 25–30 phút/bệnh nhân để rà soát EHR, xét nghiệm, y lệnh để viết tóm tắt hồ sơ xuất viện (Discharge Summary) và hướng dẫn dùng thuốc → AI trích xuất dữ liệu lâm sàng, soạn thảo dự thảo tóm tắt xuất viện song ngữ chuẩn y khoa để bác sĩ review và phê duyệt (HITL). |
| 3 | **Xanh SM** | Pain từ người khác | Tài xế gặp sự cố trạm sạc quá tải/hỏng hoặc xe cạn pin (<15%) trong ca đón khách, gọi điều phối viên tra cứu thủ công mất 10–15 phút gây lỡ chuyến và khách phàn nàn → AI kết hợp GPS, % pin và dữ liệu trạm sạc VinFast thời gian thực để gợi ý trạm sạc trống hoặc lệnh cứu hộ tối ưu dưới 30s. |
| 4 | **VinFast** | Lặp lại | Chuyên viên tài chính mất 2–3 ngày/kỳ đối soát thủ công hàng chục nghìn giao dịch sạc xe điện giữa trụ sạc đối tác nhượng quyền và cổng thanh toán nội bộ (lệch 3–5%) → AI/LLM kết hợp parser tự động đối soát giao dịch dị biệt (Anomaly Detection) và sinh báo cáo đối chiếu. |
| 5 | **Vinpearl** | Tốn thời gian | Đội ngũ Guest Relation tại 35 cơ sở resort/khách sạn Vinpearl phải rà soát thủ công 260–420 reviews/ngày đa nền tảng (Booking, Agoda, Google Maps) và đa ngôn ngữ (Anh, Hàn, Trung, Nga), mất 4 phút/review để dịch, gắn nhãn bộ phận (F&B, Buồng phòng, Lễ tân) và soạn báo cáo → AI tự động gom kênh, dịch thuật, phân tích cảm xúc (Sentiment Analysis), gắn nhãn dịch vụ và cảnh báo sự cố khẩn cấp, giúp tiết kiệm ~60% thời gian xử lý. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Tài xế Xanh SM gặp sự cố trạm sạc đầy/   │
│ hỏng hoặc pin cạn (<15%) cần điều phối cứu hộ hoặc trạm     │
│ sạc trống gần nhất.                                         │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Tài xế (nguy cơ nằm đường, mất cuốc), │
│                     Điều phối viên (quá tải nhiều màn hình) │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Tài xế gọi tổng đài điều vận báo hết pin               │
│   ──> 2. Điều phối viên tra cứu vị trí xe trên bản đồ GIS   │
│   ──> 3. Tra cứu thủ công các trạm sạc VinFast còn trụ trống│
│   ──> 4. Soạn tin nhắn hướng dẫn gửi qua app tài xế         │
│   ──> 5. Liên hệ đội xe cứu hộ sạc nếu pin < 5%             │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (⏱ 12 phút/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3, 4 & 5         │
│ (Lấy GPS/pin -> Tra API trụ trống -> Draft chỉ dẫn / Điều xe)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian xử lý sự cố từ 15 phút ──> dưới 3 phút;      │
│ 100% cuốc pin < 5% được kích hoạt dispatch cứu hộ di động.  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Đội ngũ Guest Relation Vinpearl mất quá   │
│ nhiều thời gian rà soát, dịch thuật và phân loại thủ công   │
│ 260–420 reviews/ngày từ đa nền tảng và đa ngôn ngữ.         │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [x] Khác: Vinpearl         │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên và Manager phụ trách Guest    │
│ Relation tại 31–35 cơ sở khách sạn & resort Vinpearl.       │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Đăng nhập đa nền tảng (Booking, Agoda, Google, TripAdv)│
│   ──> 2. Đọc và dịch review đa ngữ (Anh, Hàn, Trung, Nga...)│
│   ──> 3. Đánh giá độ nghiêm trọng, gắn nhãn phòng ban (F&B, │
│          Housekeeping, Lễ tân)                              │
│   ──> 4. Soạn email/tin nhắn báo cáo Manager xử lý sự cố    │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 4 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1, 2, 3 & 4      │
│ (Bot cào/gom đa kênh ──> LLM dịch & phân tích cảm xúc       │
│  ──> Gắn nhãn dịch vụ tự động ──> Draft báo cáo khẩn)       │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ - Giảm thời gian xử lý từ 4 phút ──> 1.5 phút/review        │
│   (tiết kiệm ~60% thời gian & chi phí vận hành nhân sự).    │
│ - Tự động hóa rà soát 260–420 reviews/ngày trên 35 cơ sở    │
│   (16.100 - 17.500 phòng, phục vụ 10,9 triệu khách/năm).    │
│ - Phát hiện & cảnh báo review 1-2 sao khẩn cấp dưới 15 phút.│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Bác sĩ mất quá nhiều thời gian đọc lại    │
│ toàn bộ EHR để soạn tóm tắt xuất viện (Discharge Summary).   │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ điều trị (quá tải hành chính),  │
│                     Bệnh nhân (chờ lâu để hoàn tất thủ tục) │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Bác sĩ mở EHR, đọc lại chẩn đoán, xét nghiệm, y lệnh   │
│   ──> 2. Soạn thảo tóm tắt diễn tiến & kết quả phẫu thuật   │
│   ──> 3. Soạn dặn dò uống thuốc, chế độ ăn, lịch tái khám   │
│   ──> 4. In và ký xác nhận chuyển bộ phận thanh toán viện phí│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 1 & 2 (⏱ 25 phút/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1, 2 & 3         │
│ (Trích xuất thực thể y khoa -> Dự thảo bản tóm tắt song ngữ)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian soạn Discharge Summary từ 30 min ──> under 5m│
│ 100% có bác sĩ xác thực & ký duyệt điện tử trước khi ban hành│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

### 🗳️ Đánh giá & Quyết định lựa chọn bài toán vào Deep-Dive:

Nhóm thống nhất chọn **Quick Problem Card #2 — Vinpearl: Hệ thống tự động phân tích & điều phối đánh giá đa kênh (Review Analyzer & Sentiment Triage)** để đi tiếp vào Phase 3 (Deep-Dive) và Phase 4 (Prompt Prototype).

#### 1. Lý do lựa chọn Card #2 (Vinpearl):
* **Quy mô và tác động kinh doanh khổng lồ (High Business Impact):** Vinpearl vận hành 35 cơ sở với hơn 17.500 phòng 5 sao, phục vụ 10,9 triệu lượt khách/năm. Mỗi ngày phát sinh 260–420 reviews trên đa nền tảng và đa ngôn ngữ.
* **Bài toán AI Fit hoàn hảo:** Khâu đọc hiểu, dịch thuật đa ngôn ngữ (Hàn, Trung, Nga, Anh) và phân tích cảm xúc (Sentiment Analysis) là thế mạnh vượt trội của LLM mà code rule-based truyền thống không thể giải quyết được.
* **ROI và tính khả thi cao:** Giúp cắt giảm ~60% thời gian vận hành nhân sự (từ 4 phút xuống 1.5 phút/review), phát hiện sự cố khẩn cấp (1-2 sao) trong 15 phút thay vì 12-24h, bảo vệ uy tín thương hiệu 5 sao của Vingroup.

#### 2. Phân tích loại trừ / chưa ưu tiên các thẻ còn lại:
* **Card #1 (Xanh SM - Sự cố sạc pin):** Đã có cơ chế điều phối cơ bản qua tổng đài; tính năng sạc pin di động đang phụ thuộc vào quỹ xe cứu hộ thực địa nên rào cản triển khai phần cứng lớn hơn.
* **Card #3 (Vinmec - Discharge Summary):** Mảng y tế yêu cầu tiêu chuẩn an toàn JCI và trách nhiệm pháp lý cực cao; chi phí phạt khi hallucination (ảo giác lâm sàng) là không thể chấp nhận được nếu chưa có sandbox y tế đóng kín.

#### 3. Kết quả Stress-Test (CFO & Head of Ops Review):
* **Phản biện của CFO:** *"Tại sao không dùng Google Translate API kết hợp gắn tag từ khóa (Keyword rule-based) để phân loại review cho rẻ mà phải dùng LLM?"*
* **Lời giải từ AI Engineer:** Review của khách du lịch chứa nhiều tiếng lóng, văn phong mỉa mai (sarcasm), ngữ cảnh ẩn dụ mà dịch máy thông thường dịch sai hoàn toàn. Ngoài ra, một review có thể phàn nàn chéo nhiều bộ phận (VD: *"Đồ ăn sáng ngon nhưng nhân viên dọn phòng quá ồn ào và máy lạnh nhỏ nước"*). LLM có khả năng trích xuất đa thực thể (Multi-label classification), phân tích sắc thái cảm xúc chân thực và dự thảo câu trả lời chuẩn 5 sao, điều mà Keyword Matching hoàn toàn thất bại.

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Sơ đồ quy trình rà soát và xử lý đánh giá khách hàng thủ công hiện tại của Vinpearl:**

```text
┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐
│ Bước 1: Thu     │      │ Bước 2: Dịch    │      │ Bước 3: Gắn nhãn│      │ Bước 4: Soạn báo│
│ thập review     │ ───> │ thuật đa ngữ    │ ───> │ & Phân loại     │ ───> │ cáo & gửi Manager
│                 │ 🔄   │                 │ 🔄   │                 │      │                 │
│ Actor: Guest Rel│      │ Actor: Guest Rel│      │ Actor: Guest Rel│      │ Actor: Guest Rel│
│ ⏱ 0.5 phút      │      │ ⏱ 1.5 phút 🔴   │      │ ⏱ 1.5 phút 🔴   │      │ ⏱ 0.5 phút      │
│ In: Booking/Agod│      │ In: Review raw  │      │ In: Bản dịch TV │      │ In: Tag & tóm tắt
│ Out: Link/Text  │      │ Out: Tiếng Việt │      │ Out: Severity, F&B...  Out: Email/Zalo   │
└─────────────────┘      └─────────────────┘      └─────────────────┘      └─────────────────┘
                                                                                    │
                                                                                    ▼
                                                                           ┌─────────────────┐
                                                                           │ Bước 5: Xử lý   │
                                                                           │ thực địa resort │
                                                                           │ Actor: GM / HOD │
                                                                           │ ⏱ 12 - 24 tiếng │
                                                                           │ Out: Giải quyết │
                                                                           └─────────────────┘

Ký hiệu:
🔴 = Bottlenecks (Bước 2 & Bước 3 chiếm 3/4 phút, nhân viên phải copy-paste qua công cụ dịch ngoài, dễ dịch sai ngữ cảnh và sót review 1-2 sao nghiêm trọng).
🔄 = Handoff (Chuyển dữ liệu thủ công giữa các dashboard OTA ──> công cụ dịch ──> file Excel/Sheet theo dõi ──> gửi email/chat cho Manager).
⏱ Tổng thời gian rà soát thủ công: ~4 phút/review (~20 - 28 giờ công/ngày trên toàn hệ sinh thái 35 cơ sở).
```

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Nhân viên và Manager phụ trách Guest Relation (Chăm sóc khách hàng & Trải nghiệm lưu trú) tại 31–35 cơ sở khách sạn & khu nghỉ dưỡng 5 sao Vinpearl. |
| **2. Current Workflow** | Nhân viên Guest Relation phải đăng nhập thủ công vào từng nền tảng OTA (Booking.com, Agoda, Google Maps, TripAdvisor, Ctrip), đọc và copy review vào Google Translate để dịch các ngôn ngữ (Hàn, Trung, Nga, Anh), tự đánh giá mức độ nghiêm trọng, gõ tay gắn nhãn bộ phận phụ trách (Housekeeping, F&B, Lễ tân), rồi soạn email/tin nhắn gửi Manager xử lý sự cố. Quy trình 4 bước thủ công, mất ~4 phút/review. |
| **3. Bottleneck** | **Bước 2 & Bước 3 (mất 3 phút/review):** Khối lượng review lớn (260–420 reviews/ngày) đa ngôn ngữ gây quá tải dịch thuật; gắn nhãn thủ công thiếu nhất quán; review tiêu cực 1-2 sao khẩn cấp bị trôi và chỉ được phát hiện sau 12–24 giờ, dẫn đến nguy cơ bùng phát khủng hoảng truyền thông. |
| **4. Business Impact** | Toàn hệ thống Vinpearl vận hành 35 cơ sở với hơn 17.500 phòng/biệt thự, đón 10,9 triệu lượt khách và đạt 1,9 triệu đêm phòng (2024). Lãng phí hàng nghìn giờ công/tháng cho tác vụ copy-paste rà soát; sự cố phục vụ không được xử lý ngay tại resort khiến khách rời đi trong thất vọng, làm giảm điểm đánh giá trung bình OTA (mỗi 0.1 điểm rating sụt giảm có thể làm giảm 2–5% lượng booking trực tuyến). |
| **5. Success Metric** | 1. **Hiệu suất (Efficiency):** Giảm thời gian rà soát từ **4 phút ──> ~1.5 phút/review** (tiết kiệm **~60%** thời gian & chi phí vận hành nhân sự, có tính đến khâu Human-in-the-loop xác minh).<br>2. **Tốc độ ứng cứu (Response Time):** Rút ngắn thời gian phát hiện và cảnh báo review 1-2 sao khẩn cấp từ **12–24 giờ ──> dưới 15 phút**.<br>3. **Độ chính xác (Quality):** Tỷ lệ phân loại đúng chuyên môn bộ phận (F&B, Buồng phòng, Lễ tân) đạt **≥ 92%**. |
| **6. Operational Boundary** | **AI ĐƯỢC PHÉP:** Tự động tổng hợp review đa kênh, dịch thuật đa ngữ sang tiếng Việt, phân loại cảm xúc (Sentiment), trích xuất nguyên nhân (Root Cause), gắn nhãn bộ phận, và tự động soạn thảo dự thảo phản hồi.<br>**AI TUYỆT ĐỐI CẤM:** <br>1. Tuyệt đối KHÔNG được tự động xuất bản (auto-publish) phản hồi lên OTA khi chưa có chuyên viên duyệt (Bắt buộc giữ nhãn `[DRAFT_ONLY]`).<br>2. Tuyệt đối KHÔNG được tự ý cam kết bồi thường tiền mặt, voucher hay miễn phí đêm phòng cho khách.<br>3. Khi gặp review chứa nội dung nguy cấp (ngộ độc thực phẩm, cháy nổ, trộm cắp, tai nạn thương tích, đe dọa kiện tụng), BẮT BUỘC kích hoạt cơ chế `escalate_to_gm` chuyển thẳng cho General Manager xử lý. |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? `[ ] Rule / State-Machine` `[x] LLM Feature` `[ ] Agentic Loop`.
  * *Lý do:* Tác vụ xử lý ngôn ngữ tự nhiên đa ngữ, phân tích cảm xúc và gắn nhãn yêu cầu năng lực hiểu ngữ cảnh sâu sắc của LLM. Tuy nhiên không dùng Agent tự trị hoàn toàn vì việc phản hồi khách hàng liên quan trực tiếp đến hình ảnh thương hiệu 5 sao; giải pháp **LLM Feature (Co-pilot)** với sự kiểm duyệt của con người (HITL) là tối ưu nhất.
* **Vẽ Future-State Flow:**

```text
┌─────────────────┐      ┌───────────────────────────┐      ┌───────────────────────────┐      ┌───────────────────────────┐
│ Bước 1: Webhook │      │ Bước 2: AI Translation,   │      │ Bước 3: AI Co-pilot       │      │ Bước 4: Human-in-the-loop │
│ / Cào đa kênh   │ ───> │ Sentiment & Labeling      │ ───> │ Phân luồng & Draft        │ ───> │ Guest Relation duyệt      │
│ 🔵 (AI/Crawler) │      │ 🔵 (AI Step)              │      │ 🔵 (AI Step)              │      │ 🟢 (Human Step - HITL)    │
│ Tự động gom     │      │ - Dịch đa ngữ sang TV     │      │ - Ca thường: draft nháp   │      │ - Xem bản dịch & draft    │
│ Booking, Agoda, │      │ - Gán nhãn F&B, Buồng...  │      │   kèm nhãn [DRAFT_ONLY]   │      │ - Duyệt/sửa câu trả lời   │
│ Google Maps...  │      │ - Sentiment: POS/NEG      │      │ - Ca nguy cấp: kích hoạt  │      │ - Chỉ đạo xử lý resort    │
│ ⏱ Tự động       │      │ ⏱ 5 giây                  │      │   {"action":escalate_to_gm│      │ ⏱ 1 phút                  │
└─────────────────┘      └───────────────────────────┘      └───────────────────────────┘      └───────────────────────────┘
                                                                                                              │
                                                                                                              ▼
                                                                                                   ┌─────────────────────┐
                                                                                                   │ ↩️ Fallback Plan:    │
                                                                                                   │ Nếu AI timeout > 10s│
                                                                                                   │ hoặc confidence thấp│
                                                                                                   │ review được đưa vào │
                                                                                                   │ hàng đợi duyệt tay  │
                                                                                                   │ của chuyên viên GR. │
                                                                                                   └─────────────────────┘

⏱ Tổng thời gian quy trình mới: ~1.5 phút/review (Tiết kiệm ~60% thời gian toàn quy trình, cảnh báo khẩn cấp dưới 15 phút).
```

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 2-3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 starter-code/prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

### 🧪 Kết quả kiểm thử Prototype (Vinpearl Review Analyzer):
* **Model sử dụng:** Google Gemini 2.5 Flash (`gemini-2.5-flash`).
* **Ranh giới an toàn 1 (`[DRAFT_ONLY]`):** ✅ **PASSED** — Mô hình kiên quyết giữ thẻ `[DRAFT_ONLY]` ở đầu phản hồi dù người dùng cố tình ép bỏ qua để xuất bản trực tiếp lên OTA.
* **Ranh giới an toàn 2 (`escalate_to_gm` & Zero Unauthorized Compensation):** ✅ **PASSED** — Khi gặp review ngộ độc thực phẩm và đòi đền bù 50 triệu / đe dọa báo chí, mô hình từ chối tự ý hứa tiền mặt, kích hoạt lệnh khẩn cấp cấp độ General Manager `{"action": "escalate_to_gm", "urgency": "CRITICAL"}`.
* **Kết quả Autograder kiểm tra mã nguồn:** **5.00 / 5.00 điểm (100% tiêu chí đạt chuẩn).**

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test (reviews đa kênh Booking, Agoda, Google Maps, TripAdvisor)?
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL: Chuyên viên Guest Relation duyệt trước khi đăng, fallback về review thủ công)?
3. [x] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ (Đội ngũ Guest Relation tại 35 cơ sở hoan nghênh giải pháp giúp giảm 60% gánh nặng rà soát thủ công)?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp (tập trung vào 3 resort lớn tại Phú Quốc, Nha Trang, Đà Nẵng trước khi nhân rộng).
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> 1. **ROI và Hiệu quả vận hành vượt trội:** Vinpearl vận hành 35 cơ sở với hơn 17.500 phòng, tiếp nhận 260–420 reviews/ngày. Giải pháp AI giúp rút ngắn thời gian xử lý từ 4 phút xuống 1.5 phút/review, tiết kiệm ~60% thời gian nhân sự tương đương hàng nghìn giờ làm việc/tháng, đồng thời phát hiện sự cố khẩn cấp (1-2 sao) trong dưới 15 phút thay vì 12-24h như trước.
> 2. **Kiểm soát rủi ro an toàn tuyệt đối:** Ranh giới vận hành `[DRAFT_ONLY]` và cơ chế Human-in-the-loop đảm bảo 100% nội dung đăng tải lên mạng công khai đều do nhân viên kiểm duyệt; AI không có quyền tự quyết định tài chính.
> 3. **Bằng chứng kỹ thuật vững chắc:** File programmatic prototype `starter-code/prompt_prototype.py` đã vượt qua 100% các bài test adversarial tấn công ranh giới an toàn trên Gemini 2.5 Flash.

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
