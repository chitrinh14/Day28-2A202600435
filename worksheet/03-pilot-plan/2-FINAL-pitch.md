---
artifact: 8 — 5-slide Pitch + AI Support Log (bản nộp cuối lab)
bai-tap: Pilot Plan — dồn thành pitch, sẵn sàng phản biện
phase: Double Diamond vòng 2 · ◆ output (bản nộp cuối + present)
time: ~5 phút (xem deck để biết khung giờ chính xác trong buổi)
input: 1-pilot-plan.md + toàn bộ 01-frame + 02-solution · templates/5-slide-pitch.md
nop-cuoi: Có — bản nộp cuối lab (Part E · 5-slide Pitch + AI Support Log)
---

# 2 — FINAL: 5-slide Pitch + AI Support Log

Mục tiêu: dồn cả A3 Working Canvas thành 5 slide pitch (5 phút), chuẩn bị trả lời 3 câu phản biện, và ghi AI Support Log. Đây là bản nộp cuối cùng của lab.

Lý do làm bước này: nguyên tắc *demo đơn giản + lập luận chặt > demo đẹp + lập luận yếu*. Slide đẹp mà không trả lời được "số này lấy ở đâu" thì hỏng. Pitch không phải kể chuyện — là đưa evidence để stakeholder ra được một quyết định.

Quy tắc: **slide cuối phải là một lời xin rõ ràng** (xin gì · đổi lại hứa gì). Không có lời xin = stakeholder không biết approve cái gì.

## Quy trình 5 phút

```text
3 phút  — Dồn 5 slide (mỗi slide 1 thông điệp)
1 phút  — Chuẩn bị 3 câu phản biện
1 phút  — AI Support Log
```

---

## Phần A — 5 slide (mỗi slide 1 thông điệp)

Kéo nguyên liệu từ các file đã làm, đừng viết mới. Khung đầy đủ: `templates/5-slide-pitch.md`.

### **SLIDE 1: Problem & User**
*Từ: 01-frame/3-FINAL-problem-framing.md*

**Thông điệp**: 
- **Ai đau**: Program Manager / Head of Operations (quản lý quy mô 500 học viên)
- **Đau cái gì**: Bị "mù thông tin" về chất lượng vi mô — không biết học viên gặp misconception ở module nào, dẫn đến tỷ lệ drop-out/rớt cao (25-30%) và không thể can thiệp kịp thời
- **Con số**: 500 học viên × 25% = ~125-150 học viên drop-out/fail mỗi khóa; phát hiện vấn đề bị delay 1-2 tháng sau khóa → quá muộn

**Slide layout**:
```
[PROBLEM & USER]

Stakeholder: Program Manager / Head of Operations
Quy mô: 500 học viên/khóa
Hiện tại: Chỉ thấy con số rớt/đậu cuối khóa → không biết điểm mù ở đâu

Pain:
• 25-30% drop-out/rớt (125-150 học viên)
• Phát hiện vấn đề bị delay 1-2 tháng (sau khóa)
• PM không thể can thiệp giữa khóa

Root cause: Không có cơ chế tổng hợp & phân tích misconception ở tầm 500 người
```

**Ai nói**: [Người 1 — phụ trách Problem Framing]

---

### **SLIDE 2: Quick Win Selection**
*Từ: 01-frame/2-quick-win.md*

**Thông điệp**: 
- **Tại sao chọn UC5** (không chọn UC1/UC2/UC4): Rủi ro thấp nhất (công cụ nội bộ), impact cao nhất (khai phá dữ liệu hệ thống), evidence nhanh (2 tuần proof-of-concept)
- **Lựa chọn**: AI chạy ngầm trên dữ liệu bài làm lịch sử của 1 module → gắn thẻ misconception phổ biến → xuất Dashboard cho PM

**Slide layout**:
```
[QUICK WIN SELECTION — UC5]

Từ 5 use case, chọn UC5 vì:

Risk vs Impact matrix:
✓ UC2 (chấm điểm): Impact cao nhưng Risk cao (học viên phản ứng nếu sai)
✗ UC1 (sinh câu): Impact thấp (nice-to-have)
✓ UC5 (Dashboard): Impact cao + Risk thấp (nội bộ)

Quick Win chốt: AI phân tích bài làm lịch sử → gắn thẻ misconception → Dashboard cho PM

Lợi ích: An toàn (nội bộ tool) + Nhanh (2 tuần) + Rõ (insight ngay)
```

