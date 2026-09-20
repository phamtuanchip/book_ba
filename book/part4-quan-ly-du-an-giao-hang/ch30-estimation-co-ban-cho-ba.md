# Chương 30: Estimation cơ bản cho BA: story points, T-shirt sizing

## Mục tiêu học

- Hiểu vì sao ước lượng trong Agile dùng đơn vị tương đối (story point) thay vì thời gian tuyệt đối.
- Biết cách BA hỗ trợ (không thay thế) đội kỹ thuật trong quá trình ước lượng.
- Áp dụng được kỹ thuật T-shirt sizing và Planning Poker ở mức cơ bản.

## 30.1 Vì sao dùng đơn vị tương đối thay vì giờ/ngày?

Nhiều người mới thắc mắc: "Sao không ước lượng thẳng bằng số giờ/ngày cho dễ hiểu?" — vấn đề là
con người **ước lượng thời gian tuyệt đối rất tệ** (ai cũng từng nói "chắc 2 tiếng là xong" rồi mất
cả ngày), nhưng lại **so sánh độ phức tạp tương đối khá tốt** ("việc B khó gấp đôi việc A" dễ đánh
giá hơn "việc B mất chính xác bao nhiêu giờ").

**Story point** là đơn vị đo độ phức tạp/công sức **tương đối**, không map trực tiếp sang giờ/ngày
— thường dùng dãy số Fibonacci (1, 2, 3, 5, 8, 13, 21...) vì khoảng cách giữa các số tăng dần phản
ánh đúng thực tế: càng việc lớn, càng khó ước lượng chính xác, nên không cần phân biệt "13 hay 14
điểm" — chỉ cần biết nó lớn hơn nhiều so với việc 3 điểm.

## 30.2 Vai trò của BA trong Estimation — hỗ trợ, không thay thế Dev

**Nguyên tắc quan trọng nhất: BA không tự ước lượng thay Dev.** Người ước lượng độ phức tạp kỹ
thuật phải là người **trực tiếp làm việc đó** (Dev, QA) — BA đóng vai trò:

