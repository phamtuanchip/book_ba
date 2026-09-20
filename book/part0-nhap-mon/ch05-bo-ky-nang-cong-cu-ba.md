# Chương 5: Bộ kỹ năng & công cụ của BA: kỹ năng cứng, kỹ năng mềm, công cụ phổ biến

## Mục tiêu học

- Liệt kê được các nhóm kỹ năng cứng và kỹ năng mềm cốt lõi của BA.
- Biết công cụ nào dùng để làm gì trong công việc BA hằng ngày, ở mức đủ để bắt đầu dùng được.
- Hiểu vì sao kỹ năng mềm thường quan trọng hơn kỹ năng cứng đối với BA — khác với nhiều vai trò
  kỹ thuật khác.

## 5.1 Kỹ năng cứng (Hard skills)

| Nhóm kỹ năng | Cụ thể | Học ở chương nào |
|---|---|---|
| Elicitation | Kỹ thuật phỏng vấn, workshop, quan sát | 12 |
| Modeling | Vẽ Use Case Diagram, Activity Diagram, BPMN | 15 |
| Viết tài liệu | BRD, PRD, SRS, User Story, Use Case Spec | 19-24 |
| Quản lý yêu cầu | Traceability Matrix, Change Request | 16, 18 |
| Ước lượng & ưu tiên hoá | Story point, MoSCoW, WSJF | 26, 30 |
| Đọc hiểu dữ liệu | SQL cơ bản, đọc mô hình dữ liệu (ERD) | 38 |

Lưu ý: BA **không cần biết lập trình**. Kỹ năng "đọc hiểu dữ liệu" ở Chương 38 dừng ở mức viết
được câu SELECT đơn giản để tự tra cứu, không phải kỹ năng lập trình ứng dụng.

## 5.2 Kỹ năng mềm (Soft skills)

Đây là nhóm kỹ năng **quyết định BA giỏi hay không**, nhiều hơn kỹ năng cứng — vì bản chất công
việc BA là làm việc với con người, không phải làm việc với máy:

- **Lắng nghe chủ động (active listening)**: nghe để hiểu ý định thật, không chỉ nghe để ghi chép
  từ ngữ. Ví dụ: khi Sponsor nói "tôi muốn app nhanh hơn", BA giỏi sẽ hỏi tiếp "nhanh hơn ở bước
  nào cụ thể, và nhanh hơn để giải quyết vấn đề gì" thay vì ghi thẳng "yêu cầu: tăng tốc độ app".
- **Đặt câu hỏi có mục đích**: biết hỏi câu nào để mở rộng thông tin (open question), câu nào để
  xác nhận/thu hẹp (closed question) — xem chi tiết kỹ thuật ở Chương 12.
- **Giao tiếp thích ứng theo đối tượng**: đã nói ở Chương 3 — nói khác nhau với Sponsor và với Dev.
- **Giải quyết xung đột**: các stakeholder thường có yêu cầu mâu thuẫn nhau (ví dụ: phòng Marketing
  muốn thêm nhiều bước thu thập thông tin khách hàng, phòng UX muốn quy trình đặt hàng càng ngắn
  càng tốt) — BA cần điều hoà, không né tránh.
- **Tư duy phản biện (critical thinking)**: không chấp nhận yêu cầu ở mức bề mặt, luôn hỏi "tại
  sao cần cái này" để tìm ra vấn đề gốc rễ (root cause), tránh việc chỉ giải quyết triệu chứng.
- **Kiên nhẫn & chịu được sự mơ hồ**: giai đoạn đầu dự án luôn mơ hồ, thông tin không đầy đủ — BA
  cần thoải mái làm việc trong trạng thái đó thay vì đòi hỏi mọi thứ phải rõ ràng ngay từ đầu.

## 5.3 Công cụ phổ biến