**Ai nói**: [Người 1 hoặc 2]

---

### **SLIDE 3: Solution Approach + Visual Flow**
*Từ: 02-solution/2-FINAL-solution.md*

**Thông điệp**:
- **Cách làm**: **Boost** — Gemini 1.5 Pro API + RAG (Handbook Day 28) + Few-shot Prompting
- **Vì sao Boost**: Không phải core competency (tự build lãng phí); Buy không cho phép tùy biến → Boost tối ưu (chi phí, tốc độ, control)
- **Flow**: Input (bài làm) → Gemini API (phân tích + gắn thẻ) → JSON (score + misconception + citation) → Dashboard (UI + CSV export)

**Slide layout**:
```
[SOLUTION: BOOST APPROACH]

Vì sao Build/Buy/Boost?
┌──────────────────────────────────┐
│ Giải pháp này có phải           │
│ core AI engine không? → KHÔNG    │
│                                  │
│ → Productivity layer (Boost)     │
│ → Dùng LLM API có sẵn           │
└──────────────────────────────────┘

Tech Stack (Chi phí: ~$25):
  1. Input: CSV 300 bài làm (ẩn danh)
  2. API: Gemini 1.5 Pro (reasoning mạnh)
  3. Data: RAG + Handbook D28 (knowledge)
  4. Output: Dashboard (CSV + Streamlit UI)

Luồng dữ liệu:
  Bài làm → [Gemini 1.5 Pro + RAG + Few-shot]
       → JSON (score + misconception + citation)
       → Dashboard (tần suất lỗi + trend)
       → PM dùng → can thiệp giáo trình
```

**Ai nói**: [Người 2 — phụ trách Solution]

---

### **SLIDE 4: AI Pilot Plan — Timeline & People**
*Từ: 03-pilot-plan/1-pilot-plan.md — mục 3, 4, 7*

**Thông điệp**:
- **Scope**: 1 module (D28), ~80 học viên, **3 tuần** (14 ngày làm việc)
- **Timeline**: 4 phases với 4 gates → decide approval/stop tại mỗi gate
- **Người & dữ liệu**: Engineer + QA làm; Lead Instructor review (16h); PM sponsor; dữ liệu = 300 bài lịch sử

**Slide layout**:
```
[AI PILOT PLAN — 3 WEEKS, 4 GATES]

Timeline:
  Week 1 (Ngày 1-7):
    Phase 0 (Ngày 1-3): Setup dữ liệu + Rubric + prompt
        ↓ [GATE 0: Instructor approve]
    Phase 1 (Ngày 4-7): Calibration trên 30 bài mẫu
        ↓ [GATE 1: Calibration ≥85% + Hallucination 0%]
  
  Week 2 (Ngày 8-11):
    Phase 2 (Ngày 8-11): Batch chạy 300 bài → sinh Dashboard
        ↓ [GATE 2: QA spot-check + Coverage ≥95%]
  
  Week 3 (Ngày 12-14):
    Phase 3 (Ngày 12-14): Demo + PM review + final sign-off
        ↓ [GATE 3: Head of Operations approval]

Người:
  • Engineer + QA: Code & test
  • Lead Instructor (16h): Calibration review — CRITICAL người này
  • PM (2h × 2): Requirement + feedback
  • Coach: Support

Dữ liệu:
  • 300 bài làm ngắn (ẩn danh)
  • Handbook + Rubric (15 mẫu)
```

**Ai nói**: [Người 3 — phụ trách Pilot Plan]

---

### **SLIDE 5: Metrics, Exit Criteria, & Clear Ask**
*Từ: 03-pilot-plan/1-pilot-plan.md — mục 8, 9, 12*

**Thông điệp**:
- **Đo cái gì**: 5 SMART metrics (Calibration, Hallucination, Time-to-Insight, Usability, Coverage)
- **Dừng khi nào**: ≥2 mức exit criteria (Warning vs Critical) — AI hallucination = 0% là automatic STOP
- **Xin gì + Hứa gì**: **CLEAR ASK** — $25 budget + dữ liệu + 16h Instructor = Dashboard <24h + PM adoption

