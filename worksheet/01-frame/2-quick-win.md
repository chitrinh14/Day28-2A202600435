---
artifact: 3 — Quick Win Selection
bai-tap: Frame — chọn lát cắt làm trước
phase: Double Diamond vòng 1 · ◆ siết (hội tụ về 1 lựa chọn)
time: ~10 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 1-intake-breakdown.md · prompts/02-quick-win-challenge.md
nop-cuoi: Không — file trung gian (bản chốt phase này ở 3-FINAL-problem-framing.md)
---

# 2 — Quick Win: chọn lát cắt làm trước

Mục tiêu: từ 5–8 use case ở file `1`, chấm điểm nhanh và chốt **1 Quick Win** để pilot đầu tiên — kèm lý do chọn và lý do *không* chọn các phần khác. Đây là nửa "siết lại" của [Double Diamond](https://www.thefountaininstitute.com/blog/what-is-the-double-diamond-design-process) vòng 1.

Lý do làm bước này: đây là quyết định quan trọng nhất của phase Frame. Quick Win **không phải** phần dễ nhất hay nghe hay nhất — là phần *chứng minh được giá trị nhanh và có người ủng hộ*. Chọn sai → pilot fail → mất uy tín → khó xin pilot tiếp. Nhóm phải chọn được *và bảo vệ được bằng lý do*, không bằng cảm tính.

Quy tắc: **điểm số chỉ là gợi ý, không phải đáp án.** Đừng để con số quyết thay nhóm — nó chỉ giúp so sánh.

## Bước 0 — Lấy 4–6 use case mạnh nhất từ file `1` (1 phút)

## Quy trình 10 phút

```text
1 phút  — Bước 0: chọn 4–6 ứng viên
5 phút  — Phần A: chấm điểm 4 trục
3 phút  — Phần B: 1 lý do nên / 1 lý do không cho top 2
1 phút  — Phần C: chốt + ai ủng hộ + cái KHÔNG chọn
```

---

## Phần A — Chấm điểm 4 trục (1–5 mỗi trục)

Câu hỏi phụ (tự trả lời):

- "Risk" ở đây là *sai thì mất gì* — chọn đúng việc chính của user (task centrality) thì sai cũng đỡ đau; chọn việc lớn nhất thì sai rất đắt. Use case nào risk thấp thật?
- Use case nào có sẵn data + có người trong AI20k thật sự muốn dùng?


| Use case | Impact | Feasibility | Evidence nhanh | Risk (cao = an toàn) | Tổng |
| --- | --- | --- | --- | --- | --- |
| UC1: AI sinh câu hỏi từ tài liệu | 3 | 4 | 4 | 4 | **15** |
| UC2: AI chấm điểm câu trả lời ngắn | 4 | 3 | 5 | 2 *(sai điểm ảnh hưởng Hv)* | **14** |
| UC3: AI phân tích & gắn thẻ lỗi sai (Misconception) | 5 | 3 | 4 | 3 *(nhận xét sai đỡ hơn chấm rớt)* | **15** |
| UC5: AI tổng hợp Dashboard tần suất lỗi sai cho PM | 5 | 4 | 4 | 5 *(internal tool, cực an toàn)* | **18** |


(Thang điểm chi tiết: `templates/quick-win-scoring.md`.)

## Phần B — 1 lý do nên / 1 lý do không, cho top 2

**Ứng viên A — UC2: AI chấm điểm tự động câu trả lời ngắn**

```text
Nên chọn vì: Đánh trúng ngay "nỗi đau" bề mặt là sự quá tải của TA. Có thể đo lường evidence cực nhanh (Ví dụ: giảm từ 5 phút/bài xuống 30s/bài).

Không nên vì: Rủi ro user (Học viên) phản ứng rất cao. Nếu AI chấm sai hoặc có bias, học viên sẽ khiếu nại, gây khủng hoảng niềm tin vào toàn bộ hệ thống ngay trong lần pilot đầu tiên.
```

**Ứng viên B — UC5: AI tổng hợp Dashboard các lỗi sai phổ biến cho Program Manager (Chạy ngầm batch data)**

```text
Nên chọn vì: Mang lại giá trị chiến lược cho khâu quản trị chất lượng khóa học ở quy mô 500 người. Rủi ro bằng 0 vì đây là công cụ nội bộ (internal tool), không trả kết quả trực tiếp cho học viên.

Không nên vì: Không giải quyết triệt để cơn đau tức thời của TA (họ vẫn phải duyệt lại bài). Cần phải có sẵn tập dữ liệu như bài làm lịch sử của học viên đủ dày để chạy demo.
```

## Phần C — Chốt Quick Win

* **Quick Win nhóm chọn**: UC5 - AI chạy ngầm trên dữ liệu bài làm lịch sử của 1 module (VD: D28) để xuất ra Dashboard báo cáo các misconception phổ biến nhất.

* **Vì sao chọn cái này trước** (2–4 câu, bám điểm + impact + evidence nhanh): Pilot này có rủi ro thấp nhất (Risk = 5) vì là công cụ nội bộ, sai sót của AI không trực tiếp gây hại đến điểm số của người học. Quan trọng hơn, nó chứng minh ngay lập tức giá trị cao nhất của hệ thống là khả năng xác định được sức khỏe của khóa học. Bằng cách xử lý một tệp data có sẵn (past data), ta show được kết quả (evidence) chỉ sau vài giờ thiết lập lệnh prompt mà không cần chờ tích hợp (integrate) một luồng UI phức tạp vào app học tập.

* **Ai trong AI20k sẽ ủng hộ pilot này**: Program Manager (PM) / Head of Operations. Vì họ là người chịu trách nhiệm về tỷ lệ hoàn thành và chất lượng đầu ra. Họ đang rất cần data thực tế để biết hệ thống "gãy" ở đâu, thay vì chỉ có báo cáo rớt/đậu chung chung.

* **Nhóm KHÔNG chọn gì + vì sao** (≥2 use case bị loại):

    1. **Không chọn UC4 (AI gợi ý tài liệu học lại cho Học viên):** Vì tính năng này đứng ở cuối phễu. Nếu hệ thống bắt lỗi (UC3) chưa chuẩn, việc gợi ý tài liệu sẽ càng làm học viên rối loạn. Quá rủi ro và phức tạp để làm pilot.

    2. **Không chọn UC1 (AI tự động sinh câu hỏi):** Dù khá dễ làm (Feasibility cao) nhưng impact rất thấp (nice-to-have). TA có thể dùng ChatGPT cơ bản để tự làm việc này, không đáng để đầu tư thành một module phần mềm ở phase 1.

---

## Phát hiện ban đầu

* Giá trị lớn nhất của AI trong giáo dục không phải là "chấm điểm thay người", mà là khai phá dữ liệu (data mining) các lỗi tư duy hệ thống - thứ mà con người không đủ thời gian để tổng hợp và nhìn ra được pattern ở quy mô lớn.

* Bằng cách đẩy target audience của lần pilot đầu tiên từ "Học viên/TA" sang "Ban quản lý (PM)", ta giảm thiểu gần như toàn bộ rủi ro về độ chính xác (hallucination) của AI trong giai đoạn đầu.

## Câu hỏi mở (mang sang Problem Framing)

* Để demo được cái Dashboard này trong buổi pitch, chúng ta lấy tập dữ liệu (dataset) ở đâu? Có thể xin một file CSV chứa 100 câu trả lời ngắn đã được ẩn danh của cohort trước cho bài D28 không?

* Định dạng output của AI cần như thế nào (JSON, CSV?) để dễ dàng đưa lên một công cụ trực quan hóa (như Google Data Studio hoặc Metabase) cho PM xem?

---

## Tổng kiểm tra trước khi sang `3-FINAL-problem-framing.md`

| Hạng mục | Xong? |
| --- | --- |
| Có bảng chấm 4 trục cho ≥4 use case | [x] |
| Chốt 1 Quick Win, lý do bám số/impact (không "nghe hay") | [x] |
| Nêu rõ ai ủng hộ pilot này | [x] |
| Ghi rõ ≥2 phần KHÔNG chọn + lý do | [x] |

⚑ Đây là phần coach kiểm tra ở Mốc 1: *"Vì sao không làm full tool? Vì sao chọn lát cắt này trước?"*

Sau bước này, mở `3-FINAL-problem-framing.md` — đóng khung vấn đề thật (bản nộp của phase Frame).

*Liên quan: handbook §A3 · `templates/quick-win-scoring.md` · `prompts/02-quick-win-challenge.md`*
