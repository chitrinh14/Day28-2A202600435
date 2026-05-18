---
artifact: 7 — AI Pilot Plan core
bai-tap: Pilot Plan — cam kết hai chiều: xin – hứa – đo – dừng
phase: Double Diamond vòng 2 · ◇ giãn → ◆ siết (liệt kê hết rồi chốt gọn)
time: ~10 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 02-solution/2-FINAL-solution.md · 00-context.md · prompts/06-pilot-plan-challenge.md
nop-cuoi: Không — file trung gian (bản nộp ở 2-FINAL-pitch.md)
---

# 1 — AI Pilot Plan core

Mục tiêu: viết phần kế hoạch xin pilot — scope, người, data, budget, timeline, metric, exit criteria, adoption, lời hứa, lời xin. Bước này giãn ra (liệt kê hết những thứ cần) rồi siết lại (chốt bản gọn đủ để stakeholder quyết).

Lý do làm bước này: đây là thứ stakeholder dùng để **quyết approve hay dừng**. AI Pilot Plan **không phải proposal xin tiền** — là *cam kết hai chiều*: nhóm xin nguồn lực, đổi lại hứa giao evidence + chấp nhận dừng nếu metric fail. Demo đẹp mà không nói được "xin gì, hứa gì, đo gì, dừng khi nào" → trượt Gate 5.

Quy tắc: **budget tách từng hạng mục, không gộp 1 cục; không có mục "miscellaneous".** Exit criteria phải có người có quyền thực thi, không chỉ trên giấy.

## Quy trình 10 phút

```text
6 phút  — Điền 10 mục core (kéo nguyên liệu từ 00 + 01-frame + 02-solution)
3 phút  — Phần exit criteria + adoption (chỗ nhóm hay bỏ quên)
1 phút  — Tự phản biện
```

---

## 10 mục core

Câu hỏi phụ (tự trả lời):

- Nếu tóm vấn đề không gọn trong 1 câu → nhóm chưa hiểu vấn đề.
- Exit criteria của nhóm có ai DÁM thực thi khi sếp vẫn thích pilot không?
- Adoption: ai dùng đầu tiên — không phải "cả khóa ~500 người"?

### Trả lời

1. **Tóm vấn đề** (1 câu, từ Problem Framing): 
   > Ban quản trị (PM/Operations) đang bị "mù thông tin" về chất lượng vi mô của khóa học ở quy mô 500 học viên — không biết học viên gặp rào cản nhận thức (misconception) ở module nào để kịp can thiệp, dẫn đến tỷ lệ drop-out/rớt cao (25-30%) và không thể chủ động điều chỉnh giáo trình.

2. **Cách làm + lý do** (từ 02-solution, 1 câu): 
   > Boost: Sử dụng Gemini 1.5 Pro API + RAG (dữ liệu Handbook Day 28) + Few-shot Prompting để xây dựng hệ thống tự động phân tích bài làm lịch sử, gắn thẻ misconception phổ biến, và xuất Dashboard tóm tắt cho PM — vừa giảm rủi ro (công cụ nội bộ), vừa đảm bảo tốc độ (proof-of-concept trong 2 tuần), vừa tiết kiệm budget (~$25 cho pilot).

3. **Scope pilot**: 
   - **Phục vụ ai**: Program Manager (PM) / Head of Operations, Giảng viên chính, TA trưởng (người review)
   - **Bao nhiêu người**: 1 module test (Day 28 — 1 chủ đề, ~80 học viên trong track Product) — bộ dữ liệu lịch sử từ 1-2 cohort trước (~200-300 bài làm ngắn). KHÔNG scale ra 500 người toàn khóa.
   - **Bao lâu**: 3 tuần (14 ngày làm việc) từ khi approval
   - **Mấy phase**: 
     - **Phase 0 (Ngày 1-3)**: Setup dữ liệu, chuẩn bị Rubric + taxonomy misconception, thiết lập prompt baseline
     - **Phase 1 (Ngày 4-7)**: Calibration: AI chạy trên 30 bài mẫu, Coach review & feedback
     - **Phase 2 (Ngày 8-11)**: Batch chạy trên toàn bộ dữ liệu lịch sử (~300 bài), sinh Dashboard
     - **Phase 3 (Ngày 12-14)**: Review output, fix hallucination/sai, chuẩn bị demo + nhận xét từ PM