**Slide layout**:
```
[METRICS, EXIT CRITERIA, & CLEAR ASK]

Metrics (SMART):
┌────────────────────────────────────────────┐
│ Metric              │ Ngưỡng  │ Ai đo    │
├────────────────────────────────────────────┤
│ Calibration Rate    │ ≥85%    │ Instructor
│ Hallucination       │ 0%      │ Coach     │
│ Time-to-Insight     │ <24h    │ Engineer  │
│ Dashboard Usability │ ≥80% PM │ PM        │
│ Coverage            │ ≥95%    │ Engineer  │
└────────────────────────────────────────────┘

Exit Criteria:
  🟡 WARNING: Calibration < 85% → Fix & retry
  🔴 CRITICAL: Hallucination > 0% → DỪNG NGAY
            Calibration ≤ 70% (sau 2 lần fix) → DỪNG NGAY

Clear Ask:
  ✓ Budget: $25 (API Gemini)
  ✓ Data: 300 bài CSV (ẩn danh)
  ✓ Nhân lực: Lead Instructor 16h review
  ✓ Access: API keys + Handbook files

Lời hứa:
  → PASS: Dashboard <24h, support 2h/week scaling
  → FAIL: Dừng ngay, report root cause, propose alternative
```

**Ai nói**: [Người 3]

---

## Phần B — Chuẩn bị 3 câu phản biện (Business owner/Instructor sẽ hỏi)

### **Câu hỏi 1: "Số liệu / giả định này lấy ở đâu?"**

**Câu trả lời sẵn:**
```
Phân tích từng con số:

• "500 học viên" — Từ context khóa AI20k (công khai, handbook)
• "25-30% drop-out/rớt" — Giả định từ quy mô cohort Day 28 & pattern từ các khóa trước
  (Nếu hỏi deeper: "Bạn có data cụ thể không?" → "Chưa có, nhưng có thể verify tuần 1 Phase 0")
• "3 phút/bài × 500 = 25 giờ" — Từ tính toán TA workload (phỏng vấn TA, nhận xét từ Coach)
• "300 bài lịch sử" — Dữ liệu có sẵn của cohort trước (xin PM cấp)
• "$0.01/bài API" — Giá public của Gemini 1.5 Pro API (tính toán: 300 × $0.01 × 3 lần calibration + 1 lần batch = ~$12)
• "Calibration ≥85%" — Benchmark từ auto-grading research paper (citation: nếu có) + industry standard
• "Hallucination = 0%" — Constraint do khóa AI20k yêu cầu (Human Review constraint)

Tóm lại: Số liệu mix giữa dữ liệu thực (500 học viên, $0.01/bài, 300 bài lịch sử) + giả định cần verify 
(drop-out 25-30%, Instructor 16h sẵn sàng). Sẽ validate ngay Ngày 1 Phase 0.
```

---

### **Câu hỏi 2: "Nếu giả định quan trọng nhất của bạn sai thì sao?"**

**Câu trả lời sẵn:**
```
Top 3 giả định rủi ro cao + contingency:

1️⃣ Data sạch (300 bài không corrupt, format OK)
   → Nếu sai: Mất 2-3 ngày data cleaning → delay Phase 1
   → Plan: Validate data format Ngày 1 Phase 0 (spot-check 10 bài)
   → Nếu error > 5%, báo sơ bộ + extend Phase 0 +2 ngày
   → Nếu error > 20%, escalate → xin dữ liệu thay thế

2️⃣ Gemini 1.5 Pro đủ mạnh cho misconception reasoning (accuracy ≥60% từ lần đầu)
   → Nếu sai: Model quá general → accuracy < 60% → cần fine-tune
   → Plan: Benchmark trên 10 bài mẫu Ngày 2 Phase 0 (không chờ đến Phase 1)
   → Nếu accuracy < 60%, pivot ngay sang Claude 3.5 / GPT-4o (chi phí +$5)
   → Chạy lại benchmark 1 ngày

3️⃣ Lead Instructor có 16 giờ để review (không bị busy với công việc khác)
   → Nếu sai: Review bị block 1-2 tuần → pilot delay hoàn toàn
   → Plan: Calendar commitment TRƯỚC (lên lịch 4 slots × 4h cụ thể)
   → Nếu Instructor báo bận, escalate ngay cho Head of Ops → tìm Co-Lead

Kết luận: Có 3 checkpoint sớm (Ngày 0, 1, 2) để phát hiện sai sớm nhất.
```

---

### **Câu hỏi 3: "Tình huống nào sẽ khiến bạn dừng pilot?"**

