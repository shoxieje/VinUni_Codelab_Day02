
# 🏗️ Phase 3 — DEEP-DIVE (Nhóm)

## 3.1. Current-State Workflow
Quy trình theo dõi, phân tích và xử lý review của khách hàng tại Vinpearl hiện tại:

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Truy cập các │     │ Đọc và tổng  │     │ Phân loại    │     │ Tổng hợp và  │
│ nền tảng     │ ──→ │ hợp review   │ ──→ │ nội dung,    │ ──→ │ gửi báo cáo  │
│ đánh giá     │     │ khách hàng   │     │ cảm xúc và   │     │ cho Manager  │
│              │     │              │     │ mức độ       │     │              │
│              │     │              │     │ nghiêm trọng │     │              │
│ Ai: nhân viên│     │ Ai: nhân viên│     │ Ai: nhân viên│     │ Ai: nhân viên│
│ ⏱ 30 giây    │     │ ⏱ 1 phút 🔴 │     │ ⏱ 1 phút 30 giây 🔴 │     │ ⏱ 1 phút    │
│ In: Review   │     │ In: Nội dung │     │ In: Review   │     │ In: Kết quả  │
│ Out: Dữ liệu │     │ Out: Nội dung│     │ Out: Nhóm    │     │ Out: Báo cáo │
│ review       │     │ đã đọc       │     │ vấn đề       │     │ cảnh báo     │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘

🔴 = Bottlenecks
⏱ Tổng thời gian xử lý thủ công: 4 phút/lượt.
```

---

## 3.2. Problem Statement (6-field) — Vin Smart Future Standard

| Field | Nội dung |
|---|---|
| **1. Actor / Operator** | Nhân viên chăm sóc khách hàng (CSKH), bộ phận quản lý chất lượng dịch vụ và Manager phụ trách các bộ phận tại Vinpearl. |
| **2. Current Workflow** | Nhân viên CSKH/ Bộ phần quản lý chất lượng dịch vụ truy cập Booking.com, Agoda và Google Maps để theo dõi review mới. Sau đó đọc nội dung, xác định chủ đề, cảm xúc, mức độ nghiêm trọng, tổng hợp các vấn đề và gửi báo cáo đến các Manager phụ trách. Quy trình gồm 4 bước, chủ yếu thực hiện thủ công, mất khoảng 4 phút/review theo giả định ban đầu.|
| **3. Bottleneck** | Bước 2 & 3 (mất khoảng 2 phút 30 giây): Nhân viên phải đọc từng review, hiểu ngữ cảnh, nhận diện cảm xúc, xác định vấn đề và đánh giá mức độ nghiêm trọng. Đặc biệt, các review dài hoặc chứa nhiều vấn đề cùng lúc khiến việc phân loại mất thời gian và dễ bỏ sót khiếu nại quan trọng. |
| **4. Business Impact** |Tốn thời gian nhân sự cho việc theo dõi và phân loại review. Các phàn nàn nghiêm trọng có thể không được phát hiện kịp thời, làm chậm quá trình xử lý sự cố, ảnh hưởng đến trải nghiệm khách hàng và uy tín thương hiệu Vinpearl trên các nền tảng đánh giá trực tuyến. |
| **5. Success Metric** | 1. Giảm thời gian phân tích review từ khoảng 4 phút xuống dưới 15 giây/review. 2. Tỷ lệ review được phân loại tự động đạt ≥ 90%. 3. 100% cảnh báo mức độ nghiêm trọng cao được chuyển đến Manager hoặc nhân viên phụ trách để xác nhận |
| **6. Operational Boundary** | AI được phép phân tích nội dung review, nhận diện cảm xúc, phân loại chủ đề, đánh giá mức độ nghiêm trọng và tạo cảnh báo cho Manager. Có thể tự động tổng hợp báo cáo theo ngày/tuần. AI không được tự động phản hồi công khai review của khách hàng, không được tự ý kết luận trách nhiệm của nhân viên hoặc tự động đưa ra quyết định kỷ luật. Các khiếu nại nghiêm trọng cần có nhân viên xác minh và xử lý (Human-in-the-Loop – HITL).|

---

## 3.3. Future-State Flow & AI Fit

* **AI Fit:** Chọn **LLM Feature** (Không cần xây dựng Agent tự trị vì quy trình có các bước xử lý cố định. Việc kết hợp LLM với Classification và Rule Engine giúp kiểm soát kết quả, giảm chi phí và hạn chế rủi ro AI phân loại sai).
* **Quy trình tương lai (Future-State):**

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Thu thập     │     │ 🔵 AI phân   │     │ 🔵 Rule      │     │ 🟢 Manager    │
│ review mới   │ ──→ │ tích review  │ ──→ │ Engine đánh  │ ──→ │ nhận cảnh báo │
│ từ các nền   │     │ và phân loại │     │ giá mức độ   │     │ và xác nhận   │
│ tảng         │     │              │     │ ưu tiên      │     │ xử lý         │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                           │                    │
                           │                    ▼
                           │             ┌──────────────┐
                           │             │ Tự động tổng │
                           │             │ hợp báo cáo  │
                           │             │ theo ngày    │
                           │             └──────────────┘
                           │
                           ▼
                    ↩️ Fallback:
                    Nếu AI không đủ độ tin cậy,
                    review được chuyển đến
                    nhân viên CSKH phân loại
                    thủ công.
```

---



# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [X] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test?
2. [X] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)?
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ?

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[X] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> *Viết lý giải chi tiết tại đây*
Nhóm quyết định GO vì bài toán có đầu vào, đầu ra và quy trình xử lý rõ ràng. Giải pháp LLM kết hợp Classification và Rule Engine có thể tự động hóa công đoạn đọc, phân tích và phân loại review, giúp giảm thời gian xử lý từ khoảng 4 phút xuống dưới 15 giây/review theo mục tiêu đề ra. Phương án này không đòi hỏi xây dựng Agent tự trị phức tạp, giúp tiết kiệm chi phí và dễ kiểm soát rủi ro. Tuy nhiên chưa xác nhận được liệu bên phía Stakeholders có đồng ý thay đổi quy trình làm việc và thử nghiệm giải pháp của nhóm hay không.
---