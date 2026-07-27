# Group Report — Day 02

## Thành viên nhóm

| STT | Họ và tên | Mã học viên | Vai trò trong nhóm |
|-----|-----------|-------------|--------------------|
| 1   | Vũ Hữu An | 2A202601078 | Tổng hợp report, cluster + scoring, research giải pháp |
| 2   | Nguyễn Trần Nghĩa | 2A202601664 | Đề xuất bài IT Help Desk, cung cấp hiểu biết dataset BPI 2013 |
| 3   | Lê Đình Việt | 2A202601528 | Đề xuất cluster dự báo môi trường, challenge về data access |
| 4   | Tô Ngọc Hải | 2A202601686 | Đề xuất bài ticket tagging, góp ý confidence threshold |
| 5   | Lê Thanh Phương | 2A202501658 | Đề xuất cluster so sánh giá, challenge về tính khả thi trong lab |

---

## Bước 3.1 — Trình bày top 3 (15 candidates)

| # | Người đưa ra | Candidate problem | Người gặp vấn đề | Điểm nghẽn | Cảm nhận nhanh |
|---|---|---|---|---|---|
| 1 | An | Đọc/tóm tắt 3-5 paper AI mỗi ngày (2-3h/ngày) | Sinh viên research AI | Đọc hiểu approach + thuật ngữ | Metric rõ, domain hẹp theo từng người |
| 2 | An | Lọc tin WS/OH/tài liệu trên Discord cộng đồng AI builder | Thành viên cộng đồng | Lọc tin liên quan giữa nhiều tin | Pain chung, cần data access Discord |
| 3 | An | Lập kế hoạch ngày/tuần từ nhiều nguồn việc | Sinh viên đa nhiệm | Gom việc + sắp ưu tiên | Pain nền, baseline khó đo |
| 4 | Nghĩa | Phân loại, xử lý và định tuyến IT Help Desk ticket | Nhân viên service desk, người dùng nội bộ | Triage thủ công, ticket bị chuyển lòng vòng | Actor/workflow/metric rất rõ, có dataset |
| 5 | Nghĩa | Phân loại và định tuyến bug report | Dev team, QA | Gắn label/component/assignee thủ công | Gần giống #4, có dữ liệu văn bản |
| 6 | Nghĩa | Ưu tiên và điều phối xử lý lỗ hổng bảo mật | Security team | Nhiều nguồn (NVD, CISA), escalation | Hay nhưng thiếu asset inventory nội bộ |
| 7 | Việt | Dự báo điểm ngập trước khi xảy ra | Người đi đường, đô thị | Thiếu dữ liệu lịch sử đầy đủ | Impact lớn, vượt scope lab |
| 8 | Việt | Tự động tạo báo cáo thời tiết | Người đọc báo cáo | Lặp lại hằng ngày | Workflow rõ nhưng impact nhỏ |
| 9 | Việt | Đề xuất tuyến đường tránh ngập | Người đi đường | Cần dữ liệu giao thông realtime | Giá trị cao, data realtime khó |
| 10 | Hải | Phân loại và gắn thẻ ticket/phản hồi khách hàng | Support team | Đọc → phân loại → tag → assign thủ công | Trùng pattern với #4, #5 |
| 11 | Hải | Loay hoay chốt lịch họp chung | Nhóm làm việc | Trao đổi qua lại tìm khung giờ | Cần quyền truy cập lịch, privacy |
| 12 | Hải | Bị sót task và trễ deadline → Daily Briefing | Sinh viên, RA, người đa nhiệm | Task rải trên Email/Slack/Jira | Trùng pattern với #3 |
| 13 | Phương | So sánh giá xe công nghệ (Grab, Be, Xanh SM) | Người đặt xe | Mở 3-4 app so giá thủ công, 5-10'/lần | Pain thật, không có API giá công khai |
| 14 | Phương | So sánh giá thuốc & thực phẩm chức năng | Người mua thuốc | Tra giá từng website/gọi điện | Pain thật, data phân mảnh, khó verify |
| 15 | Phương | Viết email/tin nhắn công việc (15-20'/email) | Người đi làm | Nắn chỉnh câu chữ, giọng điệu | Tool có sẵn (Copilot/Gemini) đã giải khá tốt |

## Bước 3.2 — Gom trùng / cluster

| Cluster | Candidates included | Pattern chung | Ghi chú |
|---|---|---|---|
| A. Phân loại & định tuyến ticket | #4 IT Help Desk, #5 Bug report, #10 Ticket tagging, #6 Vulnerability triage | Đọc văn bản tự do → phân loại → định tuyến đến đúng người/team | 4 bài, trong đó 2 thành viên độc lập xếp hạng 1 |
| B. Gom thông tin / planning cá nhân | #1 Paper, #2 Discord, #3 Lập kế hoạch, #12 Sót task | Gom thông tin từ nhiều nguồn rời rạc → tổng hợp cho một người dùng | Pain cả nhóm tự trải nghiệm, nhưng data cá nhân phân mảnh |
| C. So sánh giá realtime | #13 Giá xe, #14 Giá thuốc | Gom giá từ nhiều nguồn đóng → so sánh realtime | Không có API công khai, khó demo trong lab |
| D. Dự báo môi trường | #7 Ngập, #8 Thời tiết, #9 Tuyến đường | Dự báo từ dữ liệu cảm biến/lịch sử | ML-heavy, dữ liệu khó, vượt scope lab |
| E. Soạn thảo văn bản | #15 Email | AI draft, người sửa | Tool thị trường đã giải tốt |
| F. Điều phối lịch | #11 Lịch họp | Truy cập lịch nhiều người → tìm slot | Nghẽn ở quyền truy cập + privacy, không phải ở AI |

## Bước 3.3 — Shortlist

Mỗi cluster mạnh lấy một đại diện:

| Candidate | Vì sao vào shortlist | Rủi ro / điều chưa rõ |
|---|---|---|
| IT Help Desk ticket (cluster A) | 2 thành viên độc lập xếp #1; actor + workflow chuẩn ITSM ai cũng vẽ được; có dataset công khai (BPI 2013); metric đếm được từ log | Dataset là event log, chưa chắc đủ nội dung text của ticket (Nghĩa đã chỉ ra) |
| Daily Briefing / sót task (cluster B) | Pain cả nhóm tự trải nghiệm; input/output rõ (nguồn task → briefing) | Baseline cá nhân khó đo chuẩn; nguồn task mỗi người một kiểu, khó generalize |
| So sánh giá xe công nghệ (cluster C) | Pain phổ biến, tần suất cao, ai cũng validate được ngay | Không có API giá công khai; scraping app là vùng xám; gần như không demo được trong lab |

## Bước 3.4 — Score để đồng thuận

Chấm 1-5 theo 7 tiêu chí của worksheet:

| Candidate | Actor rõ | Workflow rõ | Pain có evidence | Impact đo được | Làm trong lab | So sánh R/W/A được | Nhóm hiểu domain | Tổng |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| IT Help Desk ticket | 5 | 5 | 4 | 5 | 4 | 5 | 4 | **32** |
| Daily Briefing | 4 | 4 | 4 | 3 | 4 | 4 | 5 | 28 |
| So sánh giá xe | 5 | 4 | 4 | 4 | 2 | 3 | 4 | 26 |

Candidate nhóm chọn:

```text
Phân loại và định tuyến IT Help Desk ticket — thu hẹp vào bước TRIAGE:
đọc ticket mô tả tự do → phân loại category/priority → định tuyến đúng team
ngay lần đầu, để giảm ticket bị chuyển lòng vòng giữa các team ("ping-pong").
```

Vì sao chọn:

```text
- 2/5 thành viên độc lập cùng xếp hạng 1 → đồng thuận tự nhiên, không phải ép vote.
- Workflow chuẩn ITSM, actor rõ (nhân viên L1/dispatcher), vẽ before/after được ngay.
- Có dataset công khai (BPI Challenge 2013 — Volvo IT) để đo baseline mà không cần
  chờ quyền truy cập hệ thống nội bộ nào.
- Metric đếm được từ log: % ticket đúng team ngay lần đầu, % reassignment,
  thời gian triage.
- So sánh Rule / Workflow / Agent rất tự nhiên: keyword routing → classify với
  confidence threshold → agent tự resolve.
```

Vì sao không chọn các candidate còn lại:

```text
- Daily Briefing: pain thật và gần gũi, nhưng baseline cá nhân khó đo chuẩn,
  nguồn task mỗi người một kiểu → khó viết success metric chặt trong lab.
- So sánh giá xe: pain rất phổ biến nhưng không có API giá công khai,
  không có cách lấy data hợp lệ trong lab → điểm "làm trong lab" quá thấp.
- Dự báo ngập: impact xã hội lớn nhất nhưng là bài ML nặng về dữ liệu lịch sử,
  vượt hẳn scope một buổi lab.
- Viết email: tool thị trường (Copilot/Gemini) đã giải tốt, ít không gian lập luận.
- Lịch họp: nghẽn thật nằm ở quyền truy cập lịch và privacy, không phải ở AI.
```

Nếu có disagreement, nhóm xử lý thế nào:

```text
Dùng bảng score 7 tiêu chí để ép nói rõ lý do thay vì vote cảm tính; tiêu chí
"làm trong lab" và "impact đo được" là hai tiêu chí quyết định khi hai bài
ngang nhau về pain.
```

---

## Bước 4.1 — Quick validation

Nhóm chưa thể khao sát trong thời gian Lab

## Bước 4.2 — Research giải pháp đã có

| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| Zendesk Intelligent Triage | https://support.zendesk.com/hc/en-us/articles/4964463770650-About-intelligent-triage | Tự động phân loại ticket theo topic, sentiment, language, entity ngay khi ticket được tạo | Phân loại thành field trên ticket để workflow/routing dùng tiếp | Là sản phẩm đóng, gắn với hệ sinh thái Zendesk; vẫn cần người xử lý case khó | Pattern "AI phân loại thành field → rule/workflow route tiếp" đúng với hướng nhóm định làm |
| ServiceNow Predictive Intelligence | https://www.servicenow.com/standard/resource-center/data-sheet/ds-predictive-intelligence.html | ML học từ ticket lịch sử để đoán category, priority, assignment group | Học từ chính dữ liệu tổ chức, tích hợp thẳng vào ITSM flow | Cần lượng lớn ticket lịch sử chất lượng tốt để train | Baseline lịch sử là tài sản quan trọng nhất — đúng lý do nhóm chọn bài có dataset công khai |
| Freshservice Freddy AI — Ticket Field Suggester | https://support.freshservice.com/support/solutions/articles/240431-use-ticket-field-suggester-to-categorize-tickets | Gợi ý giá trị field (category, group, priority...) cho ticket mới, agent xác nhận | AI chỉ *gợi ý*, con người vẫn là người chốt field | Chất lượng gợi ý phụ thuộc dữ liệu quá khứ | Mức "AI đề xuất + người duyệt" là mức khởi điểm an toàn trước khi cho auto-route |
| BPI Challenge 2013 (Volvo IT — VINST) | https://ais.win.tue.nl/bpi/2013/challenge.html (dataset: https://data.4tu.nl/collections/_/5065448/1) | Event log thật của quy trình incident/problem management: 7.554 incidents, 65.533 events | Dữ liệu thật, công khai, có ground truth về team xử lý; chính đề bài nêu vấn đề ping-pong và giữ incident ở tuyến 1 | Là event log — cần kiểm tra có đủ nội dung text mô tả ticket cho bài classification không (nghi ngại của Nghĩa) | Dùng làm dataset đo baseline cho pilot; nếu thiếu text thì đổi sang bug report dataset (Bugzilla) làm proxy |

Research takeaway:

```text
Cả ba sản phẩm thương mại đều hội tụ về cùng một pattern: AI phân loại và đề xuất
định tuyến, quyết định cuối (nhất là auto-route) đi qua ngưỡng tin cậy hoặc con
người duyệt — không tool nào để AI tự đóng ticket. Nhóm không cần phát minh
kiến trúc mới: bài của nhóm là Workflow "classify → confidence threshold →
route hoặc đưa người review", đo được trên dataset công khai.
```

---

## Bước 5.1 — Current workflow bản nhóm

Workflow chuẩn ITSM (tham chiếu quy trình trong dataset BPI 2013 + kinh nghiệm của Nghĩa). Thời gian đánh dấu `(*)` là **giả định của nhóm, sẽ đo lại trong pilot**.

| Bước | Actor | Input | Output | Thời gian/tần suất | Ghi chú |
|---|---|---|---|---|---|
| 1. Gửi ticket | End user | Sự cố + mô tả tự do | Ticket trong hệ thống | Liên tục | Chất lượng mô tả rất không đều |
| 2. Đọc + hỏi lại nếu thiếu | L1/dispatcher | Ticket thô | Ticket đủ thông tin | Vài phút → hàng giờ chờ phản hồi (*) | Chờ user trả lời là dead-time |
| 3. Phân loại | L1 | Nội dung ticket | Category, impact, priority | 2-5 phút/ticket (*) | Dựa kinh nghiệm cá nhân, không đồng nhất giữa các L1 |
| 4. Định tuyến | L1 | Ticket đã phân loại | Ticket vào hàng đợi team | 1-2 phút (*) | Sai ở đây là gốc của mọi chi phí phía sau |
| 5. Reassign nếu sai team | Các team chuyên môn | Ticket sai chỗ | Ticket chuyển team khác | Cộng thêm hàng giờ → ngày chờ (*) | "Ping-pong" — hiện tượng được chính BPI 2013 nêu thành câu hỏi phân tích |
| 6. Xử lý | Kỹ thuật viên | Ticket đúng team | Giải pháp | Tùy sự cố | Ngoài scope bài này |
| 7. Đóng + phản hồi | Kỹ thuật viên | Giải pháp | Ticket đóng, user được báo | Vài phút | Ngoài scope bài này |

Bottleneck chính:

```text
Bước 3-4: triage thủ công dựa trên kinh nghiệm từng L1. Chi phí thật không nằm ở
vài phút phân loại, mà ở hậu quả khi phân loại/định tuyến sai: ticket bị đẩy
qua lại giữa các team (bước 5), mỗi lần đẩy cộng thêm thời gian chờ trong hàng
đợi mới, user chờ lâu hơn và SLA vỡ.
```

```text
CURRENT STATE — 7 bước, bottleneck ở triage

[1 User gửi ticket]
→ [2 L1 đọc + hỏi lại: phút→giờ]
→ [3 L1 phân loại: 2-5'/ticket]      <-- bottleneck (không đồng nhất)
→ [4 L1 định tuyến: 1-2']            <-- bottleneck (sai là gốc chi phí)
→ [5 Sai team → reassign: +giờ→ngày] <-- hậu quả đo được ("ping-pong")
→ [6 Team xử lý]
→ [7 Đóng ticket]
```

## Bước 5.2 — Future workflow bản nhóm

```text
FUTURE STATE — 5 bước, AI ở bước triage, người giữ quyền quyết định case không chắc

[1 User gửi ticket]
→ [2 AI trích xuất thông tin + phân loại category/priority
     + đề xuất team kèm confidence score: tự động, giây]      -- Workflow step
→ [3a Confidence ≥ ngưỡng → auto-route vào hàng đợi team]     -- Rule trên output AI
   [3b Confidence < ngưỡng → hàng đợi L1 review: 1-2'/ticket] <-- human boundary
→ [4 L1 audit mẫu ngẫu nhiên các ticket auto-route định kỳ]   -- human boundary
→ [5 Team xử lý; route sai → ghi nhận feedback để chỉnh model/ngưỡng]

Boundary:
- AI KHÔNG tự giải quyết ticket, KHÔNG tự trả lời user.
- Ticket nhạy cảm (security, VIP, pháp lý) LUÔN vào hàng đợi người review.

Fallback:
- Accuracy tụt hoặc route sai tăng → hạ ngưỡng auto-route (nhiều ticket qua
  người hơn), tệ nhất tắt auto-route → quay về triage thủ công như cũ.
```

Before/after impact:

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---|---|---|
| Số bước | 7 | 5 | Bước hỏi lại giảm nhờ AI trích xuất; bước reassign giảm tần suất |
| Bước thủ công | 7/7 | 2/5 | Người chỉ còn review case không chắc + audit mẫu |
| Thời gian triage/ticket | 2-5' (*) mọi ticket | Giây (auto) hoặc 1-2' (review) | (*) giả định, đo lại trong pilot |
| % ticket đúng team ngay lần đầu | Baseline đo từ dataset trong pilot | Cao hơn baseline | Metric chính |
| % ticket bị reassign (ping-pong) | Baseline đo từ dataset trong pilot | Giảm | Metric chính |
| Bottleneck chính | Triage thủ công | L1 review case không chắc | Bottleneck mới chấp nhận được — là điểm kiểm soát chất lượng |
| Risk mới | Không có | AI phân loại sai, model drift | Cần ngưỡng confidence + audit định kỳ |

## Bước 5.3 — Problem Statement v0

| Field | Nội dung |
|---|---|
| **Actor** | Nhân viên L1/dispatcher tại service desk của tổ chức lớn, chịu trách nhiệm phân loại và định tuyến ticket đến đúng team chuyên môn. |
| **Workflow** | User gửi ticket mô tả tự do → L1 đọc, hỏi lại nếu thiếu → phân loại category/priority → định tuyến team → nếu sai team thì reassign → team xử lý → đóng ticket. |
| **Bottleneck** | Triage thủ công dựa kinh nghiệm từng L1; định tuyến sai làm ticket bị đẩy qua lại giữa các team, mỗi lần đẩy cộng thêm thời gian chờ. |
| **Impact** | Ticket chậm được xử lý thêm hàng giờ đến ngày; user chờ lâu; SLA vỡ; L1 tốn thời gian vào việc phân loại lặp lại. Hiện tượng ping-pong được nêu trong chính đề bài BPI Challenge 2013. |
| **Success Metric** | Tăng % ticket đến đúng team ngay lần đầu; giảm % ticket bị reassign; giảm thời gian triage/ticket. Baseline đo trên dataset BPI 2013 trong pilot. |
| **Boundary** | Chỉ phân loại + định tuyến. Không tự giải quyết ticket, không tự trả lời user, không xử lý ticket nhạy cảm (security/VIP) tự động. |

---

## Bước 6.0 — Ma trận độ phù hợp với AI

Bài toán của nhóm nằm ở ô nào?

```text
Độ mơ hồ THẤP × độ phức tạp TRUNG BÌNH.
```

Vì sao?

```text
- Độ mơ hồ thấp: output có đáp án đúng/sai khá rõ — category và team đúng là
  category/team đã thực sự giải quyết ticket đó (ground truth có trong log).
  Input là văn bản tự do (nhiễu) nhưng output là nhãn cố định.
- Độ phức tạp trung bình: workflow nhiều bước và nhiều team, nhưng tuyến tính —
  bước sau không đòi hỏi AI tự quyết định kế hoạch mới.
→ Theo ma trận: Workflow điều phối các bước rõ ràng là đủ, chưa cần Agent.
```

## Bước 6.1 — So sánh Rule / Workflow / Agent

| Mức | Phương án cho bài toán nhóm | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| **Rule** | Routing theo keyword/form: dropdown bắt buộc khi tạo ticket, keyword "VPN" → network team | Đủ cho ticket có mẫu rõ, lặp lại (reset password, cấp quyền) | Mô tả tự do đa dạng làm rule vỡ; user chọn sai category trong form; rule phình to khó bảo trì | Không chọn làm toàn bộ, nhưng giữ cho subset ticket mẫu rõ + form nhập có cấu trúc |
| **Workflow** | AI phân loại + đề xuất team kèm confidence → trên ngưỡng auto-route, dưới ngưỡng người review → audit mẫu định kỳ | Hợp vì output là nhãn cố định có ground truth, flow tuyến tính, có điểm chèn người rõ ràng | AI phân loại sai → ticket vẫn trễ; model drift theo thời gian; phụ thuộc chất lượng text ticket | **Chọn** |
| **Agent** | Agent tự hỏi lại user khi thiếu thông tin, tra knowledge base, tự resolve ticket L1 đơn giản | Chỉ cần khi muốn tự động cả bước hỏi lại + xử lý, nhiều nhánh quyết định động | Dataset không có KB article và nội dung hội thoại (đúng nghi ngại Nghĩa nêu); cần quyền tương tác với user; rủi ro trả lời sai trực tiếp đến user | Chưa chọn |

Mức chọn:

```text
Workflow.
```

Vì sao chọn:

```text
- Phân loại văn bản tự do vào nhãn cố định là đúng thế mạnh của AI, và có
  ground truth trong log để đo — không phải tin vào cảm giác.
- Điểm chèn con người rõ: ngưỡng confidence quyết định ticket nào người phải xem.
- Research cho thấy cả Zendesk, ServiceNow, Freshservice đều dừng đúng ở mức này.
```

Vì sao không chọn mức đơn giản hơn (Rule):

```text
Rule keyword/form đã tồn tại trong thực tế và vẫn để lọt: mô tả tự do đa dạng,
user chọn sai category, rule set phình to theo thời gian. Rule giữ vai trò xử lý
subset ticket mẫu rõ, không thay được bước hiểu văn bản tự do.
```

Vì sao không chọn Agent:

```text
Chưa có dữ liệu KB và hội thoại để agent tra cứu/tự resolve; agent tương tác
trực tiếp với user tạo rủi ro mới (trả lời sai) trong khi bottleneck đo được
nằm ở triage — giải quyết triage trước, nâng cấp sau nếu metric chứng minh.
```

## Bước 6.2 — Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Nhân viên L1/dispatcher tại service desk tổ chức lớn. |
| **Workflow** | User gửi ticket → L1 đọc + hỏi lại → phân loại → định tuyến → (sai thì reassign) → team xử lý → đóng. |
| **Bottleneck** | Triage thủ công (2-5'/ticket, giả định cần đo) và định tuyến sai gây ping-pong giữa các team, cộng hàng giờ→ngày chờ. |
| **Impact** | Ticket trễ, SLA vỡ, user chờ lâu; L1 làm việc phân loại lặp lại thay vì việc giá trị hơn. |
| **Success Metric** | % ticket đúng team ngay lần đầu tăng so với baseline; % reassignment giảm; thời gian triage/ticket giảm từ 2-5' xuống giây (auto) hoặc 1-2' (review). Baseline đo trên BPI 2013 trong pilot. |
| **Boundary** | AI chỉ phân loại + định tuyến; không tự resolve, không tự trả lời user; ticket nhạy cảm (security/VIP/pháp lý) luôn qua người; chỉ dùng dữ liệu trong ticket được cấp. |
| **AI intervention point** | Ngay sau khi ticket được tạo, trước khi vào hàng đợi bất kỳ team nào. |
| **Mức chọn** | Workflow: AI classify + confidence threshold; Rule cho subset mẫu rõ; người review case dưới ngưỡng. |
| **Rủi ro & người thật kiểm tra** | Risk: phân loại sai làm ticket trễ thêm, model drift, L1 ỷ lại vào AI. Người thật kiểm: L1 review mọi ticket dưới ngưỡng confidence + audit mẫu ngẫu nhiên ticket auto-route định kỳ; feedback route sai được ghi nhận để chỉnh ngưỡng/model. |

## Bước 6.3 — Final decision

| Câu hỏi | Yes / Not Yet / No | Ghi chú |
|---|---|---|
| Actor và workflow đã rõ chưa? | Yes | Quy trình ITSM chuẩn, cả nhóm vẽ được before/after |
| Baseline và success metric đã đo được chưa? | Not Yet | Metric định nghĩa rõ nhưng baseline phải đo từ dataset trong pilot |
| Có data/input đủ dùng chưa? | Not Yet | BPI 2013 công khai nhưng cần kiểm có đủ text mô tả không (nghi ngại Nghĩa) |
| Nếu AI sai, hậu quả có chấp nhận được không? | Yes | Sai = ticket đi vòng như hiện trạng, không tệ hơn; có ngưỡng + review + fallback |
| Có người review/owner vận hành không? | Yes | L1 review case dưới ngưỡng + audit mẫu; trong lab: nhóm đóng vai L1 |
| Có cách non-AI đơn giản hơn không? | Một phần | Rule/form giải được subset mẫu rõ, không giải được văn bản tự do |

Decision:

```text
Go với scope nhỏ — "Go" ở đây là go làm PILOT ĐO LƯỜNG trên dataset công khai,
không phải go deploy. Pilot chính là cách trả lời hai câu "Not Yet" ở trên.
```

Pilot nhỏ nhất:

```text
1. Kiểm tra BPI 2013: có đủ trường text mô tả ticket cho bài classification không.
   Nếu không đủ → chuyển sang bug report dataset công khai (Bugzilla của
   Eclipse/Mozilla) làm proxy — cùng pattern "văn bản tự do → phân loại → định tuyến".
2. Lấy subset vài trăm ticket có ground truth (team/component đã thực sự xử lý).
3. Chạy AI phân loại category + đề xuất team, xuất kèm confidence.
4. Đo: first-assignment accuracy so với ground truth; phân bố confidence để
   chọn ngưỡng auto-route; ước lượng % ticket ping-pong tránh được.
5. Báo cáo lại nhóm để chốt ngưỡng và viết đề xuất tiếp theo.
```

Exit / rollback:

```text
- Nếu accuracy trên dataset thấp hơn mức người thật làm được (ước từ chính log),
  hạ về Rule + form nhập có cấu trúc, không dùng AI classify.
- Nếu text ticket quá nghèo để phân loại (cả ở dataset thay thế), kết luận
  No-Go cho AI ở bước này và đề xuất sửa form nhập ticket trước — đó cũng là
  một kết luận tốt theo tinh thần lab.
```

Decision rationale:

```text
- Problem, workflow, metric đều rõ; ground truth có sẵn trong log công khai.
- Có non-AI component (Rule/form) giữ đúng vai trò của nó.
- AI nằm ở một bước cụ thể (triage), không ôm toàn bộ quy trình.
- Human boundary và fallback rõ: ngưỡng confidence, review, audit, tắt auto-route.
- Hai điểm chưa chắc (baseline, độ đầy đủ dữ liệu) được xử lý bằng chính pilot,
  với điều kiện dừng rõ ràng.
```

---

*02 — Group Problem Statement — Day 02 Lab*
