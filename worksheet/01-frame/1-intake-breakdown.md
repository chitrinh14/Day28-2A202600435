---
artifact: 1 — Track & Big Ask + 2 — Tool Breakdown
bai-tap: Frame — nghe đúng đề rồi tách nhỏ
phase: Double Diamond vòng 1 · ◇ giãn (nghe rộng, chưa chốt)
time: ~12 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 00-context.md · track card · prompts/01-breakdown.md
nop-cuoi: Không — file trung gian (bản chốt phase này ở 3-FINAL-problem-framing.md)
---

# 1 — Intake & Breakdown: nghe đúng đề, tách nhỏ

Mục tiêu: cả nhóm hiểu giống nhau "công cụ lớn stakeholder muốn", rồi tách nó thành 5–8 use case nhỏ làm được riêng. Đây là nửa "giãn ra" của [Double Diamond](https://www.thefountaininstitute.com/blog/what-is-the-double-diamond-design-process) vòng 1 — nghe rộng, tách rộng, chưa chọn.

Lý do làm bước này: hai cái bẫy chết người ở đây. Một, nhận đề literal ("làm con chatbot") rồi nhảy vào build — trong khi yêu cầu mơ hồ thường chỉ là triệu chứng. Hai, ôm cả công cụ lớn đi pitch "build cả platform" → trượt Gate 1 ngay. Tách nhỏ là động tác bắt buộc để từ "một ý tưởng to" sang "danh sách phần làm được".

Quy tắc: **nghe trước, tách trước, chưa chọn.** Bước này không được chốt Quick Win (việc đó ở file `2`).

## Bước 0 — Đọc track card + 00-context (2 phút)

Đọc track card được giao và `00-context.md` (mục 2 đã điền). Đừng lướt.

## Quy trình 12 phút

```text
2 phút  — Bước 0: đọc track card + context
4 phút  — Phần A: phát biểu lại Big Ask bằng lời nhóm
6 phút  — Phần B: tách 5–8 use case + check độc lập
```

---

## Phần A — Phát biểu lại Big Ask bằng lời nhóm

Đừng chép lại đề. Cả nhóm nói lại "công cụ lớn stakeholder muốn" bằng lời mình. Nếu 3 người nói 3 kiểu khác nhau → chưa hiểu giống nhau, bàn thêm.

Câu hỏi phụ (tự trả lời):

- Stakeholder nói họ muốn gì, và họ thực sự *cần* gì — có khác nhau không?
- "Tại sao bây giờ?" — ở quy mô ~500 người, cái gì đang đau khiến phải làm công cụ này lúc này?
- Ai là người dùng đầu tiên thật sự, không phải "cả khóa"?

### Trả lời

- **Big Ask, viết lại bằng lời nhóm (2–3 câu)**: Stakeholder muốn một hệ thống "trợ giảng ảo" có thể tự động hóa toàn bộ luồng kiểm tra đánh giá quá trình của học viên. Công cụ này không chỉ đơn thuần là tạo đề và chấm điểm, mà cốt lõi là phải có khả năng phát hiện chính xác học viên đang hiểu sai khái niệm nào và tự động gợi ý đúng phần cần học lại. Về bản chất, họ cần một giải pháp cá nhân hóa lộ trình ôn tập cho học viên mà không cần sự can thiệp thủ công của con người.

- **Tại sao bây giờ**: Khi hệ thống scale lên ngưỡng ~500 người, ban quản lý hoàn toàn mất khả năng kiểm soát chất lượng ở tầng vi mô. Họ có thể thấy tỷ lệ rớt hoặc drop-out cao ở cuối kỳ nhưng không có data để biết học viên bắt đầu "gãy" từ đoạn nào. Doanh nghiệp cần công cụ này ngay lúc này để tự động hóa việc thu thập dữ liệu của toàn bộ khóa học, giúp họ tracking chất lượng mà không cần phình to quỹ lương để tuyển thêm đội ngũ TA. Đồng thời, engine này giúp họ phát hiện lỗi hệ thống: ví dụ, nếu hệ thống báo cáo 80% học viên đều bị misconception ở concept D28, ban quản lý sẽ biết ngay cần phải sửa lại nội dung bài giảng D28 thay vì đi đổ lỗi cho người học.

- **Người dùng đầu tiên cụ thể**: Người dùng đầu tiên sẽ là đội ngũ Trợ giảng (TA) và Giảng viên phụ trách một vài module/bài học cụ thể có chứa các khái niệm khó, dễ gây nhầm lẫn (ví dụ: bài D28 với concept Build/Buy/Boost). Ở phía người học, đó là nhóm học viên đang thử nghiệm học đến bài D28 đó, những người cần phản hồi tức thì ngay sau bài giảng để xác nhận xem mình đã hiểu đúng bản chất chưa trước khi bắt tay vào làm bài tập thực hành.

## Phần B — Tách công cụ lớn thành 5–8 use case

Nhìn mục **Big Vision Modules** trong track card. Mỗi dòng = 1 use case làm được riêng, viết dạng *"AI làm X cho ai để họ Y"* — không phải tính năng mơ hồ. Cần 5–8 dòng (ít hơn 5 = chưa tách đủ; nhiều hơn 8 = đang liệt kê vụn).
Dưới đây là phần điền cho **Phần B** dựa trên tư duy chia nhỏ sản phẩm (Product Breakdown) của một Business Analyst/Product Manager, tập trung vào việc bóc tách các luồng giá trị cốt lõi thay vì liệt kê tính năng vụn vặt:

| # | Use case (AI làm gì · cho ai · để họ làm được gì) | Người dùng | Làm được độc lập? |
| --- | --- | --- | --- |
| 1 | AI tự động sinh câu hỏi trắc nghiệm và câu hỏi ngắn từ tài liệu bài giảng cho Trợ giảng (TA) để họ tiết kiệm thời gian ra đề kiểm tra cho từng module. | Trợ giảng (TA) | Có |
| 2 | AI chấm điểm tự động các câu trả lời ngắn dựa trên rubric cho trước cho Trợ giảng (TA) để họ không phải đọc và chấm thủ công từng bài của hàng trăm học viên. | Trợ giảng (TA) | Có |
| 3 | AI phân tích câu trả lời sai để gắn thẻ misconception cụ thể, VD: nhầm Build với Buy cho Học viên để họ biết chính xác tư duy của mình đang sai ở bước nào. | Học viên | Không — phụ thuộc #2 |
| 4 | AI truy xuất và gợi ý chính xác tài liệu cần xem lại cho Học viên dựa trên lỗi sai của họ để họ chủ động bổ sung lại kiến thức ngay lập tức. | Học viên | Không — phụ thuộc #3 |
| 5 | AI tổng hợp dashboard báo cáo tần suất xuất hiện của các misconception trong một lớp cho Program Manager / Giảng viên để họ phát hiện điểm mù trong giáo trình và điều chỉnh bài giảng kịp thời. | PM / Giảng viên | Có (nếu dùng mock data/data có sẵn từ DB) |
| 6 | AI đóng vai học viên giả lập để làm thử đề thi cho Giảng viên để họ kiểm tra trước xem đề có quá mơ hồ hoặc đánh đố hay không trước khi phát hành. | Giảng viên | Có |

---

## Phát hiện ban đầu

* **Sự phân mảnh của hệ thống:** "Quiz & Auto-Grading Engine" thực chất chứa 2 luồng sản phẩm (product flows) hoàn toàn khác nhau: Luồng tạo đề - UC1, UC6 và Luồng chấm bài + chẩn đoán - UC2, 3, 4, 5. Nhóm rút ra rằng không nên ôm đồm build cả hai cùng lúc ở phase đầu.

* **Giá trị cốt lõi thực sự:** Chấm điểm nhanh (UC2) chỉ là tính năng giảm đau cho TA. Nhưng giá trị chiến lược đối với business nằm ở khâu chẩn đoán lỗi sai (UC3) và tổng hợp dữ liệu (UC5). Nếu AI chỉ chấm Đúng/Sai mà không lý giải được "Tại sao sai", nó sẽ không khác gì các công cụ trắc nghiệm truyền thống.

## Câu hỏi mở (mang sang bước chọn Quick Win)

* Dữ liệu đầu vào (Rubric, tài liệu bài giảng) của chúng ta hiện tại đã đủ "sạch" và chuẩn hóa để AI có thể hiểu và mapping ra các misconception một cách chính xác chưa?

* Giữa việc "TA đang quá tải vì chấm bài" và "Học viên đang rớt vì không hiểu bài (nhưng không ai biết sớm)", bài toán nào đang gây thiệt hại trực tiếp hơn đến các chỉ số OKRs của tổ chức ở thời điểm hiện tại để chọn làm Quick Win?

---

## Tổng kiểm tra trước khi sang `2-quick-win.md`

| Hạng mục | Xong? |
| --- | --- |
| Cả nhóm phát biểu lại Big Ask giống nhau, không cần nhìn card | [x] |
| Có 5–8 use case dạng "AI làm X cho ai để Y" | [x] |
| Có ≥4 use case thật sự độc lập | [x] |
| Nhóm KHÔNG còn ý định pitch "build cả platform" | [x] |

Sau bước này, mở `2-quick-win.md` — chấm điểm chọn 1 lát cắt làm trước.

*Liên quan: handbook §A1+§A2 · `prompts/01-breakdown.md` · `00-context.md`*
