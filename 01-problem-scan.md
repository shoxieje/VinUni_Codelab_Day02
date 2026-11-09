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
| 1 | Xanh SM | Stakeholder Pain | **Điều phối sạc pin:** Tài xế tự chọn trạm V-Green theo cảm tính → dồn trạm giờ cao điểm, xếp hàng chờ ~20 phút/xe/ngày (ước tính ~3.300 giờ xe/ngày mất doanh thu với đội 10.000 xe); xe pin thấp vẫn nhận cuốc xa. |
| 2 | Xanh SM | Repetitive | **Tái phân bổ xe / giảm chạy rỗng:** Điều phối viên điều xe về sân bay, khu sự kiện theo kinh nghiệm → tỷ lệ km rỗng ~35% (ước tính), khách giờ cao điểm báo "không có xe". |
| 3 | Xanh SM | Repetitive | **Kiểm tra xe khi giao ca:** Tài xế chụp ảnh, nhân viên bãi soi bằng mắt 5–10 phút/lượt × 2 lượt/xe/ngày; bỏ sót vết xước nhỏ → không truy được ca gây hư hỏng, phát sinh tranh chấp. |
| 4 | Xanh SM | Time-consuming | **Hồ sơ va chạm & bồi thường bảo hiểm:** Ảnh hiện trường, biên bản, báo giá gara chuyển qua email/Zalo thủ công → xe nằm xưởng chờ duyệt 4–7 ngày (ước tính ~1.000 ngày xe/tháng), khó phát hiện báo giá bị đội lên. |
| 5 | Xanh SM | AI-upgrade | **CSKH khiếu nại, hoàn tiền, đồ thất lạc:** Tổng đài viên phân loại ticket và tra lịch sử chuyến thủ công ~8 phút/ticket; phản hồi rập khuôn, đồ thất lạc xử lý bằng cách gọi điện từng tài xế. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #___                                     │
│                                                             │
│ Bài toán (1 câu): ________________________________________  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. ___ ──> 2. ___ ──> 3. ___ ──> 4. ___                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? ___ (⏱ ___ phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? _____________________ │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

### 🃏 Quick Problem Card #1 — Điều phối sạc pin (Xanh SM)

| Mục | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Tài xế Xanh SM tự chọn trạm và giờ sạc theo cảm tính, dẫn đến dồn trạm giờ cao điểm, xếp hàng chờ và mất giờ chạy xe. |
| **Công ty thành viên** | [ ] VinFast [x] Xanh SM [ ] Vinhomes [ ] Vinmec [ ] Khác |
| **Ai đang đau (Actor)?** | Tài xế (mất thời gian, giảm số cuốc); điều phối viên vận hành (thiếu xe giờ cao điểm); V-Green (trạm quá tải cục bộ). |
| **Workflow thủ công hiện tại** | 1. Tài xế thấy pin còn ~20–30% ──> 2. Tự chọn trạm quen hoặc gần nhất ──> 3. Lái tới trạm, gặp hết cổng thì xếp hàng hoặc chạy sang trạm khác ──> 4. Sạc xong mới online lại nhận cuốc |
| **Bước tốn thời gian/lỗi nhất** | Bước 3: chờ cổng sạc (⏱ ~20 phút/lượt, ước tính). Lỗi đi kèm: xe pin thấp vẫn nhận cuốc xa, giữa chừng phải đi sạc. |
| **AI hỗ trợ ở bước nào?** | Bước 2: dự báo mức pin theo lộ trình và dự báo trạm nào sắp đầy trong 30–60 phút tới, rồi gợi ý trạm + khung giờ cho từng tài xế. Thêm ràng buộc cho điều phối: không gán cuốc xa khi pin thấp. |
| **Metric thành công (có số)** | Giảm thời gian chờ sạc trung bình từ ~20 phút ──> dưới 8 phút/lượt; giảm 50% số cuốc bị huỷ vì hết pin; tăng tỷ lệ kWh sạc ngoài giờ cao điểm điện. |
| **Quick Architecture** | [ ] No AI [x] Rule [ ] LLM [ ] Agent. Lõi là **ML dự báo + thuật toán tối ưu**, không cần LLM. |

### 🃏 Quick Problem Card #2 — Tái phân bổ xe, giảm chạy rỗng (Xanh SM)

| Mục | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Điều phối viên điều xe rỗng về khu có nhu cầu cao dựa trên kinh nghiệm, nên xe chạy rỗng nhiều trong khi giờ cao điểm vẫn thiếu xe cục bộ. |
| **Công ty thành viên** | [ ] VinFast [x] Xanh SM [ ] Vinhomes [ ] Vinmec [ ] Khác |
| **Ai đang đau (Actor)?** | Điều phối viên trung tâm; tài xế (chạy rỗng, đứng chờ sai khu); khách hàng (báo "không có xe gần bạn"). |
| **Workflow thủ công hiện tại** | 1. Điều phối viên theo dõi bản đồ xe và đơn trên dashboard ──> 2. Tự đoán khu nào sắp đông (sân bay, tan tầm, mưa, sự kiện) ──> 3. Nhắn/gọi nhóm tài xế điều về khu đó ──> 4. Tài xế tự quyết đi hay không, điều phối viên kiểm tra lại |
| **Bước tốn thời gian/lỗi nhất** | Bước 2–3: đoán thủ công nên phản ứng chậm 15–30 phút so với nhu cầu thực; mỗi đợt nhắn/gọi điều xe mất ⏱ ~5–10 phút (ước tính). |
| **AI hỗ trợ ở bước nào?** | Bước 2: dự báo nhu cầu theo từng ô khu vực, khung 15 phút (lịch bay, thời tiết, lịch sự kiện). Bước 3: tự động đẩy gợi ý điều xe tới từng tài xế đang rảnh gần nhất. |
| **Metric thành công (có số)** | Giảm tỷ lệ km rỗng từ ~35% ──> 30%; giảm thời gian khách chờ xe giờ cao điểm từ ~8 phút ──> dưới 5 phút; tăng tỷ lệ đặt xe thành công thêm 3 điểm %. |
| **Quick Architecture** | [ ] No AI [x] Rule [ ] LLM [ ] Agent. Lõi là **ML dự báo nhu cầu**; LLM chỉ có thể phụ trợ (đọc lịch sự kiện, tin tức thành dữ liệu đầu vào). |

### 🃏 Quick Problem Card #3 — CSKH khiếu nại, hoàn tiền, đồ thất lạc (Xanh SM)

| Mục | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Tổng đài viên Xanh SM xử lý thủ công khiếu nại, hoàn tiền và đồ thất lạc bằng cách tra nhiều hệ thống, mất ~8 phút/ticket và phản hồi rập khuôn. |
| **Công ty thành viên** | [ ] VinFast [x] Xanh SM [ ] Vinhomes [ ] Vinmec [ ] Khác |
| **Ai đang đau (Actor)?** | Tổng đài viên CSKH (quá tải giờ cao điểm); khách hàng (chờ phản hồi lâu); tài xế (bị gọi điện hỏi đồ thất lạc giữa ca). |
| **Workflow thủ công hiện tại** | 1. Nhận ticket từ app/hotline/fanpage ──> 2. Đọc và phân loại thủ công ──> 3. Tra chuyến đi (cước, lộ trình GPS, tài xế) trên 2–3 hệ thống ──> 4. Đối chiếu chính sách, quyết định hoàn tiền/xin lỗi/liên hệ tài xế ──> 5. Soạn phản hồi và đóng ticket |
| **Bước tốn thời gian/lỗi nhất** | Bước 3–4: tra cứu và đối chiếu chính sách (⏱ ~5 trong tổng ~8 phút/ticket, ước tính). Lỗi đi kèm: hoàn tiền sai chính sách, phản hồi không nhất quán. |
| **AI hỗ trợ ở bước nào?** | Bước 2: LLM phân loại ticket và trích xuất mã chuyến, loại khiếu nại. Bước 3–4: agent gọi tool tra chuyến, so lộ trình thực tế với lộ trình tối ưu, áp chính sách hoàn tiền có ngưỡng (ví dụ ≤ 50.000đ tự duyệt, trên ngưỡng chuyển người duyệt). Bước 5: soạn phản hồi theo ngữ cảnh. |
| **Metric thành công (có số)** | Giảm thời gian xử lý trung bình từ ~8 phút ──> dưới 3 phút/ticket; ≥ 40% ticket xử lý xong không cần người; tỷ lệ hoàn tiền sai < 1%. |
| **Quick Architecture** | [ ] No AI [ ] Rule [ ] LLM [x] Agent. **LLM + tools**, có human-in-the-loop cho ca vượt ngưỡng hoặc nhạy cảm. |

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ____ phút/lượt**.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Ai đang thực hiện tác vụ hằng ngày? |
| **2. Current Workflow** | Mô tả tóm tắt quy trình thủ công hiện tại và công cụ sử dụng. |
| **3. Bottleneck** | Bước nào chậm, lỗi, hoặc cần xử lý ngôn ngữ tự động nhiều nhất? |
| **4. Business Impact** | Tổn thất thực tế đo bằng thời gian, chi phí, hoặc SLA của Vingroup. |
| **5. Success Metric** | AI giải quyết được thì đạt ngưỡng số mấy? (Ví dụ: *"85% vé được phân loại dưới 10s"*). |
| **6. Operational Boundary** | AI được phép làm gì, TUYỆT ĐỐI không được làm gì, điểm nào cần duyệt? |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [ ] LLM Feature [ ] Agentic Loop.
* **Vẽ Future-State Flow:** Đánh dấu rõ:
  * 🔵 **AI Step:** Tác vụ LLM xử lý.
  * 🟢 **Human Step (HITL):** Bước con người phê duyệt/review (Human-in-the-loop).
  * ↩️ **Fallback:** Kế hoạch dự phòng khi LLM trả về kết quả lỗi hoặc không tự tin.

---

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [ ] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [ ] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
