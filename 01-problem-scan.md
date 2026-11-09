# 01 — Problem Scan & Quick Problem Cards

> **Vai trò:** AI Product Engineer — Vin Smart Future (Trưởng nhóm)
> **Nội dung:** Phase 1 (SCAN) và Phase 2 (QUICK-ASSESS) từ `01-worksheet.md`.
> Các con số có ghi *(ước tính)* là giả định để so sánh và chọn bài toán, chưa phải số đo thực tế.

---

# 🔍 Phase 1 — SCAN

Quét hoạt động vận hành của các công ty thành viên Vingroup bằng **4 Lenses**: Lặp lại · Tốn thời gian · AI có thể tốt hơn · Pain từ người khác.

### 📝 List bài toán của nhóm

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | **Vinhomes** | Pain từ người khác + Tốn thời gian | Cư dân phải đến trực tiếp Ban Quản lý (BQL) để đăng ký thi công nội thất, vé gửi xe tháng hoặc cấp thẻ cư dân → **AI chatbot hỗ trợ đăng ký và thực hiện thủ tục trực tuyến 24/7.** |
| 2 | **Vinhomes** | AI có thể tốt hơn | Cư dân không biết cần chuẩn bị giấy tờ gì, dễ nộp thiếu hoặc sai hồ sơ → **AI dùng RAG tra cứu quy định, hướng dẫn và tự động tạo biểu mẫu theo yêu cầu.** |
| 3 | **Vinmec** | Tốn thời gian | Khi làm bệnh án, bác sĩ phải tổng hợp thủ công lời kể của bệnh nhân cùng kết quả xét nghiệm từ các phòng ban → **AI hỗ trợ tổng hợp bản nháp bệnh án.** |
| 4 | **Vinpearl** | Pain từ người khác + Lặp lại | Quét review trên **Booking.com, Agoda, Google Maps** của Vinpearl (đa nền tảng, đa ngôn ngữ) để lọc ra các phàn nàn khẩn cấp → **AI dịch, gắn nhãn dịch vụ và soạn email nháp gửi đúng bộ phận xử lý.** |
| 5 | **Xanh SM** | Tốn thời gian | Tài xế tự chọn trạm và giờ sạc theo cảm tính: xe dồn về cùng một trạm V-Green vào cuối ca/giờ nghỉ trưa và xếp hàng chờ; nhiều xe sạc giờ cao điểm điện, trong khi xe gần hết pin vẫn nhận cuốc xa → **AI hỗ trợ điều phối sạc pin.** |
| 6 | **VinFast** | AI có thể tốt hơn | Khách hàng không hiểu mã lỗi hoặc cảnh báo trên xe → **AI giải thích mã lỗi bằng ngôn ngữ dễ hiểu** và hướng dẫn bước tiếp theo (tự xử lý / đặt lịch xưởng / gọi cứu hộ). |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

**Tiêu chí chọn top 3:** (1) mức đau và tần suất, (2) dữ liệu có sẵn để thử, (3) rủi ro khi AI sai có kiểm soát được không.
#3 (Vinmec) không chọn vì rủi ro y tế cao, bác sĩ phải duyệt 100% và dữ liệu bệnh án rất nhạy cảm. #6 (VinFast) không chọn vì giải thích sai mã lỗi an toàn (phanh, pin) có thể gây nguy hiểm, cần dữ liệu kỹ thuật chính hãng mà nhóm không tiếp cận được. #1 và #2 (Vinhomes) được gộp vào một card vì cùng một hành trình của cư dân.

### 🃏 Card #1 — Vinpearl: Review Analyzer ⭐ (chọn để Deep-Dive)