4. **Người**: 
   - **Nhóm làm** (Kỹ thuật): 1 người Engineer (setup API, RAG, prompt) + 1 người QA (test batch output)
   - **Ai review output rủi ro cao**: Lead Instructor & Lab Coach (kiểm duyệt rằng AI phân loại misconception CHÍNH XÁC trước khi cho PM xem)
   - **Ai có quyền quyết approve/dừng**: 
     - **Approve tiếp tục**: Head of Operations (sponsor)
     - **Dừng ngay**: Lead Instructor (nếu phát hiện AI hallucination hoặc sai lệch > 15% trong calibration phase)

5. **Data**: 
   - **Dùng data gì** (mẫu/giả định): 
     - Dữ liệu lịch sử bài làm ngắn của cohort trước (Day 28 module) — ~300 bài, đã ẩn danh (xóa tên, email, ID học viên)
     - Handbook + Slide Day 28 (công khai nội bộ) làm Knowledge Base cho RAG
     - Rubric chuẩn & danh sách 15 câu trả lời mẫu (5 Pass, 5 Misconception, 5 Fail) để Few-shot
   - **Cơ chế privacy**: Toàn bộ dữ liệu học viên được ẩn danh hóa trước khi input vào API. File CSV chứa: `[submission_id]` + `[student_response_text]` (không có tên, email). Output Dashboard chỉ hiển thị pattern & tần suất lỗi (không liệt kê từng học viên).
   - **Citation**: LLM prompt bắt buộc trích dẫn số trang/mục chính xác từ Handbook D28 trong mọi gợi ý học lại. Nếu câu trả lời nằm ngoài scope D28, AI trả lời: "Nội dung này nằm ngoài phạm vi bài học D28 — thảo luận với Coach trên Discord."

6. **Budget** (tách hạng mục): 
   | Hạng mục | Chi tiết | Giá | Ghi chú |
   |---|---|---|---|
   | **API (Gemini 1.5 Pro)** | 300 bài × $0.01/bài = 3 lần chạy calibration + 1 lần batch full | $10 | Không dùng miễn phí vì Gemini Flash 8B không đủ mạnh cho reasoning misconception phức tạp |
   | **Infrastructure** (Hosting Bot/Streamlit UI) | Cloudflare Workers (serverless) hoặc Vercel — miễn phí tier đủ cho pilot | $0 | Nếu quá tải, nâng lên Pro: ~$10/tháng |
   | **Thời gian Engineer** (Setup + Ops) | 1 người × 80 giờ (10 ngày × 8h) × $10/h (tính internal cost) | $800 | Đã được tính vào nhân lực nội bộ, không yêu cầu cấp thêm |
   | **Thời gian Lead Instructor** (Review & Calibration) | 12 giờ review + 4 giờ feedback | $200 (tính $12/h internal coaching rate) | Là phần không thể bỏ qua, rủi ro cao |
   | **Maintenance & Alert Monitoring** (nếu deploy dài hạn) | 1 người TA — 2h/tuần × 4 tuần | $80 (tính $10/h) | Hạng mục "ẨN": nếu PM muốn tiếp tục sau pilot, phải dành budget theo dõi |
   | **Hạng mục ẨN khác** | Training PM & Stakeholder cách đọc Dashboard | $0 (30 phút × 1 Coach) | Nhưng nếu bỏ qua → adoption fail |
   | **TỔNG CỘNG** | | **~$25 API + $800 nhân lực (nội bộ)** | Nếu không tính nhân lực nội bộ, chỉ tiền mặt = $25. Nếu scale lên, hạng mục maintenance sẽ tăng. |

