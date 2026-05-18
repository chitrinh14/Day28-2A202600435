---
artifact: 4 — Problem Framing (bản nộp phase Frame)
bai-tap: Frame — đóng khung vấn đề thật
phase: Double Diamond vòng 1 · ◆ output (chốt — owner xác nhận)
time: ~13 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 2-quick-win.md · prompts/03-problem-framing-challenge.md
nop-cuoi: Có — đây là bản nộp của phase Frame (Part A · A3 Working Canvas mục Problem Framing)
---

# 3 — FINAL: Problem Framing

Mục tiêu: đóng khung Quick Win đã chọn cho thật cụ thể. Đây **không phải** bản đề xuất giải pháp — là tài liệu trả lời đúng 1 câu: *"nhóm đã hiểu đúng vấn đề chưa?"*. Đây là output chốt của [Double Diamond](https://www.thefountaininstitute.com/blog/what-is-the-double-diamond-design-process) vòng 1, và là một mục trong A3 Working Canvas nộp cuối buổi.

Lý do làm bước này: một AI Pilot Plan cho vấn đề SAI — dù viết hay — vẫn sai. Đa số nhóm trượt Gate 3 vì khung chung chung ("học viên cần học tốt hơn", "coach quá tải") — câu đó không đo được, không ai chịu trách nhiệm, không biết khi nào thành công.

Quy tắc: **pain phải có số.** "Nhiều người phàn nàn" không phải evidence. "200 câu hỏi/tuần × 20 phút = 67 giờ/tuần" mới là evidence. Trong lab dùng số giả định cũng được, nhưng phải nói rõ số đến từ đâu.

## Quy trình 13 phút

```text
9 phút  — Điền 9 mục Problem Framing
3 phút  — Tự phản biện
1 phút  — Chốt: owner (giả định) có xác nhận đúng vấn đề không
```

---

## 9 mục Problem Framing

Câu hỏi phụ (tự trả lời trước khi điền):

- Một người ngoài đọc khung này có biết CHÍNH XÁC ai đau, đau cái gì không?
- Nếu KHÔNG có baseline thì nhóm đo "tốt hơn" bằng cách nào?
- Mục Open Questions trống = nguy hiểm (chưa nghĩ đủ). Nhóm còn chưa biết gì?

### Trả lời

1. **Original Ask** (stakeholder nói gì, nguyên văn): "Tạo quiz từ bài học, chấm formative, phát hiện misconception và gợi ý học lại."

2. **Reframed problem** (vấn đề thật sau khi tách): Ở quy mô 500 học viên, ban quản trị (PM/Operations) đang bị "mù thông tin" về chất lượng khóa học ở tầng vi mô. Họ không biết học viên đang gặp rào cản nhận thức (misconception) ở những module cụ thể nào để kịp thời điều chỉnh giáo trình, dẫn đến việc không thể chủ động can thiệp trước khi học viên trượt bài kiểm tra cuối kỳ hoặc drop-out.

3. **Current workflow** (hiện tại đang xử lý thế nào, kể cả "không ai làm gì"): Hiện tại TA phải tự đọc và chấm điểm thủ công từng bài trả lời ngắn. Việc nhận xét chỉ dừng lại ở mức 1-1 (TA feedback cho từng học viên). Không có ai (và cũng không ai có đủ thời gian) để tổng hợp hàng trăm câu trả lời sai đó thành một báo cáo tổng quan (pattern) cho PM biết cả lớp đang hổng kiến thức ở đâu. PM chỉ nhìn thấy con số cuối cùng (VD: 20% rớt module D28).

4. **Pain evidence — bằng SỐ** (ai đau · đau ở khoảnh khắc nào trong việc · tần suất · quy mô; số giả định ghi rõ nguồn giả định):

```text
- Góc độ Quản trị (PM) - Giả định từ quy mô cohort 500 người:
  + Tỷ lệ drop-out hoặc điểm kém (dưới 6/10) ở một số module khó (như D28) lên tới 25-30% (tương đương 125-150 học viên).
  + Thời gian độ trễ (delay) để phát hiện ra lỗi hệ thống của giáo trình là quá lâu: Mất đến cuối khóa (1-2 tháng) mới có data tổng hợp, lúc đó cohort hiện tại đã chịu thiệt hại.

- Góc độ Vận hành (TA) - Giả định thời gian:
  + 500 học viên × 3 phút (để đọc, suy nghĩ và viết feedback cho 1 câu trả lời ngắn) = 1,500 phút (25 giờ làm việc) chỉ cho 1 bài tập của 1 module. Đây là nút thắt cổ chai không thể scale.
```

5. **Affected people** (ai dùng · ai quyết · ai là người review/expert):

    * **Người dùng trực tiếp (Đọc Dashboard):** Program Manager (PM), Head of Operations, Giảng viên chính.

    * **Người quyết định (Sponsor):** Head of Operations / Giám đốc chương trình.

    * **Người review/Expert (Kiểm định data):** Giảng viên chính, TA trưởng (để xác nhận AI gắn thẻ misconception đúng không).

6. **Constraints** (từ `00-context.md`: privacy / human review / citation / budget / formative / adoption):
    * **Privacy:** Dữ liệu lịch sử mang vào chạy batch phải được ẩn danh hóa (xóa tên, email học viên).

    * **Human Review:** AI chỉ đóng vai trò "chẩn đoán" và "gợi ý". Bất kỳ thay đổi nào về nội dung bài giảng D28 dựa trên Dashboard đều phải được Giảng viên phê duyệt.

    * **Adoption:** Phải xuất ra định dạng dễ đọc (Dashboard UI hoặc CSV) mà PM có thể dùng ngay, không bắt họ học tool mới.


7. **Quick Win đã chọn** (1 dòng, lấy từ file `2`): UC5 - AI chạy ngầm trên dữ liệu bài làm lịch sử của 1 module (VD: D28) để xuất ra Dashboard báo cáo các misconception phổ biến nhất.
8. **Open questions** (còn chưa biết gì — không được để trống):
    * Đã có sẵn bộ từ điển/taxonomy định nghĩa rõ các "misconception" chuẩn của bài D28 để làm barem cho AI đối chiếu chưa, hay AI phải tự cluster (nhóm) các câu trả lời lại theo ý nó?

    * File dữ liệu lịch sử (CSV) của cohort trước lưu trữ ở đâu? Format cột dữ liệu đang như thế nào?

    * Ngưỡng chính xác (accuracy) tối thiểu mà PM chấp nhận được đối với việc AI phân loại lỗi sai là bao nhiêu phần trăm? (80% hay 95%?).


9. **Validation** (đóng vai owner: *"đúng, đây là vấn đề đáng giải"* — Có / Chưa, vì sao):

```text
Có. Là một Head of Operations, việc nhìn thấy trước điểm mù của khóa học ngay khi nó đang diễn ra quan trọng hơn rất nhiều so với việc chỉ tự động hóa khâu chấm điểm. Nếu chứng minh được ở 1 module nhỏ, tôi sẽ có cơ sở (business case) để cấp ngân sách scale hệ thống chẩn đoán này ra toàn bộ khóa học, vừa cứu được tỷ lệ pass rate, vừa tối ưu được giờ làm của TA mà không mang rủi ro trực tiếp cho trải nghiệm của học viên.
```

---

## Tự phản biện

- Khung này còn câu chung chung kiểu "cần học tốt hơn" không?
    - Không. Vấn đề đã được khóa chặt vào việc "giảm độ trễ trong việc phát hiện điểm mù của giáo trình" và "tổng hợp dữ liệu chất lượng khóa học".

- 3 câu sẽ bị hỏi: *số/giả định lấy ở đâu · giả định chính sai thì sao · tình huống nào khiến dừng.* Trả lời thử 1 câu.  
    - Nếu AI không thể phân loại chuẩn xác các misconception, pilot sẽ dừng lại vì rác đầu vào (garbage in) sẽ dẫn đến quyết định sai lầm của PM (garbage out).

---

## Tổng kiểm tra trước khi sang `02-solution/`

| Hạng mục | Xong? |
| --- | --- |
| Chỉ rõ 1 nhóm người + 1 khoảnh khắc cụ thể (không "user nói chung") | [x] (Nhóm PM/Ops lúc cần review sức khỏe module D28) |
| Pain có số (hoặc kế hoạch lấy số), nói rõ số từ đâu | [x] (Có số giả định ở mục 4) |
| Có baseline (hoặc cách đo baseline) + ≥1 chỉ số có ngưỡng | [x] (Độ trễ hiện tại: 1-2 tháng → Goal: Báo cáo có ngay sau khi batch data chạy) |
| Mục 9: owner (giả định) xác nhận đúng vấn đề = qua cổng phase Frame | [x] |

⚑ Coach kiểm tra ở Mốc 2: *"Ai đau? Baseline là gì? Không có baseline thì đo thế nào?"*

Owner chưa xác nhận → quay lại file `1`/`2`, đừng sang Solution. Owner xác nhận → mở `../02-solution/1-find-existing-solutions.md`.

*Liên quan: handbook §A4 · `prompts/03-problem-framing-challenge.md`*