- Đảm bảo User Story đủ rõ ràng để đội ước lượng chính xác (Definition of Ready — Chương 24, 27).
- Trả lời câu hỏi làm rõ ngay khi đội đang thảo luận ước lượng (ví dụ: "có cần hỗ trợ cả trường
  hợp khách hàng chưa đăng nhập không?" — câu trả lời ảnh hưởng trực tiếp đến độ phức tạp).
- Giúp đội hiểu **giá trị nghiệp vụ** đằng sau, để phân biệt việc "phức tạp về nghiệp vụ" (nhiều
  quy tắc, nhiều trường hợp) và "phức tạp về kỹ thuật" (khó implement dù quy tắc đơn giản) — hai
  loại phức tạp này ảnh hưởng khác nhau đến ước lượng.

## 30.3 Planning Poker — kỹ thuật ước lượng theo nhóm

**Planning Poker** là kỹ thuật phổ biến nhất để ước lượng story point theo nhóm, tránh hiện tượng
một người có tiếng nói ảnh hưởng đến tất cả người khác (anchoring bias):

1. BA trình bày User Story và Acceptance Criteria.
2. Mỗi thành viên đội (thường là Dev/QA) **đồng thời** chọn một con số (từ bộ thẻ Fibonacci) thể
   hiện ước lượng của riêng mình, không xem trước con số của người khác.
3. Tất cả lật thẻ cùng lúc.
4. Nếu con số khác nhau nhiều (ví dụ người chọn 3, người chọn 13) — người có số cao nhất và thấp
   nhất giải thích lý do, cả nhóm thảo luận ngắn.
5. Lặp lại vòng chọn cho đến khi đạt đồng thuận tương đối.

Kỹ thuật này giúp lộ ra ngay **những hiểu biết khác nhau về cùng một yêu cầu** — nếu một Dev nghĩ
task đơn giản (3 điểm) trong khi Dev khác nghĩ rất phức tạp (13 điểm), đây thường là dấu hiệu yêu
cầu **chưa đủ rõ ràng**, cần BA làm rõ thêm trước khi chốt ước lượng — một lợi ích phụ quan trọng
của Planning Poker ngoài việc ra con số cuối cùng.

## 30.4 T-shirt Sizing — ước lượng nhanh, ít chính xác hơn

Khi cần ước lượng **nhanh, ở mức rất tổng quan** (ví dụ để PO sắp xếp độ ưu tiên sơ bộ cho hàng
chục Epic trước khi refine chi tiết), dùng **T-shirt Sizing**: XS, S, M, L, XL — không cần họp
Planning Poker đầy đủ, chỉ cần đội cho ý kiến nhanh, tương đối.

| Kích cỡ | Ý nghĩa | Ví dụ FoodNow (ở mức Epic) |
|---|---|---|
| XS | Rất nhỏ, vài giờ đến 1 ngày | Thêm 1 trường thông tin vào form đặt hàng |
| S | Nhỏ, 1-3 ngày | US-402: xem số điểm hiện có |
| M | Vừa, khoảng 1 sprint | US-106: áp dụng mã giảm giá |
| L | Lớn, 2-3 sprint | Epic B: Theo dõi đơn hàng real-time |
| XL | Rất lớn, cần phân rã thêm trước khi ước lượng chính xác | Epic C: Chương trình khách hàng thân thiết |

Một Epic được xếp XL là tín hiệu rõ ràng: **cần phân rã (Chương 24) trước khi ước lượng chi tiết
bằng story point** — T-shirt Sizing không thay thế Planning Poker, chỉ là bước lọc sơ bộ trước đó.

## 30.5 Velocity — dùng ước lượng để lập kế hoạch

Sau vài sprint, đội tích luỹ được **Velocity** (tốc độ trung bình) — tổng story point hoàn thành
mỗi sprint. BA/PO dùng Velocity để dự đoán: với backlog còn lại tổng cộng bao nhiêu điểm, còn cần
khoảng bao nhiêu sprint nữa — hữu ích khi Sponsor hỏi "khi nào xong?"

> Ví dụ: Đội FoodNow có Velocity trung bình 25 điểm/sprint (2 tuần). Backlog còn lại của Epic C là
> 60 điểm → ước tính cần khoảng 60/25 ≈ 2.4 sprint, tức khoảng 5 tuần để hoàn thành Epic C.

**Lưu ý quan trọng**: Velocity chỉ đáng tin cậy sau vài sprint ổn định của **cùng một đội** — không
nên so sánh Velocity giữa các đội khác nhau (story point không phải đơn vị tuyệt đối, mỗi đội có
"thang đo" riêng), và Velocity của một đội mới thành lập thường chưa ổn định.

## Bài tập

1. Chọn 4 User Story từ `templates/user-story-epic/FoodNow-UserStories.md`, tự ước lượng T-shirt
   Size cho mỗi story (dựa trên trực giác, không cần chính xác tuyệt đối) — giải thích lý do.
2. Giải thích bằng lời của bạn: nếu trong một buổi Planning Poker, 3 Dev chọn "3 điểm" còn 1 Dev
   chọn "13 điểm" cho cùng một story, BA nên làm gì tiếp theo?

## Sai lầm thường gặp

- **BA tự ước lượng thay Dev vì "sợ mất thời gian họp"**: vi phạm nguyên tắc cốt lõi — người làm
  việc đó phải là người ước lượng, BA chỉ hỗ trợ làm rõ yêu cầu.
- **Quy đổi story point sang giờ một cách máy móc** (ví dụ "1 điểm = 4 giờ" cố định): đi ngược bản
  chất đơn vị tương đối của story point — quy đổi này chỉ đúng tạm thời với một đội cụ thể, không
  áp dụng chung cho mọi đội/mọi thời điểm.
- **So sánh Velocity giữa các đội khác nhau để đánh giá "đội nào giỏi hơn"**: sai lầm phổ biến của
  quản lý thiếu kinh nghiệm Agile — Velocity không phải thước đo năng suất tuyệt đối, chỉ có ý nghĩa
  để lập kế hoạch nội bộ của chính đội đó.

## Tóm tắt & tiếp theo

Story point là đơn vị ước lượng tương đối, BA hỗ trợ (không thay thế) đội kỹ thuật ước lượng thông
qua làm rõ yêu cầu; Planning Poker giúp ước lượng chi tiết theo nhóm, T-shirt Sizing giúp ước lượng
nhanh ở mức tổng quan, và Velocity giúp lập kế hoạch dựa trên tốc độ thực tế của đội. Chương 31 sẽ
học công cụ quản lý rủi ro/vấn đề xuyên suốt dự án: **RAID Log**.