7. **Timeline + cổng giữa phase**: 
   ```
   Ngày 1–3 (Phase 0: Setup)
   ├─► Chuẩn bị dữ liệu + Rubric + prompt baseline
   └─► [GATE 0] Lead Instructor approve prompt & rubric (hoặc yêu cầu sửa)
   
   Ngày 4–7 (Phase 1: Calibration)
   ├─► Chạy AI trên 30 bài mẫu
   ├─► Coach review kết quả + feedback
   └─► [GATE 1] Tỷ lệ đồng thuận (Calibration rate) ≥85% + Hallucination = 0%
       ├─ PASS → tiếp tục Phase 2
       └─ FAIL → dừng pilot, báo cáo root cause
   
   Ngày 8–11 (Phase 2: Batch Run)
   ├─► Chạy toàn bộ dữ liệu lịch sử (~300 bài)
   ├─► Sinh Dashboard: bảng tần suất lỗi, clustering misconception
   └─► [GATE 2] Cơ chế QA: Engineer + Coach spot-check 50 kết quả ngẫu nhiên
       ├─ PASS → tiếp tục Phase 3
       └─ FAIL → fix batch, chạy lại
   
   Ngày 12–14 (Phase 3: Review & Demo)
   ├─► Chạy thử trên 10 bài mới (thực tế) nếu có
   ├─► PM review Dashboard, yêu cầu điều chỉnh UI/metric
   └─► [GATE 3 = APPROVAL] Head of Operations + Lead Instructor sign off
       ├─ APPROVE → quyết định scale hoặc mở rộng
       └─ PAUSE → chỉ rõ cần sửa cái gì, lên kế hoạch vòng 2
   ```

8. **Metrics** (SMART + baseline + ngưỡng + ai đo):

| Metric | Đo bằng gì · ai đo | Baseline (hiện trạng) | Ngưỡng đạt | Tần suất đo |
|---|---|---|---|---|
| **Calibration Rate** (tỷ lệ AI khớp với Coach chấm lại) | Sau chạy 30 bài mẫu, Coach chấm lại & so sánh output AI vs Coach: % bài được AI & Coach gắn thẻ misconception **giống nhau** · Đo bởi: Lead Instructor | Chưa có (mới xây) | ≥85% | Ngày 7 (cuối Phase 1) |
| **Hallucination Rate** (AI bịa ra tài liệu không có) | Spot-check: đếm % bài mà AI trích dẫn sai trang / sai Handbook · Đo bởi: Coach + Engineer | Chưa có | 0% (zero hallucination tolerance) | Ngày 11 (Phase 2) + Ngày 14 (Phase 3) |
| **Time-to-Insight** (giảm độ trễ phát hiện lỗi) | Thời gian từ khi có data → đến khi PM nhận được Dashboard báo cáo · Đo bởi: PM + Engineer | Hiện tại: 1–2 tháng sau khóa (dùng data từ bài kiểm tra cuối) | <24 giờ sau khi chạy batch | Sau Phase 2 (Ngày 11) |
| **Dashboard Usability** (PM có thể dùng được không) | Sau Phase 3, PM dùng Dashboard trong 15 phút & trả lời: "Tôi biết được module nào đang có lỗi phổ biến không?" · Đo bởi: PM + Product Manager | Chưa có (UI chưa tồn tại) | ≥80% PM trả lời "Có, rõ ràng" | Ngày 14 |
| **Coverage** (bao nhiêu % bài làm được phân tích) | % bài mà hệ thống AI chạy được / tổng số bài trong dataset · Đo bởi: Engineer | Chưa có | ≥95% (chấp nhận ≤5% bài lỗi do format) | Ngày 11 (Phase 2) |

   **Leading indicator** (biết kết quả sớm trong 1–2 tuần): 
   - Trong Phase 1 (tuần 1-2), nếu Calibration Rate đã đạt ≥85% → sign đó cho thấy approach sẽ thành công
   - Nếu end-to-end pipeline (từ input data → output JSON → render Dashboard) chạy được không có lỗi → xác suất Phase 2-3 success cao