```
┌──────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                                │
│                                                                      │
│ Bài toán (1 câu): Review của khách Vinpearl trên Booking.com, Agoda, │
│   Google Maps phải được đọc, dịch, phân loại và chuyển tay đến từng  │
│   bộ phận, 4 phút/review với ~260-420 review/ngày toàn chuỗi.        │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes           │
│                     [ ] Vinmec   [x] Khác: Vinpearl (Khách sạn)      │
│                                                                      │
│ Ai đang đau (Actor)? Nhân viên và Manager phụ trách Guest Relations; │
│   trưởng các bộ phận nhận việc; khách lưu trú.                       │
│                                                                      │
│ Workflow thủ công hiện tại:                                          │
│   1. Truy cập từng nền tảng ──> 2. Đọc + DỊCH review ──>             │
│   3. Phân loại mức độ, gắn nhãn dịch vụ, trích xuất nội dung ──>     │
│   4. Soạn email/tin nhắn gửi Manager & bộ phận liên quan             │
│                                                                      │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3: dịch đa ngôn ngữ và gắn   │
│   nhãn dịch vụ không nhất quán (4 phút/review tổng, ước tính)        │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bot lấy review từ các kênh;    │
│   LLM dịch, gắn nhãn dịch vụ + mức độ, trích xuất nội dung, SOẠN     │
│   EMAIL NHÁP [DRAFT_ONLY] cho từng bộ phận để GR duyệt và gửi.       │
│                                                                      │
│ Đo thành công bằng gì (Metric có số)?                                │
│   - Thời gian GR: 4 phút ──> ~1,5 phút/review (giảm ~60%)            │
│   - Review khẩn cấp đến trưởng bộ phận < 30 phút sau khi đăng        │
│   - ≥ 90% review gán đúng bộ phận; recall ≥ 98% với Critical         │
│                                                                      │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent          │
└──────────────────────────────────────────────────────────────────────┘
```

**Vì sao chọn để Deep-Dive:**
* **Quy mô lớn, đo được:** Vinpearl có 31–35 cơ sở, 1,9 triệu đêm phòng (2024); với tỉ lệ để lại review 5–8% → ~260–420 review/ngày (cận trên, tính trên đêm phòng; theo lượt lưu trú ≈ 130–210), tương đương tới ~17–28 giờ công/ngày chỉ để đọc và chuyển review *(ước tính)*.
* **Tác động kinh doanh rõ:** phát hiện và xử lý sớm → ít review 1–2 sao → điểm sao và thứ hạng OTA tăng → nhiều người đặt phòng hơn; review gắn nhãn nhất quán còn giúp đánh giá chất lượng dịch vụ từng bộ phận.
* **Rủi ro kiểm soát được:** AI chỉ tạo **email nháp nội bộ**, GR duyệt trước khi gửi; không đăng gì công khai.
* **Dữ liệu sẵn có:** review là dữ liệu công khai, có lịch sử để test.

**Tự phản biện (CFO / Trưởng phòng vận hành):** *"Sao không thuê thêm nhân viên GR?"* — Thêm người không giải quyết rào cản tiếng Hàn/Trung/Nga, phân loại cảm tính và độ trễ ngoài giờ. *"Rule từ khóa có đủ không?"* — Đủ cho từ khóa an toàn rõ ràng (giữ lại làm lưới chặn), nhưng không xử lý được 5 ngôn ngữ, review nói về nhiều dịch vụ và không soạn được email có ngữ cảnh. *"Giảm 60% có thật không?"* — AI tiết kiệm ~90% khâu đọc/dịch/phân loại, nhưng con người vẫn phải kiểm tra lại và chỉ đạo xử lý → 50–60% là mốc cam kết an toàn cho toàn quy trình.

### 🃏 Card #2 — Vinhomes: trợ lý thủ tục cư dân trực tuyến (gộp #1 + #2)

```
┌──────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                                │
│                                                                      │
│ Bài toán (1 câu): Cư dân phải đến BQL làm thủ tục (thi công nội      │
│   thất, vé xe tháng, thẻ cư dân) và hay nộp thiếu/sai giấy tờ vì     │
│   không biết quy định.                                               │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes           │
│                     [ ] Vinmec   [ ] Khác                            │
│                                                                      │
│ Ai đang đau (Actor)? Cư dân; nhân viên tiếp nhận hồ sơ tại BQL.      │
│                                                                      │
│ Workflow thủ công hiện tại:                                          │
│   1. Cư dân hỏi BQL cần giấy tờ gì ──> 2. Đến BQL nộp hồ sơ ──>      │
│   3. NV kiểm tra, trả lại nếu thiếu ──> 4. Cư dân bổ sung, nộp lại   │
│                                                                      │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3-4 — hồ sơ thiếu phải đi lại  │
│   (~15 phút/lượt tại quầy, ước tính; nhiều lượt cho 1 hồ sơ)         │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Chatbot RAG tra cứu quy định   │
│   của từng dự án, liệt kê đúng giấy tờ, tạo biểu mẫu điền sẵn; BQL   │
│   vẫn là người duyệt hồ sơ.                                          │
│                                                                      │
│ Đo thành công bằng gì (Metric có số)?                                │
│   - ≥ 70% thủ tục thông dụng được nộp trực tuyến, không cần đến BQL  │
│   - Tỉ lệ hồ sơ bị trả lại vì thiếu giấy tờ giảm 50%                 │
│   - Câu trả lời về quy định đúng ≥ 95% trên bộ 100 câu hỏi kiểm tra  │
│                                                                      │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent          │
└──────────────────────────────────────────────────────────────────────┘
```