**Câu trả lời sẵn:**
```
Exit Criteria — 2 mức (đã định trước):

🟡 WARNING → Không dừng, fix lại:
  • Calibration Rate < 85% ở Phase 1
    → Sửa prompt + rubric + Few-shot examples
    → Chạy lại trên 30 bài mẫu
    → Nếu vẫn < 85%, tiếp tục lên CRITICAL

🔴 CRITICAL → DỪNG NGAY:
  • Hallucination Rate > 0% (AI bịa tài liệu)
    → Dừng ngay, KHÔNG tiếp tục
    → Báo cáo root cause cho Head of Operations
    → Đề xuất Quick Win khác (VD: UC2 — chấm điểm cho học viên, rủi ro kiểm soát hơn)
  
  • Calibration Rate ≤ 70% dù đã sửa prompt 2 lần
    → Dừng, không chạy Phase 2-3
    → Kết luận: Model hiện tại không phù hợp
  
  • PM feedback sau Phase 3: "Dashboard không hữu ích / không thể dùng"
    → Không approve scaling
    → Pivot sang approach khác

Người có quyền dừng:
  • WARNING: Lead Instructor (có thể sửa + retry)
  • CRITICAL: Head of Operations (quyết định tối hậu)

Khác biệt với proposal khác: Chúng tôi cam kết DỪNG nếu criteria fail, 
không kéo dài vì "sếp muốn cố gắng tiếp".
```

---

## Phần C — AI Support Log

| Câu hỏi | Trả lời |
|---|---|
| **AI giúp được gì trong lab này?** | AI giúp draft 12 mục AI Pilot Plan (tóm vấn đề, cách làm, scope, người, data, budget, timeline, metrics, exit criteria, adoption, lời hứa, lời xin) dựa trên thông tin từ Problem Framing + Solution Approach files. AI giúp tổ chức logic thành bảng chi tiết (timeline gates, metrics SMART, budget breakdown) và đưa ra gợi ý về contingency planning (3 giả định rủi ro cao). Nhóm sử dụng AI như "sounding board" để validate logic, không phải copy-paste. |
| **AI đưa output nào nghe hợp lý nhưng nhóm phải sửa?** | AI draft ban đầu đưa ra timeline 2 tuần, nhưng nhóm sửa lại thành 3 tuần vì lý do thực tế: Instructor có thể bận, data cleaning có thể mất thêm thời gian. AI cũng draft "exit criteria chỉ 1 mức" (CRITICAL dừng), nhưng nhóm thêm mức WARNING để cho phép fix lại 1 lần. AI draft budget gộp "nhân lực vào 1 cục", nhóm tách rõ: $10 API + $0 infra + $800 nhân lực nội bộ để transparency. |
| **Phần nào nhóm tự lập luận, KHÔNG copy AI?** | (1) Lý do chọn UC5 (rủi ro thấp, impact cao, internal tool) — nhóm tự phân tích từ Quick Win scoring matrix. (2) Contingency cho 3 giả định rủi ko (data validation Day 1, model benchmark Day 2, calendar commitment beforehand) — nhóm tự lên kế hoạch từ kinh nghiệm TA work. (3) Adoption plan (Tier 1 PM + Giáo viên → Tier 2 Coaches) — nhóm tự suy nghĩ phạm vi pilot nhỏ, không scale cùng lúc. (4) Lời hứa FAIL case (nếu hallucination > 0%, dừng ngay + đề xuất UC2) — nhóm tự thấy trách nhiệm là phải chấp nhận dừng thay vì bao che. |

---

## Tổng kiểm tra trước khi nộp

| Hạng mục | Xong? | Ghi chú |
|---|---|---|
| 5 slide, mỗi slide 1 thông điệp, đã phân ai nói slide nào | ✓ | Slide 1-2: Người 1 · Slide 3: Người 2 · Slide 4-5: Người 3 |
| Slide 5 có lời xin rõ ràng (xin gì · hứa gì) | ✓ | Xin: $25 + data + 16h Instructor · Hứa: Dashboard <24h + adoption |
| Có câu trả lời sẵn cho cả 3 câu phản biện | ✓ | Q1 (số liệu), Q2 (giả định sai), Q3 (dừng khi nào) |
| AI Support Log điền đủ 3 dòng | ✓ | AI role · AI output sửa lại · Nhóm tự lập luận |
| Pitch sẵn sàng nộp (5 phút + 3 câu Q&A + log) | ✓ | Ready for Gate 5 presentation |