9. **Exit criteria** (định trước, ≥2 mức):

| Mức | Điều kiện | Hành động | Ai có quyền dừng |
|---|---|---|---|
| **Cảnh báo** (WARNING) | Calibration Rate < 85% ở Phase 1; hoặc Hallucination Rate > 0% ở bất kỳ phase nào; hoặc Time-to-Insight > 48 giờ | Dừng batch, debug prompt, review lại Few-shot examples, chạy lại Phase 1 | Lead Instructor (có thể điều chỉnh lại chứ không dừng luôn) |
| **Nghiêm trọng** (CRITICAL) | Calibration Rate ≤ 70% dù đã sửa prompt 2 lần; hoặc Hallucination Rate = 0% nhưng PM feedback "Dashboard không hữu ích / không biết cách dùng"; hoặc Cost overrun > 200% ngân sách API (≥ $20); hoặc PM quyết định không muốn tiếp tục (sau Phase 3 review) | Dừng ngay pilot, báo cáo root cause chi tiết, quay lại rethink Quick Win | Head of Operations (quyết định tối hậu) |

**Liên hệ Red Flag** (nếu được điền trong `00-context.md`): 
   - Nếu Red Flag #1 = "AI phán đoán sai sẽ gây rối loạn cho PM" → Exit CRITICAL nếu Dashboard chứa lỗi > 15%
   - Nếu Red Flag #2 = "Không ai dùng được tool" → Exit CRITICAL nếu PM không thể hiểu cách dùng Dashboard sau 30 phút training

