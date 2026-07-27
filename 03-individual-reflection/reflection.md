# 03 — Individual Reflection

Học viên: **Vũ Hữu An — 2A202601078**

## Tôi đã tham gia vào phần nào?

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| Scan cá nhân | Scan 8 problems từ 3 bối cảnh (research AI, cộng đồng AI builder, nhóm/cá nhân), có số liệu thật (2-3h/ngày đọc paper, 3-5 lần/ngày lướt Discord) | Nhóm có thêm cluster "gom thông tin / planning cá nhân" với 4 candidates |
| Pitch Problem Card | Pitch cả top 3: đọc paper, lọc tin Discord, lập kế hoạch ngày/tuần | 2 bài vào cluster B; nhóm cuối cùng chọn bài khác (IT Help Desk) — tôi chấp nhận vì tiêu chí score rõ ràng |
| Challenge bài của bạn khác | Hỏi Phương lấy giá realtime Grab/Be từ đâu; hỏi Việt về độ đầy đủ dữ liệu lịch sử ngập; hỏi lại nghi ngại của Nghĩa về việc BPI 2013 có đủ text mô tả ticket không | Nhóm thấy rõ 2 bài thiếu data access hợp lệ; nghi ngại về BPI 2013 được đưa thành điều kiện kiểm tra đầu tiên của pilot |
| Gom trùng / cluster | Đề xuất gom 15 candidates thành 6 clusters theo pattern | Nhóm nhìn ra cluster A (ticket triage) có 2 người độc lập xếp #1 |
| Chọn candidate problem | Đề xuất bảng score 7 tiêu chí, chấm cùng nhóm | Chọn được IT Help Desk bằng lý do, không phải vote cảm tính |
| Validation / research | Tìm và kiểm 4 nguồn: Zendesk Intelligent Triage, ServiceNow Predictive Intelligence, Freshservice Field Suggester, dataset BPI 2013 | Nhóm thấy pattern chung "AI đề xuất — người quyết ca không chắc", không cần phát minh kiến trúc mới |
| Workflow nhóm | Tổng hợp workflow before (7 bước) / after (5 bước, confidence threshold + human boundary + fallback) | Thành workflow bản cuối trong group report và slide |
| Problem Statement | Soạn v0 và v1, tách rõ metric và boundary | PS v1 có điểm chèn AI, mức chọn và người kiểm rõ |
| Rule / Workflow / Agent | Lập luận chọn Workflow; dùng chính nghi ngại thiếu KB data để loại Agent | Nhóm thống nhất chọn Workflow, giữ Rule cho subset ticket mẫu rõ |
| Decision | Đề xuất cách hiểu "Go = go làm pilot đo lường, không phải go deploy" | Quyết định Go với scope nhỏ, có exit/rollback rõ |

## Bảng dùng AI trong reflection