**Điểm yếu:** nhiều thủ tục có thể giải quyết bằng **form trực tuyến có checklist cố định (rule)**; LLM/RAG chỉ cần cho câu hỏi tự do và quy định khác nhau giữa các dự án. AI không được tự duyệt hồ sơ hay trả lời sai quy định → cần dẫn nguồn văn bản quy định.

### 🃏 Card #3 — Xanh SM: điều phối sạc pin cho tài xế

```
┌──────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                                │
│                                                                      │
│ Bài toán (1 câu): Tài xế tự chọn trạm và giờ sạc theo cảm tính nên   │
│   xe dồn về cùng trạm V-Green giờ cao điểm, xếp hàng chờ, trong khi  │
│   xe gần hết pin vẫn nhận cuốc xa.                                   │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes           │
│                     [ ] Vinmec   [ ] Khác                            │
│                                                                      │
│ Ai đang đau (Actor)? Tài xế Xanh SM; điều phối viên; khách hàng chờ  │
│   xe.                                                                │
│                                                                      │
│ Workflow thủ công hiện tại:                                          │
│   1. Tài xế xem pin, tự chọn trạm ──> 2. Đến trạm, xếp hàng ──>      │
│   3. Sạc ──> 4. Quay lại nhận cuốc                                   │
│                                                                      │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 — xếp hàng chờ (~20 phút/    │
│   xe/lượt giờ cao điểm, ước tính)                                    │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Gợi ý trạm + khung giờ sạc     │
│   theo mức pin, tình trạng trạm và nhu cầu cuốc; pin < 5% → điều xe  │
│   sạc di động thay vì chỉ trạm xa.                                   │
│                                                                      │
│ Đo thành công bằng gì (Metric có số)?                                │
│   - Thời gian chờ tại trạm giờ cao điểm: ~20 ──> < 8 phút            │
│   - 0 xe pin < 5% được chỉ tới trạm > 5 km                           │
│                                                                      │
│ Quick Architecture: [ ] No AI  [x] Rule  [x] LLM  [ ] Agent          │
└──────────────────────────────────────────────────────────────────────┘
```

**Điểm yếu:** phần lõi là **bài toán tối ưu** (thuật toán điều phối trên dữ liệu pin, GPS, trạm) — rule/optimization làm tốt hơn LLM; LLM chỉ hợp cho phần giao tiếp với tài xế. Ranh giới an toàn pin < 5% được nhóm stress-test trong `starter-code/prompt_prototype.py`.

---

### ✅ Kết luận Phase 2

| Card | Mức đau / tần suất | Dữ liệu sẵn có | Rủi ro khi AI sai | AI có thật sự cần? | Kết luận |
|---|---|---|---|---|---|
| #1 Vinpearl Review Analyzer | Cao — 260–420 review/ngày | ✅ Review công khai + lịch sử | Thấp–TB (email nháp nội bộ có duyệt) | ✅ Đa ngôn ngữ, nhiều dịch vụ | **Chọn Deep-Dive** |
| #2 Vinhomes thủ tục | Trung bình | ⚠️ Cần số hóa quy định từng dự án | Thấp–TB | ⚠️ Phần lớn giải được bằng form | Dự phòng |
| #3 Xanh SM sạc pin | Cao | ⚠️ Cần dữ liệu pin/trạm thời gian thực | Cao (an toàn xe) | ⚠️ Lõi là tối ưu hóa, không phải LLM | Để sau |

➡️ Phân tích chi tiết Card #1 tại [`02-deep-dive-report.md`](02-deep-dive-report.md), sơ đồ quy trình hiện tại tại [`04-workflow-diagram.png`](04-workflow-diagram.png).