---

## Hướng dẫn Presentation (Gate 5)

### **Cấu trúc 5 phút Pitch:**
- **Slide 1 (Problem)**: 1 phút — Giới thiệu vấn đề (ai, đau gì, con số)
- **Slide 2 (Quick Win)**: 30 giây — Tại sao chọn UC5
- **Slide 3 (Solution)**: 1 phút — Boost approach + flow
- **Slide 4 (Plan)**: 1.5 phút — Timeline + gates + người
- **Slide 5 (Metrics + Ask)**: 30 giây — Metrics + exit criteria + lời xin rõ ràng

### **Sau pitch 5 phút — Q&A (3–5 phút):**
- Business owner / Instructor hỏi 1–2 câu từ Phần B
- Nhóm trả lời bằng câu trả lời đã chuẩn bị (hoặc tương tự logic)

### **Đánh giá theo Gate 5 Rubric:**
- ✓ Vấn đề rõ ràng + có con số
- ✓ Quick Win justified (không chọn theo cảm giác)
- ✓ Solution specific (Boost, không Build/Buy mơ hồ)
- ✓ Plan realistic (timeline + gates + exit criteria)
- ✓ Metrics SMART (có baseline, ngưỡng, ai đo)
- ✓ **Lời xin clear** (xin gì đổi lại hứa gì)
- ✓ Team ready (biết trả lời phản biện)

---

## Checklist Nộp Cuối (Before submitting to Discord)

**File worksheet/ cần đã committed + pushed:**
- [ ] 00-context.md — Filled track info
- [ ] group-members.md — Filled member names + roles
- [ ] 01-frame/3-FINAL-problem-framing.md — ✓ (hoàn thiện)
- [ ] 02-solution/2-FINAL-solution.md — ✓ (hoàn thiện)
- [ ] 03-pilot-plan/1-pilot-plan.md — ✓ (hoàn thiện)
- [ ] 03-pilot-plan/2-FINAL-pitch.md — ✓ (hoàn thiện)

**GitHub actions:**
```bash
git add worksheet/
git commit -m "Day28-lab: AI Pilot Plan — Final submission (Problem Framing + Solution + Pilot Plan + Pitch)"
git push origin main
```

**Discord post** (include link + summary):
```
📌 Day 28 Lab: AI Pilot Plan — Tự động phát hiện misconception ở quy mô 500 học viên

🔗 GitHub: [paste link to worksheet folder]

📊 Summary:
- Vấn đề: PM mù thông tin about misconception → 25-30% drop-out
- Cách làm: Boost (Gemini API + RAG) — $25 — 3 tuần
- Metric: Calibration ≥85% + Hallucination 0% + Time-to-Insight <24h
- Xin: Budget $25 + data + 16h Instructor
- Hứa: Dashboard <24h + PM adoption (hoặc dừng nếu fail)

🎯 Ready for Gate 5: 5-min pitch + Q&A
```

---

## Tài liệu tham khảo

- **Handbook**: §A7 (Pilot Planning) + §A8 (Metrics & Exit Criteria) + §A9 (Pitch & Presentation)
- **Templates**: `templates/5-slide-pitch.md` · `templates/ai-pilot-plan-core.md` · `templates/ai-support-log.md`
- **Rubric**: `templates/rubric-gate-sheet.md` (5 gates: Problem → Quick Win → Solution → Pilot Plan → Pitch)

---

**Lab này là câu chuyện hoàn chỉnh**: 
1. ✓ Problem Framing (vấn đề thật, con số rõ)
2. ✓ Quick Win (UC5: không chọn theo cảm giác)
3. ✓ Solution (Boost: có lý do tại sao)
4. ✓ Pilot Plan (xin gì, hứa gì, đo gì, dừng khi nào)
5. ✓ Pitch (dồn thành 5 slide + ready for Q&A)

**Key differentiation**: 
- Không phải "proposal xin tiền mà không rõ approve cái gì"
- Là "cam kết hai chiều": nhóm xin resource, đổi lại hứa giao evidence + chấp nhận dừng nếu metric fail
- Demo đơn giản nhưng lập luận chặt → quyết định rõ ràng

Lịch submit: Theo deadline khóa. Đảm bảo file đã push GitHub + link dán Discord trước giờ pitch chính thức.