Tôi dùng AI (Claude Code) xuyên suốt lab. Bảng dưới ghi trung thực AI giúp gì, sai/hời hợt ở đâu, và tôi đã sửa gì bằng nhận định của mình.

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| Scan | AI đặt câu hỏi khai thác theo 4 lăng kính, tôi trả lời từ trải nghiệm thật | Ép tôi đưa ra con số cụ thể (2-3h/ngày, 15-20'/lần) thay vì mô tả chung chung | AI đề xuất top 3 có "Recap sau họp" và khuyên tôi pitch card #1 (đọc paper) | Tôi đổi vị trí #3 thành "Lập kế hoạch" và chọn pitch card #3 vì đó là pain nền của tôi — AI recommend khác nhưng quyết định là của tôi |
| Problem Card | AI dựng card từ câu trả lời của tôi theo đúng template | Không sót field; workflow trước/sau có bottleneck và fallback rõ | Thời gian chia nhỏ từng bước (đọc hiểu 60-90', lướt 7-10'/lần) là AI ước lượng từ tổng số tôi cho | Tôi kiểm lại từng con số; yêu cầu đánh dấu rõ đâu là giả định cần đo lại |
| Workflow | AI vẽ workflow ASCII before/after cho cả bài cá nhân và bài nhóm | Nhanh, thể hiện được human boundary và fallback | Ban đầu chưa nhấn đủ rằng chi phí thật nằm ở hậu quả reassign chứ không phải phút phân loại | Tôi tự kiểm từng bước, xác nhận bottleneck đặt đúng chỗ (bước 3-4, hậu quả ở bước 5) |
| Research | AI search và đề xuất 4 nguồn kèm link | Link đều là tài liệu chính thức, tự kiểm được | Kết quả search kèm số liệu vendor (kiểu "giảm 60-70% triage") không kiểm chứng được nguồn gốc | Chỉ giữ mô tả tính năng có trong tài liệu chính thức; loại toàn bộ số liệu không verify được khỏi report |
| Problem Statement | AI draft PS v0/v1 từ nội dung nhóm đã chốt | Boundary và success metric viết chặt, có baseline và cách đo | AI viết sẵn kế hoạch validation kèm bảng chờ điền — dễ tạo cảm giác nhóm "sắp làm" trong khi thực tế không kịp | Tôi sửa thẳng phần 4.1 thành "nhóm chưa thể khảo sát trong thời gian lab" — thà ghi trung thực còn hơn để bảng trống giả vờ |
| Rule / Workflow / Agent | AI lập luận so sánh 3 mức | Biết dùng chính nghi ngại của Nghĩa (dataset thiếu KB article) làm lý do loại Agent, không loại theo cảm tính | Không đáng kể ở phần này | Tôi đối chiếu lại với ma trận mơ hồ × phức tạp của worksheet trước khi đồng ý |
| Decision | AI đề xuất Go với scope nhỏ + điều kiện exit/rollback | Định nghĩa lại "Go = go pilot đo lường" giải quyết được mâu thuẫn với 2 câu "Not Yet" | Không đáng kể | Tôi giữ nguyên vì đúng tinh thần "không cần AI vẫn là kết luận tốt" của lab |
| Slide | AI dựng slide deck HTML từ group report | Tự kiểm tra render từng slide trước khi giao | Bản đầu ôm cả phần hội tụ/score làm loãng trọng tâm | Tôi yêu cầu cắt còn 8 slide, chỉ tập trung vào bài IT Help Desk |
| Reflection | AI gợi ý câu hỏi tự soi và cấu trúc lại câu trả lời của tôi | Giúp tôi không bỏ sót mục theo template | — | Nội dung trải nghiệm, bài học và lựa chọn trong file này là của tôi; AI chỉ giúp cấu trúc |

## Reflection câu hỏi mở

**Tôi học được gì khi nghe top 3 của các bạn khác?**

15 bài toán tưởng rất khác nhau nhưng rơi vào 6 pattern. Bài "Lập kế hoạch" của tôi trùng pattern với bài "Sót task" của Hải — nghĩa là pain đó phổ biến thật, nhưng cũng vì nó gắn với thói quen từng người nên baseline rất khó đo. Ngược lại, bài của Nghĩa nghe "khô" hơn nhưng có dataset và ground truth — và đó chính là thứ quyết định bài nào làm được trong lab.

**Nhóm có lúc nào bị solution-first không?**

Có nguy cơ ở chỗ AI: khi tôi nhờ AI gợi ý, nó có xu hướng đề xuất giải pháp nghe hợp lý rất nhanh (ví dụ khuyên tôi pitch bài đọc paper vì "metric mạnh nhất"). Nhóm giữ được problem-first nhờ bảng score 7 tiêu chí — mọi lựa chọn phải nói được lý do bằng tiêu chí, không phải bằng độ "ngầu" của solution.

**Tôi có thay đổi ý kiến sau khi bị challenge không?**

Có. Bài tôi muốn pitch nhất (Lập kế hoạch) không được chọn vì đúng điểm yếu tôi đã tự ghi trong Problem Card: baseline khó đo do tôi không plan đều. Khi tiêu chí "impact đo được" được đặt lên bàn, tôi chấp nhận bài của mình xếp sau — và thấy đó là cách chọn đúng.

**Tôi đóng góp gì thật sự vào artifact cuối?**

Phần cluster + bảng score, research 4 nguồn có link kiểm được, tổng hợp group report, và ba câu challenge (data giá xe, dữ liệu ngập, text trong BPI 2013) — câu cuối trở thành điều kiện kiểm tra đầu tiên của pilot.

**Điều khó nhất khi viết Problem Statement là gì?**

Success metric. Viết "nhanh hơn, tốt hơn" thì dễ; viết được "% ticket đúng team ngay lần đầu, đo trên BPI 2013, so với ground truth là team đã thực sự xử lý" mới khó — và phải chấp nhận ghi "Not Yet" cho những gì chưa đo được thay vì bịa baseline.

**Nếu làm lại, tôi sẽ đổi gì?**

```text
Hai việc. Một: đo baseline cá nhân trước khi ước lượng — các con số 2-3h/ngày
của tôi là nhớ lại, không phải đo; lần sau tôi sẽ log thời gian thật vài ngày
trước lab. Hai: khảo sát/validate song song từ đầu thay vì để cuối — nhóm đã
phải ghi "chưa thể khảo sát trong thời gian lab" ở phần 4.1, trung thực nhưng
đáng lẽ tránh được nếu chia người làm validation ngay khi chốt candidate.
```

## Bài học chính của tôi

- **Problem trước, AI sau.** Bài toán tốt không phải bài "nghe AI" nhất trong 15 candidates, mà là bài có actor, workflow, metric và data đo được. Bài dự báo ngập có impact xã hội lớn nhất nhưng vẫn bị loại — vì không làm được trong lab.
- **Rule/Workflow đủ tốt là lựa chọn tốt.** Nhóm không chọn Agent dù nghe "ngầu" hơn: thiếu KB data, rủi ro trả lời sai trực tiếp user, và bottleneck đo được nằm ở triage. Chọn Workflow với ngưỡng confidence là chọn theo bài toán, không phải theo công nghệ.

## Tự kiểm cuối bài

- [x] Cá nhân có 5+ problems (8 problems) và top 3 Problem Cards.
- [x] Tôi đã pitch cả top 3 và challenge 3 bài của các bạn đúng trọng tâm data/scope.
- [x] Nhóm có nhật ký hội tụ từ 15 candidates về 1 bài.
- [x] Nhóm có workflow trước/sau.
- [x] Nhóm có Problem Statement v0/v1 với metric và boundary rõ.
- [x] Nhóm có so sánh No AI / Rule / Workflow / Agent.
- [x] Nhóm có quyết định Go (với scope nhỏ) và lý do rõ.
- [x] Reflection nói rõ vai trò trong nhóm, cách dùng AI, điều học được và nếu làm lại sẽ đổi gì.
- [x] Tôi tự giải thích được mạch: pain triage → workflow 7 bước nghẽn ở phân loại/định tuyến → metric % đúng team lần đầu → boundary AI không tự resolve → Workflow là mức phù hợp vì output có ground truth.

---

*03 — Individual Reflection — Day 02 Lab*
