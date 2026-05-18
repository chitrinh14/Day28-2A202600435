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

1. **Tóm vấn đề** (1 câu, từ Problem Framing): [...]
2. **Cách làm + lý do** (từ 02-solution, 1 câu): [...]
3. **Scope pilot**: phục vụ ai · bao nhiêu người · bao lâu · mấy phase: [...]
4. **Người**: nhóm làm · ai review output rủi ro cao · ai có quyền quyết approve/dừng: [...]
5. **Data**: dùng data gì (mẫu/giả định) · cơ chế privacy/citation: [...]
6. **Budget** (tách hạng mục): API/tool [...] · thời gian người [...] · hạng mục ẩn (training, maintenance) [...]
7. **Timeline + cổng giữa phase**: Phase 1 (… tuần) … → cổng … · Phase 2 … : [...]
8. **Metrics** (SMART + baseline + ngưỡng + ai đo):

| Metric | Đo bằng gì · ai đo | Baseline | Ngưỡng đạt |
|---|---|---|---|
| | | | |
| | | | |

   Leading indicator (biết kết quả sớm trong 1–2 tuần): [...]

9. **Exit criteria** (định trước, ≥2 mức):

| Mức | Điều kiện | Hành động | Ai có quyền dừng |
|---|---|---|---|
| Cảnh báo | | theo dõi / tối ưu | |
| Nghiêm trọng | | dừng pilot | |

   *Liên hệ 2 Red Flag ở `00-context.md`: exit criteria có chặn được chúng không?*

10. **Adoption** (tool không ai dùng = $0): ai dùng đầu tiên · workflow đổi ở đâu · ai train/support · nếu không ai dùng thì sao: [...]

---

## Tự phản biện

- Budget thiếu hạng mục ẩn nào không?
- Exit criteria đủ mạnh để THẬT SỰ dừng, hay chỉ trên giấy?
- Giả định quan trọng nhất sai → plan gì?

---

## Tổng kiểm tra trước khi sang `2-FINAL-pitch.md`

| Hạng mục | Xong? |
|---|---|
| Tóm vấn đề trong 1 câu | / |
| Budget tách hạng mục, không "miscellaneous" | / |
| Metric có baseline + ngưỡng + ai đo | / |
| Exit criteria có người có quyền thực thi (≥2 mức) | / |
| Adoption: chỉ rõ ai dùng đầu tiên (không "cả khóa") | / |

⚑ Coach kiểm tra ở Mốc 4: *"Xin gì? Hứa gì? Đo gì? Dừng khi nào?"*

Sau bước này, mở `2-FINAL-pitch.md` — dồn tất cả thành 5-slide pitch + AI Support Log.

*Liên quan: handbook §A7+§A8 · `templates/ai-pilot-plan-core.md` · `prompts/06-pilot-plan-challenge.md`*