| Công cụ | Dùng để làm gì | Mức độ cần biết |
|---|---|---|
| **Jira** | Quản lý backlog, epic/story, theo dõi tiến độ sprint | Thành thạo (Chương 37) |
| **Confluence** | Viết và lưu trữ tài liệu (BRD, SRS, meeting notes), liên kết với Jira | Thành thạo (Chương 37) |
| **draw.io / Lucidchart / Visio** | Vẽ sơ đồ quy trình, use case diagram, wireframe đơn giản | Cơ bản, đủ vẽ sơ đồ trong tài liệu |
| **Figma** | Xem/góp ý thiết kế UI do Designer làm, đôi khi tự vẽ wireframe nhanh | Cơ bản — BA thường chỉ cần đọc/comment, không cần tự thiết kế |
| **Excel/Google Sheets** | Traceability Matrix, RAID log, so sánh phương án | Thành thạo — công cụ "vạn năng" bị đánh giá thấp nhưng dùng liên tục |
| **Draw diagrams as code (Mermaid, PlantUML)** | Vẽ sơ đồ dạng text, dễ version control, dễ nhúng vào tài liệu Markdown/Confluence | Cơ bản, ngày càng phổ biến ở các đội kỹ thuật hiện đại |

> Sách này không đi sâu hướng dẫn cài đặt/thao tác từng công cụ như một khoá học phần mềm riêng —
> Chương 37 giới thiệu cách **dùng Jira/Confluence trong quy trình làm việc của BA** (workflow),
> không phải hướng dẫn admin/cấu hình hệ thống (đó là việc của PM/IT Admin).

## 5.4 Ma trận ưu tiên học: nên học gì trước?

Nếu bạn hoàn toàn mới, thứ tự ưu tiên hợp lý:

1. Kỹ năng mềm (lắng nghe, đặt câu hỏi) — nền tảng cho mọi thứ khác, học qua thực hành là chính.
2. Cách viết User Story và Acceptance Criteria (Chương 23) — kỹ năng dùng hằng ngày ở hầu hết công
   ty làm Agile hiện nay.
3. Cách vẽ Use Case/Activity Diagram cơ bản (Chương 15) — công cụ tư duy giúp phát hiện lỗ hổng
   trong yêu cầu trước khi trình bày với người khác.
4. Jira/Confluence ở mức dùng được (Chương 37) — hầu hết nơi tuyển dụng đòi hỏi biết công cụ này.
5. BRD/SRS đầy đủ (Chương 19-20) — cần thiết hơn khi làm ở các dự án lớn, tổ chức theo Waterfall
   hoặc yêu cầu tài liệu hoá chặt chẽ (ví dụ ngành Banking, Insurance).

## Bài tập

1. Tự đánh giá bản thân theo 6 kỹ năng mềm ở mục 5.2 (thang 1-5). Chọn ra 1 kỹ năng yếu nhất, viết
   một hành động cụ thể để cải thiện trong tuần tới (ví dụ: "trong buổi họp tới, chủ động hỏi lại
   ít nhất 2 câu làm rõ trước khi ghi chú yêu cầu").
2. Nếu chưa dùng Jira/Confluence bao giờ, tạo một tài khoản dùng thử (bản miễn phí cho cá nhân) và
   thử tạo một Epic + 2 User Story cho một tính năng bất kỳ của FoodNow.

## Sai lầm thường gặp

- **Học công cụ trước, bỏ qua kỹ năng mềm**: biết dùng Jira thành thạo không giúp ích nếu không
  biết hỏi đúng câu hỏi để có nội dung đưa vào Jira.
- **Nghĩ phải giỏi vẽ đẹp mới vẽ được sơ đồ**: giá trị của sơ đồ nằm ở việc **làm rõ tư duy và phát
  hiện lỗ hổng logic**, không nằm ở tính thẩm mỹ — sơ đồ vẽ tay trên giấy trong buổi họp vẫn có giá
  trị như sơ đồ vẽ bằng công cụ chuyên nghiệp.
- **Ôm đồm học hết mọi công cụ cùng lúc**: nên học công cụ theo nhu cầu thực tế của dự án đang làm,
  thay vì học dàn trải nhiều công cụ chưa dùng đến.

## Tóm tắt & tiếp theo

BA cần cả kỹ năng cứng (viết tài liệu, modeling, quản lý yêu cầu) lẫn kỹ năng mềm (lắng nghe, đặt
câu hỏi, giao tiếp thích ứng) — trong đó kỹ năng mềm thường là yếu tố phân biệt BA giỏi với BA
trung bình. Phần 0 đến đây đã cho bạn bức tranh tổng quan về nghề BA. Từ Chương 6, sách sẽ đi sâu
vào Phần 1: các mô hình quản lý dự án phần mềm cụ thể (Waterfall, Agile, Scrum, XP, Kanban) và vai
trò chi tiết của BA trong từng mô hình.