10. **Adoption** (tool không ai dùng = $0):
    - **Ai dùng đầu tiên** (KHÔNG phải "cả khóa 500 người"): 
      - **Tier 1 (Week 1 sau pilot approve)**: Program Manager (PM) + Giảng viên chính Day 28. Họ kiểm tra Dashboard hàng tuần để phát hiện misconception mới.
      - **Tier 2 (nếu PM hài lòng, sau tuần 2)**: Mở rộng cho 3-4 Coaches khác từ các module khác, training họ cách dùng Dashboard & trigger "Yêu cầu Coach chấm lại" khi học viên khiếu nại.
    
    - **Workflow đổi ở đâu** (hiện tại vs sau):
      - **Hiện tại**: PM chỉ nhìn thấy con số cuối cùng (rớt/đậu) cuối khóa hoặc từ bài kiểm tra → không biết điểm mù nằm ở đâu → chỉ có thể nói chung chung "cần cải thiện"
      - **Sau pilot**: PM mỗi tuần kiểm tra Dashboard (export CSV hoặc UI Streamlit) → thấy ngay "Module D28 có 25% học viên gặp lỗi X (VD: confusion Build vs Boost)" → trực tiếp nói với Giáo viên "cần thêm ví dụ hoặc slide clarify Build vs Boost" hoặc đề xuất "có nên thay đổi nội dung bài hay không"
    
    - **Ai train/support**:
      - **Training PM & Giáo viên**: Product Manager hoặc Lab Coach — 30-45 phút, hướng dẫn:
        - Cách đọc bảng tần suất lỗi
        - Cách filter dữ liệu (VD: chỉ xem misconception > 10% frequency)
        - Cách export PDF hoặc share link Dashboard
        - Cơ chế báo cáo lỗi AI (nút "Report incorrect classification")
      - **Support runtime**: Engineer + Lead Coach (đọc Slack #support hoặc email để xử lý sự cố)
      - **Escalation**: Nếu PM phát hiện AI hallucination, báo cáo trực tiếp cho Engineer + Lead Instructor, không phải chỉ in ra log
    
    - **Nếu KHÔNG ai dùng thì sao**:
      - **Scenario A** (PM muốn dùng nhưng không hiểu): Phân bổ 4 giờ training bổ sung + tạo video hướng dẫn 10 phút, tái train PM
      - **Scenario B** (PM không thấy giá trị vì Dashboard format không phù hợp): Yêu cầu PM giải thích cụ thể "metric nào không hữu ích, cần gì khác" → điều chỉnh Dashboard (VD: thay đổi cách group lỗi, hiển thị trend over time, thêm cột "suggested remediation") → tái pitch sau 1 tuần
      - **Scenario C** (Sau 2 tuần mà PM vẫn chưa dùng): Dừng pilot, chuyển sang Quick Win khác (VD: UC2 — AI chấm điểm trực tiếp cho học viên), vì **adoption là proof-of-concept quan trọng nhất**, không phải chỉ accuracy trên giấy. Tool không ai dùng = $0 giá trị.

11. **Lời hứa** (REALISTIC — kể cả khi kết quả nói NÊN dừng):
    - **Nếu PASS cả 3 gate** (Calibration ≥85%, Hallucination = 0%, Dashboard usable, PM hài lòng):
      > "Sau 3 tuần, nhóm giao một Dashboard hoàn thiện (xuất file CSV + UI Streamlit/web app) cho PM có thể dùng ngay, giúp phát hiện misconception phổ biến trong module D28 (VD: học viên nhầm Build vs Boost) chỉ trong <24 giờ sau khi chạy batch — thay vì 1-2 tháng như hiện tại chờ tích hợp + analyze data thủ công. Nếu PM hài lòng, nhóm cam kết support 2h/tuần trong 1 tháng tiếp theo để giúp PM/Coaches triển khai hệ thống với các module khác."
    
    - **Nếu FAIL tại gate nào đó** (VD: Hallucination > 0%, hoặc Calibration rate < 70%, hoặc PM không thể dùng):
      > "Nếu phát hiện lỗi ở calibration phase (tuần 1-2), nhóm sẽ dừng ngay, không tiếp tục vào Phase 2-3 để tránh gây hại cho PM khi quyết định điều chỉnh giáo trình. Nhóm sẽ báo cáo chi tiết: cái gì sai, tại sao sai, root cause là gì, bài học là gì. Có thể mô hình hiện tại (Gemini 1.5 Pro) không phù hợp với loại reasoning phức tạp này, hoặc dữ liệu training cần xử lý kỹ hơn (VD: chuẩn hóa rubric chặt chẽ hơn). Nhóm sẽ ghi nhận và đề xuất Quick Win khác tốt hơn (VD: UC2 — chấm điểm trực tiếp cho học viên với rủi ro kiểm soát được hơn)."
    
    - **Backup plan nếu API Gemini bị sự cố hoặc đột ngột tăng giá**:
      > "Sẽ pivot sang Gemini Flash 8B (miễn phí) hoặc Claude 3.5 Sonnet (chi phí tương đương ~$0.01/bài), chạy lại benchmark trên 10 bài mẫu (1 ngày). Thời gian tổng có thể kéo dài thêm 2-3 ngày nhưng vẫn nằm trong 3 tuần pilot. Nếu API bị down hoàn toàn, sẽ đình chỉ pilot, báo cáo cho stakeholder, đề xuất lịch lại."

12. **Lời xin** (rõ ràng, không mơ hồ):
    - **Xin approve**: 
      - ✓ **Budget**: $25 API Gemini (hoặc $50 nếu cần pivot sang vendor khác)
      - ✓ **Dữ liệu**: 1 file CSV (~300 bài làm ngắn từ cohort trước, đã ẩn danh hóa không có tên/email)
      - ✓ **Nhân lực**: Lead Instructor dành **16 giờ** (8 giờ review prompt + rubric chuẩn hóa, 8 giờ calibration review & feedback)
      - ✓ **Quyền truy cập**: 
        - Google Gemini API (hoặc LLM API khác được phê duyệt)
        - Truy cập file Handbook D28 + Slide D28
        - Truy cập Google Drive/Slack để export output
    
    - **Xin hỗ trợ từ stakeholder**:
      - **PM (Head of Operations)**: 2 giờ × 2 lần 
        - Lần 1 (Ngày 0, trước Phase 0): Brief about dashboard, understand requirement
        - Lần 2 (Ngày 14, Phase 3): Feedback on output, usability test
      - **Giảng viên D28**: 1 giờ review Rubric + misconception list (Ngày 1-2) để chắc chắn Rubric đúng scope khóa học, không lệch
    
    - **Xin quyền**:
      - Được nói "Dừng pilot" nếu phát hiện AI hallucination hoặc calibration rate < 70% (không bắt phải tiếp tục bằng mọi giá)
      - Được pivot sang vendor API khác nếu Gemini bị sự cố
      - Được extend deadline +3 ngày nếu Phase 1 review phát hiện vấn đề cần fix lại prompt/rubric (timeline sẽ từ 3 tuần → max 3.5 tuần)
      - **Không được** bypass Lead Instructor review hoặc reduce training effort — đó là khâu kiểm soát rủi ro chính

---

## Tự phản biện

### 1. Budget thiếu hạng mục ẩn nào không?

**Có một số hạng mục ẩn cần lưu ý:**
- **Maintenance & Monitoring** (2h/tuần nếu deploy dài hạn) — đã liệt kê ở mục 6, nhưng nếu PM muốn tiếp tục sau pilot 4 tuần, sẽ cần +$80/tháng cho TA monitoring
- **Training bổ sung** nếu mở rộng cho 3-4 Coaches khác (không tính ở budget Phase 1 vì chỉ PM dùng trong tuần 1)
- **Contingency**: Nếu phải debug/fix hallucination lại prompt, có thể thêm 1-2 tuần → thêm $0 API nhưng +40 giờ Engineer time
- **Data cleaning** nếu file CSV input có format sạch sẽ hoặc corrupted (có thể mất 1-2 ngày)

**Cách xử lý**: 
- Ghi rõ ở Gate 3 (before scaling): "Nếu muốn mở rộng sang module khác, phải approve thêm budget maintenance ($80/tháng) và training Coaches"
- Ngày 1 Phase 0, Engineer validate data format & report sơ bộ → reserve 2-3 ngày data cleaning nếu cần

### 2. Exit criteria đủ mạnh để THẬT SỰ dừng, hay chỉ trên giấy?

**Rủi ro cao**: Lead Instructor có quyền dừng ở Gate 1, nhưng nếu Head of Operations "vẫn muốn cố tiếp" → có conflict authority.

**Giải quyết**: 
- **Trước khi bắt đầu pilot**, Lead Instructor & Head of Operations phải ký (hoặc confirm qua email) một memo: 
  > "Nếu Hallucination Rate > 0% hoặc Calibration rate < 70%, pilot sẽ **dừng ngay, không kéo dài**. Đây không phải negotiable."
- **Quy tắc hard stop**: **Hallucination = 0% là ĐKiện ĐỦ để dừng ngay** — không thể thương lượng
- Nếu có conflict, Engineer sẽ report trực tiếp cho **Chương trình quản lý** (Program Director), không phải chỉ PM, để đảm bảo independence
- Gate 2 & 3 là "optional tuning" chứ Gate 1 là "must pass"

### 3. Giả định quan trọng nhất sai → plan gì?

**Top 3 giả định rủi ro cao:**

**A. Dữ liệu input không sạch**
- **Giả định**: Dữ liệu lịch sử (~300 bài) có format sạch, không bị corrupted, encode đúng UTF-8
- **Nếu sai**: Sẽ mất 2-3 ngày data cleaning (đáng kể, vì pipeline phụ thuộc vào input) → delay Phase 1 → chạy lại deadline
- **Cách handle**: 
  - Ngày 1 Phase 0, Engineer validate data: kiểm tra format CSV, encoding, số rows, missing values
  - Nếu error > 5%, báo cáo ngay + extend Phase 0 thêm 2-3 ngày (timeline từ 3 tuần → 3.5 tuần)
  - Nếu error > 20%, cấp báo CRITICAL → xem có dữ liệu thay thế không?

**B. Gemini 1.5 Pro không đủ mạnh để phân loại misconception chính xác**
- **Giả định**: Gemini 1.5 Pro (hoặc API tương đương) có reasoning power đủ để hiểu "Build vs Boost" nuance phức tạp
- **Nếu sai**: Accuracy < 60% ngay từ 10 bài mẫu → model quá general, cần fine-tune hoặc đổi model → vượt ngân sách + timeline
- **Cách handle**: 
  - Benchmark trên 10 bài mẫu ngày 2 Phase 0 (không chờ tới Phase 1)
  - Nếu accuracy < 60%, pivot **ngay** sang Claude 3.5 Sonnet hoặc GPT-4o (chi phí tương đương $0.015/bài, tổng +$5)
  - Chạy lại benchmark 1 ngày → quyết định tiếp tục hay pivot sang Quick Win khác

**C. Lead Instructor không có đủ 16 giờ để review**
- **Giả định**: Lead Instructor sẵn sàng dành 16 giờ (4h × 4 tuần) không ảnh hưởng công việc khác
- **Nếu sai**: Review bị kéo dài → Calibration phase bị block 1-2 tuần → delay pilot hoàn toàn
- **Cách handle**: 
  - Lên lịch CỤ THỂ trước: 4 slots × 4h mỗi slot (VD: Thứ 2-4 tuần 1, Thứ 2-3 tuần 2, v.v.)
  - Khóa lịch của Instructor trong calendar, không dùng email informal
  - Nếu Instructor báo bận bất ngờ, lập tức **escalate** cho Head of Operations để tìm Co-Lead hoặc Plan B (không được delay cứng)

---

## Tổng kiểm tra trước khi sang `2-FINAL-pitch.md`

| Hạng mục | Xong? | Ghi chú |
|---|---|---|
| Tóm vấn đề trong 1 câu | ✓ | "PM mù thông tin về misconception ở quy mô 500 người" |
| Budget tách hạng mục, không "miscellaneous" | ✓ | API $10 + Infrastructure $0 + Nhân lực $800 (nội bộ) |
| Metric có baseline + ngưỡng + ai đo | ✓ | 5 metrics: Calibration Rate, Hallucination, Time-to-Insight, Usability, Coverage |
| Exit criteria có người có quyền thực thi (≥2 mức) | ✓ | Lead Instructor (warning), Head of Operations (critical) |
| Adoption: chỉ rõ ai dùng đầu tiên (không "cả khóa") | ✓ | Tier 1: PM + Giáo viên D28; Tier 2: 3-4 Coaches nếu PM hài lòng |
| Lời hứa realistic (kể cả fail case) | ✓ | Có backup plan & nếu fail cũng báo được lý do |
| Lời xin rõ ràng, không mơ hồ | ✓ | $25 budget + dữ liệu + 16h Instructor + quyền truy cập |
| Tự phản biện 3 giả định rủi ro cao | ✓ | Data sạch / Model mạnh / Instructor có thời gian |

**⚑ Coach kiểm tra ở Mốc 4**: *"Xin gì? (Budget $25 + dữ liệu + 16h Instructor) · Hứa gì? (Dashboard <24h + calibration ≥85% + adoption PM) · Đo gì? (7 metrics SMART) · Dừng khi nào? (Hallucination > 0% hoặc calibration < 70%)"*

**Lưu ý**: 
- Lời hứa gắn vào Exit criteria: Nếu không pass Gate 1, lời hứa "giao Dashboard" là invalid
- Budget hiển thị "ngoài" (API $25) và "trong" (nhân lực nội bộ $800) — khi pitch, highlight **chỉ $25** để show hiệu quả chi phí, nhưng cũng disclose nhân lực để stakeholder hiểu full picture

---

## Sau bước này

Mở `2-FINAL-pitch.md` — dồn tất cả thành 5-slide pitch + AI Support Log để nộp.

Liên quan: handbook §A7+§A8 · templates/ai-pilot-plan-core.md · prompts/06-pilot-plan-challenge.md
