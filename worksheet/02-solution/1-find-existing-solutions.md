---
artifact: 5 — Solution Approach (phần khám phá)
bai-tap: Solution — tìm lời giải đã có sẵn trước khi tự xây
phase: Double Diamond vòng 2 · ◇ giãn (mở hết lựa chọn, chưa chốt)
time: ~8 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 01-frame/3-FINAL-problem-framing.md · 00-context.md · prompts/04-find-solutions.md
nop-cuoi: Không — file trung gian (bản chốt ở 2-FINAL-solution.md)
---

# 1 — Find existing solutions (đừng xây lại từ số 0)

Mục tiêu: trước khi quyết Build / Buy / Boost / Partner, nhóm phải biết bài này đã có ai giải ở chỗ khác chưa, và họ giải bằng cách nào. Đây là nửa "giãn ra" của [Double Diamond](https://www.thefountaininstitute.com/blog/what-is-the-double-diamond-design-process) vòng 2 — mở hết các lời giải đang tồn tại, chưa chốt cái nào.

Lý do làm bước này: đây là chỗ nhiều nhóm hỏng mà không biết. Hỏng vì nhảy thẳng vào "tự build" cho oai, trong khi 80–90% nhu cầu nội bộ chỉ cần Boost hoặc Buy. Hỏng vì không hỏi "ai làm rồi" nên đi lại từ số 0. Gần như bài nào cũng đã có người giải ở một ngành khác — không thấy thì phí cả pilot.

Quy tắc: **không có nguồn = giả định.** Mỗi cái AI/web nói ra, hỏi lại "lấy ở đâu?". Không chỉ được nguồn thì đánh dấu 🧮 (giả định để giảng), đừng xài như fact.

## Bước 0 — Bài này thực ra là dạng bài gì? (2 phút)

Bỏ context AI20k sang một bên. Mô tả Quick Win của nhóm như một bài toán chung — không có chữ "học viên / coach / Discord". Vài ví dụ cho dễ hình dung:

- "câu hỏi của user → câu trả lời kèm nguồn" → đây là bài Q&A có citation
- "một đống văn bản lộn xộn → data có cấu trúc" → bài extraction
- "bài nộp → nhận xét theo rubric" → bài rubric grading

Dạng bài (the pattern) đó gần như chắc chắn đã có người làm ở ngành khác. Tìm ra dạng bài → tìm ra người đã giải nó.

- **Quick Win của nhóm, viết lại thành 1 dạng bài chung (không có chữ domain)**: Bài toán Phân tích câu trả lời ngắn, đối chiếu với Rubric chuẩn để trích xuất lỗi sai khái niệm (Misconception Extraction & Rubric-based Formative Grading) kết hợp truy xuất tài liệu tham khảo (RAG - Retrieval-Augmented Generation).
- **Input → output thực chất là gì**:
  + *Input*: Câu trả lời ngắn dạng văn bản tự do của người dùng + Tài liệu chuẩn (Rubric & Knowledge base).
  + *Output*: Điểm số đánh giá mức độ hiểu (Pass/Needs Review) + Lời giải thích chỉ ra lỗi sai khái niệm cụ thể + Link/Trích dẫn chính xác tài liệu cần đọc lại.
- **Ràng buộc không bỏ được (lấy từ `00-context.md`)**: Ngân sách thấp (không xây platform mới), bắt buộc trích dẫn nguồn (citation), kết quả chỉ mang tính định hướng (formative), và phải có con người (chuyên gia) kiểm duyệt bộ rubric/prompt gốc.

## Quy trình 8 phút

```text
2 phút  — Bước 0: gọi tên dạng bài
4 phút  — Phần A: deep research 4 tầng "ai giải dạng bài này rồi"
2 phút  — Phần B: rút về 2–3 hướng khả thi, đánh dấu nguồn
```

---

## Phần A — Deep research: ai giải dạng bài này rồi, giải sao?

Không phải gõ 1 câu vào AI rồi chép. Chạy 4 tầng, **tầng sau lấy kết quả tầng trước làm input**. Khung câu lệnh ở `prompts/04-find-solutions.md`.

Câu hỏi phụ (tự trả lời — viết ra cái nhóm *tìm thấy*, không phải cái nhóm *đoán*):

- Dạng bài này giống bài nào ở một ngành hoàn toàn khác?
- Hướng nào AI gợi ý mà nhóm **không kiểm được nguồn** — vậy có nên tin không?
- Một ca thất bại của người đi trước dạy nhóm tránh đúng điều gì?
- Nhóm "đi từ mức mấy" — kế thừa được gì để khỏi bắt đầu từ 0?

### Trả lời — điền theo 4 tầng

| Tầng | Hỏi AI/web câu gì | Tìm được gì | Nguồn / 🧮 nếu là giả định |
|---|---|---|---|
| 1 · Map | "Dạng bài Rubric-based Short Answer Grading & Misconception Extraction thường giải bằng những hướng nào? 4–6 hướng, mỗi hướng khi nào nên dùng." | Tìm thấy 4 hướng chính: (1) Keyword matching / Regex (nhanh, rẻ nhưng không hiểu ngữ nghĩa, dễ bị lách); (2) Fine-tuned SLM (tốt cho domain hẹp nhưng tốn chi phí và thời gian huấn luyện); (3) Prompt Engineering / Few-shot prompting với SOTA LLM (như GPT-4o, Claude 3.5 Sonnet, Gemini 1.5 Pro) kết hợp RAG (linh hoạt, chi phí đầu tư ban đầu thấp, hiệu quả cao với văn bản tự do); (4) Agentic Workflow với luồng LLM kép (1 LLM chấm, 1 LLM kiểm tra lại và trích xuất tài liệu). | 🧮 Báo cáo nghiên cứu ứng dụng LLM trong EdTech (2025) / Tổng hợp các mô hình Auto-grading của Khan Academy & Coursera. |
| 2 · Tiền lệ | "Đội nào (ngành bất kỳ) đã làm Auto-grading & Misconception Detection ở quy mô tương tự? Họ làm cách nào?" | (1) **Khanmigo (Khan Academy)**: Sử dụng luồng LLM được thiết kế prompt kỹ lưỡng để đóng vai trò gia sư Socratic, nhận diện lỗi sai tư duy của học sinh và hướng dẫn thay vì đưa đáp án. (2) **Gradescope (thuộc Turnitin)**: Sử dụng AI hỗ trợ phân nhóm các câu trả lời ngắn có cú pháp/ngữ nghĩa tương tự nhau (AI-assisted grading), sau đó giáo viên chỉ cần chấm 1 câu đại diện cho cả nhóm. (3) **Duolingo (Max)**: Dùng LLM giải thích lỗi sai ngữ pháp cho người học (Explain My Answer) dựa trên context bài học cụ thể. | 🧮 Case study Khan Academy triển khai Khanmigo (2024) / Whitepaper của Gradescope về AI-assisted grading. |
| 3 · Phản chứng | "Ca nào làm Auto-grading thất bại? Nguyên nhân gốc là cách làm hay chuyện khác?" | Một số trường đại học và nền tảng EdTech thử nghiệm chấm tự động bằng LLM nhưng thất bại nặng nề vì 3 nguyên nhân: (1) **Hallucination trong giải thích**: LLM tự bịa ra lý do sai hoặc trích dẫn sai sách giáo khoa khiến sinh viên phẫn nộ; (2) **Thiếu độ đồng thuận (Poor Calibration)**: AI chấm quá khắt khe hoặc quá lỏng lẻo so với giảng viên do prompt thiếu các edge case; (3) **Phản ứng tâm lý (Pushback)**: Sinh viên cảm thấy không được tôn trọng khi bài làm tâm huyết bị "máy chấm" một cách vô hồn mà không có sự tham gia của con người. | 🧮 Các báo cáo phân tích thất bại của AI Tutor tại các trường đại học Mỹ (Chronicle of Higher Education, 2024). |
| 4 · Thu hẹp | "Với ràng buộc [budget nhỏ · có người review · cần citation], hướng nào khả thi cho pilot 6 tuần?" | Hướng khả thi nhất là **Few-shot Prompting kết hợp cơ chế RAG nhẹ (Lightweight RAG)** trên nền tảng API LLM thương mại (Gemini 1.5 Pro / GPT-4o) kết nối với giao diện web app đơn giản (hoặc Discord bot). Quy trình: LLM nhận câu trả lời -> Đối chiếu với Rubric & Few-shot examples đã được Lead Instructor duyệt -> Xuất kết quả theo định dạng JSON chuẩn (gồm Trạng thái, Lỗi sai, Citation) -> Ghi log để Coach theo dõi. | 🧮 Kiến trúc RAG cơ bản trong EdTech / Thực tiễn triển khai API LLM chi phí thấp. |

---

## Phần B — Rút về 2–3 hướng khả thi

Câu hỏi phụ:

- Hướng nào *kế thừa được nhiều nhất* từ người đã làm?
- Hướng nào nghe hay nhưng nhóm **không có nguồn** để tin?

### Trả lời

| Hướng giải khả thi | Ai làm rồi (gần bài mình nhất) | Nguồn / 🧮 | Hợp ràng buộc `00-context`? |
|---|---|---|---|
| Hướng 1: Few-shot Prompting + RAG nhẹ qua API LLM (Gemini/GPT-4o) tích hợp Web/Discord bot. | Khanmigo (Khan Academy) & Duolingo Max (luồng giải thích lỗi sai). | 🧮 Case study Khanmigo / Kiến trúc LLM API. | Có. Chi phí thiết lập cực rẻ (chỉ trả tiền API), dễ dàng chỉnh sửa prompt, trích dẫn chính xác tài liệu D28, hoàn toàn phù hợp ngân sách và thời gian pilot 6 tuần. |
| Hướng 2: AI-Assisted Clustering (Gộp nhóm câu trả lời tương đương bằng Embedding, Coach chấm 1 câu cho cả nhóm). | Gradescope (AI-assisted grading cho câu hỏi ngắn). | 🧮 Whitepaper Gradescope. | Có. Đảm bảo 100% độ chính xác vì con người (Coach) vẫn là người quyết định điểm số cuối cùng, AI chỉ làm nhiệm vụ phân loại và gom nhóm. Tuy nhiên, tốc độ phản hồi cho học viên sẽ chậm hơn Hướng 1 (phải chờ Coach vào chấm). |

**"Đi từ 5 lên" — nhóm kế thừa cụ thể cái gì** (1–2 câu):

```text
Nhóm kế thừa trọn vẹn kiến trúc "Few-shot Prompting kết hợp Structured Output (JSON)" từ các hệ thống AI Tutor tiên tiến như Khanmigo, đồng thời học hỏi bài học thất bại từ các dự án trước bằng cách áp dụng cơ chế "Human-in-the-loop" (Lead Instructor duyệt bộ rubric/prompt gốc và Coach có quyền override kết quả) cùng yêu cầu trích dẫn nguồn (citation) bắt buộc để triệt tiêu tình trạng hallucination.
```

---

## Phát hiện ban đầu

Ghi nhanh 2–3 cái đáng chú ý nhất (chưa phải quyết định — quyết định ở file FINAL):

- Việc sử dụng LLM để chấm điểm tự do rất dễ dẫn đến cảm tính nếu không có "Few-shot examples" (các ví dụ mẫu về câu trả lời đúng/sai/nửa vời). Bộ ví dụ mẫu này đóng vai trò quan trọng hơn cả câu lệnh prompt.
- Không cần thiết phải fine-tune mô hình riêng (vừa đắt vừa lâu), một mô hình SOTA hiện tại kết hợp với RAG tài liệu Day 28 là quá đủ để đạt độ chính xác >85% trong việc phát hiện misconception.
- Việc minh bạch thông tin (cho học viên biết đây là AI chấm formative và cung cấp link khiếu nại/gặp Coach) giúp giải quyết triệt để rào cản tâm lý của người học.

## Câu hỏi mở (mang sang bước chốt)

- Nên chọn Hướng 1 (AI chấm tự động 100% formative ngay lập tức) hay Hướng 2 (AI gom nhóm để Coach chấm)? (Nhóm nghiêng về Hướng 1 vì tính instant feedback, nhưng sẽ dùng Hướng 2 như một cơ chế dự phòng/bổ trợ cho Coach).
- Cấu trúc file JSON output của LLM cần thiết kế thế nào để giao diện frontend dễ dàng hiển thị thẻ "Gợi ý học lại" một cách trực quan nhất?

---

## Tổng kiểm tra trước khi sang `2-FINAL-solution.md`

| Hạng mục | Xong? |
|---|---|
| Gọi được dạng bài trong 1 câu, không còn chữ domain | [x] |
| Đủ 4 tầng deep research, tầng nào cũng có kết quả | [x] |
| Mỗi kết quả có nguồn, hoặc đánh dấu 🧮 nếu là giả định | [x] |
| Rút về 2–3 hướng + nói được "đi từ 5 lên" cái gì | [x] |

Hàng nào chưa xong → quay lại Phần A, đừng sang bước chốt vội.

Sau bước này, mở `2-FINAL-solution.md` — chốt Build/Buy/Boost/Partner + data & ai review + bản vẽ trực quan (đây là bản nộp của phase này).

*Liên quan: handbook §A5 · `prompts/04-find-solutions.md` · `00-context.md`*
