---
artifact: 5 — Solution Approach + 6 — Demo/Mockup/Flow (bản nộp phase Solution)
bai-tap: Solution — chốt cách làm + cho stakeholder nhìn thấy
phase: Double Diamond vòng 2 · ◆ siết (chốt 1 cách làm + 1 artifact trực quan)
time: ~12 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 1-find-existing-solutions.md · 00-context.md · templates/demo-examples.md · prompts/05-demo-challenge.md
nop-cuoi: Có — bản nộp của phase Solution (Part B + C · A3 mục Solution Approach + Demo/Mockup/Flow)
---

# 2 — FINAL: Solution Approach + Demo/Mockup/Flow

Mục tiêu: chốt cách làm cho Quick Win (Build / Buy / Boost / Partner), nói rõ data & ai review cần có, và tạo 1 bản vẽ trực quan để stakeholder *nhìn* được. Đây là nửa "siết lại" của [Double Diamond](https://www.thefountaininstitute.com/blog/what-is-the-double-diamond-design-process) vòng 2 và là bản nộp của phase Solution.

Lý do làm bước này: hai cái bẫy. Một, "tự build" cho oai — trong khi 80–90% nhu cầu nội bộ chỉ cần Boost/Buy; tự build là quyết định khó rút lại nhất. Hai, chỉ nói bằng chữ — stakeholder không duyệt một đoạn văn, họ duyệt khi *nhìn thấy* flow. Không có bản vẽ → trượt Gate 4 dù lập luận tốt.

Quy tắc: **bản vẽ trực quan là BẮT BUỘC; demo chạy được chỉ là điểm cộng.** *Demo đơn giản + lập luận chặt > demo đẹp + lập luận yếu.*

## Quy trình 12 phút

```text
4 phút  — Phần A: chốt Build/Buy/Boost/Partner (decision tree + ego check)
3 phút  — Phần B: data & ai review cần có
5 phút  — Phần C: vẽ 1 artifact trực quan + đánh dấu chỗ người review
```

---

## Phần A — Chốt cách làm

Đi decision tree, đừng chọn theo cảm giác:

```text
Bài này có phải LỢI THẾ CẠNH TRANH CỐT LÕI không?
 ├─ CÓ  → đội có AI engineer mạnh? CÓ → Build · KHÔNG → Boost
 └─ KHÔNG (chỉ là productivity layer) → có tool sẵn?
          CÓ → Buy · KHÔNG → Boost (model sẵn + data riêng)
```

Câu hỏi phụ:

- Nhóm chọn cách này vì *cần* hay vì *thích tự build*? Một câu thành thật.
- Hướng nào ở file `1` (đã tìm được người làm rồi) khớp với cách này — "đi từ 5 lên"?

### Trả lời

- **Cách làm chốt**: Boost (Sử dụng LLM API thương mại mạnh mẽ có sẵn như Gemini 1.5 Pro / GPT-4o kết hợp với dữ liệu/rubric tri thức độc quyền của khóa học AI20k thông qua RAG và Few-shot Prompting).
- **Lý do CẦN (không phải thích), 2–3 câu**: Hệ thống Auto-grading không phải là lợi thế cạnh tranh cốt lõi (core AI engine) của tổ chức mà là một "productivity & learning layer" giúp tối ưu hóa việc vận hành. Việc "Build từ số 0" (tự huấn luyện mô hình) là hoàn toàn lãng phí, bất khả thi với ngân sách nhỏ và không thể kịp tiến độ pilot; trong khi "Buy" (mua giải pháp SaaS đóng gói bên ngoài) lại không cho phép tùy biến sâu vào các khái niệm đặc thù của khóa học (như Build/Buy/Boost hay Partnership). Do đó, "Boost" là lựa chọn tối ưu nhất về chi phí, tốc độ và khả năng kiểm soát tri thức.
- **Vì sao KHÔNG "Build từ số 0"**: Tự huấn luyện một LLM riêng từ đầu hoặc fine-tune một mô hình mã nguồn mở đòi hỏi chi phí server/GPU khổng lồ, đội ngũ AI engineer chuyên trách bảo trì, và mất hàng tháng trời thử nghiệm, trong khi chất lượng xử lý ngữ nghĩa chưa chắc đã vượt qua được các API thương mại hiện có.
- **Tool / API / vendor cần + ước lượng chi phí thô** (budget nhỏ, ưu tiên sẵn có):
  + *LLM API*: Google Gemini 1.5 Pro API (hoặc OpenAI GPT-4o API) để xử lý luồng chấm điểm và trích xuất JSON. Chi phí ước tính: ~$0.01/bài test. Với 80 học viên × 3 lần làm thử/người = 240 lượt run, tổng chi phí API cho đợt pilot D28 chỉ tốn dưới $10.
  + *Giao diện tương tác*: Tích hợp thẳng vào Discord thông qua Discord Bot API (sử dụng Python/Node.js trên server nhỏ hoặc dịch vụ serverless miễn phí như Vercel/Cloudflare Workers) hoặc một trang Web App đơn giản bằng Streamlit/Gradio. Chi phí: $0 - $15/tháng.
  + *Tổng chi phí thô cho Pilot*: ~$25 (Cực kỳ tiết kiệm).

## Phần B — Data & ai review (cách làm này cần gì để chạy được)

| Cần gì | Có sẵn trong AI20k? | Trong lab dùng (mẫu/giả định) | Privacy? |
|---|---|---|---|
| Data: Tài liệu Handbook & Slide Day 28 (để làm Knowledge Base cho RAG) | Có sẵn | Dùng trọn bộ tài liệu handbook Day 28 | Tài liệu nội bộ khóa học (Không chứa thông tin cá nhân) |
| Data: Rubric chấm điểm Short Answer & Danh sách 5 Misconceptions phổ biến (đặc biệt về Build/Buy/Boost) | Có sẵn (dạng thô) | Dùng bảng Rubric chuẩn hóa kèm 15 câu trả lời mẫu (5 Pass, 5 Misconception, 5 Fail) | Dữ liệu học thuật mẫu (Không vi phạm privacy) |

- **Output nào rủi ro cao** (sai gây hậu quả): AI nhận diện sai misconception (ví dụ học viên hiểu đúng nhưng AI lại bảo sai) hoặc trích dẫn sai nguồn tài liệu (hallucination), khiến học viên bức xúc, mất niềm tin vào hệ thống và khiếu nại lên giảng viên.
- **Ai review + bao nhiêu mẫu + pass/fail theo gì**:
  + *Trước khi triển khai (Pre-flight Review)*: Lead Instructor và Head Coach trực tiếp kiểm duyệt bộ Prompt gốc, bảng Rubric và chạy thử nghiệm (benchmarking) trên 30 câu trả lời mẫu của các khóa trước. *Tiêu chí Pass*: Tỷ lệ đồng thuận (Calibration rate) giữa AI và Coach đạt ≥85%, tỷ lệ hallucination trích dẫn = 0%.
  + *Trong quá trình Pilot (Runtime Review)*: Hệ thống có nút "Báo cáo chấm sai / Yêu cầu Coach chấm lại". Lab Coach phụ trách sẽ nhận cảnh báo và review các trường hợp học viên khiếu nại.
- **Có cần citation / nói "không biết" khi thiếu nguồn không**: BẮT BUỘC. LLM được cấu hình prompt nghiêm ngặt: Mọi lời giải thích và gợi ý học lại phải kèm theo số trang/mục chính xác trong handbook D28. Nếu câu trả lời của học viên nằm ngoài phạm vi kiến thức D28, AI bắt buộc trả lời: "Nội dung này nằm ngoài phạm vi đánh giá của bài học Day 28, vui lòng thảo luận trực tiếp với Coach trên Discord."

## Phần C — Bản vẽ trực quan (BẮT BUỘC)

Chọn **1** dạng nhẹ nhất đủ rõ (xem `templates/demo-examples.md`): mockup 2–3 màn hình · user flow trước/sau · prompt flow · agent flow · 1 cặp input–output thật. Vẽ tay / ASCII / bảng đều được.

```text
===================================================================================================
                    BẢN VẼ TRỰC QUAN: KIẾN TRÚC & LUỒNG TƯƠNG TÁC (PROMPT & USER FLOW)
===================================================================================================

[HỌC VIÊN] 
    │
    ├─► 1. Truy cập Web App / Discord Bot chọn "Quiz Day 28 - AI Pilot Plan"
    ├─► 2. Trả lời câu hỏi ngắn: "Giải thích chiến lược Build/Buy/Boost và áp dụng cho Track 8?"
    │      (Ví dụ input: "Em nghĩ nên tự build một LLM riêng từ đầu để chấm bài cho chuẩn và bảo mật.")
    │
[HỆ THỐNG AI ENGINE: GEMINI 1.5 PRO + RAG]
    │
    ├─► 3. Truy xuất Knowledge Base (Handbook D28 - Mục §A5) & Rubric chuẩn
    ├─► 4. Phân tích ngữ nghĩa & Đối chiếu Few-shot examples
    │
[JSON STRUCTURED OUTPUT] ──┐
    │                      ▼
    │     {
    │       "status": "Needs Review",
    │       "score": "4/10",
    │       "misconception_detected": "Hiểu sai về chiến lược Build/Buy/Boost (Mặc định tự Build).",
    │       "explanation": "Học viên đang mắc lỗi ngụy biện 'tự build cho oai'. Hệ thống chấm bài chỉ là productivity layer, không phải core cạnh tranh. Tự build LLM tốn kém tài nguyên, vượt quá ngân sách và không kịp tiến độ 6 tuần pilot.",
    │       "remediation_action": "Đọc lại Handbook Day 28, mục §A5 (trang 12) - Decision Tree cho Build/Buy/Boost.",
    │       "coach_alert": false
    │     }
    │
[GIAO DIỆN HIỂN THỊ KẾT QUẢ CHO HỌC VIÊN]
    │
    ├─► [Thẻ Kết Quả]: ⚠️ KẾT QUẢ: CHƯA ĐẠT (Formative Feedback)
    ├─► [Phân Tích Lỗi]: Bạn đang mắc hiểu lầm phổ biến #2: Lạm dụng chiến lược 'Build từ số 0'.
    ├─► [Gợi Ý Học Lại]: 📖 Vui lòng xem lại Handbook Day 28 - Mục §A5 (trang 12).
    └─► [Nút Hành Động]: [Làm Lại Quiz]  │  [🚨 Báo Cáo Coach Chấm Lại (Human Review)]

===================================================================================================
Chỗ con người review (output rủi ro cao) nằm ở:
1. PRE-PILOT: Lead Instructor duyệt toàn bộ System Prompt, bảng Rubric và Few-shot benchmark.
2. RUNTIME: Nút [🚨 Báo Cáo Coach Chấm Lại] cho phép học viên yêu cầu Lab Coach can thiệp, chấm lại và ghi đè (override) kết quả của AI nếu AI chấm sai.
```

Câu hỏi phụ — một người đóng vai stakeholder nhìn 20 giây: *hiểu user làm gì, nhận lại gì, không cần giải thích thêm không? Có chỗ nào "đẹp nhưng rỗng" không?* -> Rất rõ ràng, thể hiện cụ thể input của học viên, quá trình RAG, output JSON và luồng Human review.

---

## Tổng kiểm tra trước khi sang `../03-pilot-plan/`

| Hạng mục | Xong? |
|---|---|
| Cách làm có lý do CẦN, không phải "mặc định tự build" | [x] |
| Nói rõ data cần + ai review output rủi ro cao | [x] |
| Có ≥1 bản vẽ trực quan, người ngoài hiểu trong ~20 giây | [x] |
| Có đánh dấu chỗ con người review | [x] |

⚑ Coach kiểm tra ở Mốc 3: *"Stakeholder nhìn vào đâu để hiểu flow? Mockup/sketch/demo đâu?"* Chỉ nói bằng chữ = chưa qua.

Sau bước này, mở `../03-pilot-plan/1-pilot-plan.md`.

*Liên quan: handbook §A5+§A6 · `templates/demo-examples.md` · `prompts/05-demo-challenge.md`*
