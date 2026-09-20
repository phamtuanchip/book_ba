# Chương 21: FRD & yêu cầu phi chức năng (performance, security, usability)

## Mục tiêu học

- Phân biệt FRD (Functional Requirements Document) với SRS — và biết khi nào cần tách riêng.
- Nắm được các nhóm yêu cầu phi chức năng phổ biến và biết viết mỗi nhóm sao cho đo lường được.
- Tránh lỗi phổ biến nhất về yêu cầu phi chức năng: viết chung chung, không kiểm tra được.

## 21.1 FRD là gì, khác SRS ở đâu?

**FRD (Functional Requirements Document)** đôi khi được dùng như một tài liệu **tách riêng phần
chức năng** ra khỏi SRS đầy đủ (SRS bao gồm cả chức năng lẫn phi chức năng, giao diện bên ngoài...).
Ở nhiều công ty, FRD và SRS được dùng thay thế lẫn nhau (không phân biệt), hoặc FRD được coi là
"phiên bản rút gọn, chỉ tập trung chức năng" của SRS đầy đủ.

**Khi nào nên tách FRD riêng khỏi SRS?**

- Khi đối tượng đọc khác nhau: FRD cho Dev tập trung code chức năng, SRS đầy đủ (bao gồm phi chức
  năng, ràng buộc hệ thống) dành cho kiến trúc sư/đội hạ tầng.
- Khi dự án lớn, cần tài liệu phi chức năng dùng chung cho **nhiều module** (không lặp lại yêu cầu
  bảo mật/hiệu năng ở từng SRS riêng lẻ của từng module).

Với dự án quy mô vừa/nhỏ như FoodNow, gộp chung trong một SRS (như mẫu ở Chương 20) là đủ và hợp
lý — không cần tách FRD riêng.

## 21.2 Vì sao yêu cầu phi chức năng hay bị viết sơ sài?

Yêu cầu chức năng ("hệ thống phải làm được gì") thường dễ hình dung và dễ được stakeholder nói ra
rõ ràng khi elicitation (Chương 12) — vì nó gắn trực tiếp với thao tác cụ thể. Yêu cầu phi chức
năng ("hệ thống phải làm tốt đến mức nào") lại thường **bị coi là hiển nhiên** ("tất nhiên phải
nhanh, tất nhiên phải bảo mật rồi") nên ít khi được hỏi rõ ràng — dẫn đến viết chung chung như "hệ
thống phải nhanh", "hệ thống phải bảo mật", những câu **không thể verify được** (Chương 17) và
không ai biết khi nào là "đủ nhanh, đủ bảo mật".

## 21.3 Các nhóm yêu cầu phi chức năng phổ biến

| Nhóm | Câu hỏi cần hỏi khi elicitation | Ví dụ viết đạt chuẩn (đo lường được) |
|---|---|---|
| **Performance (Hiệu năng)** | Thao tác này cần nhanh đến mức nào? Bao nhiêu người dùng cùng lúc? | "Trang xác nhận đơn hàng phải tải xong trong dưới 2 giây với 95% lượt truy cập, đo trên kết nối 4G" |
| **Security (Bảo mật)** | Dữ liệu nào nhạy cảm? Ai được phép truy cập gì? | "Mật khẩu người dùng phải được băm (hash) bằng thuật toán bcrypt, không lưu dạng plain text" |
| **Usability (Khả năng sử dụng)** | Người dùng mục tiêu có đặc điểm gì (tuổi, kinh nghiệm công nghệ)? | "Người dùng lần đầu phải hoàn tất được một đơn hàng mà không cần hướng dẫn, đo qua kiểm thử usability với tối thiểu 5 người dùng thử nghiệm" |
| **Reliability (Độ tin cậy)** | Hệ thống được phép "chết" (downtime) bao lâu? | "Hệ thống đặt hàng phải đạt độ khả dụng (uptime) tối thiểu 99.5% mỗi tháng" |
| **Scalability (Khả năng mở rộng)** | Trong 1-2 năm tới, tải sẽ tăng đến mức nào? | "Hệ thống phải chịu tải gấp 3 lần hiện tại mà không cần thay đổi kiến trúc, khi FoodNow mở thêm chi nhánh" |
| **Maintainability (Khả năng bảo trì)** | Ai sẽ bảo trì hệ thống sau này, cần tài liệu gì? | "Toàn bộ API tích hợp phải có tài liệu Swagger/OpenAPI cập nhật" |
| **Compatibility (Khả năng tương thích)** | Chạy trên thiết bị/nền tảng nào? | "Ứng dụng phải chạy được trên iOS 14+ và Android 8+" |
| **Compliance (Tuân thủ pháp lý)** | Có quy định pháp luật/ngành nào cần tuân thủ? | "Dữ liệu cá nhân khách hàng phải được xử lý theo quy định bảo vệ dữ liệu cá nhân hiện hành" |

## 21.4 Kỹ thuật viết yêu cầu phi chức năng đo lường được

Công thức chung: **[Đối tượng] phải [hành vi đo lường được] trong [điều kiện cụ thể], đo bằng
[phương pháp/công cụ đo]**.

> Ví dụ áp dụng công thức: "**[Trang thanh toán]** phải **[phản hồi kết quả giao dịch trong dưới
> 3 giây]** trong **[điều kiện tải bình thường, dưới 100 giao dịch/phút]**, đo bằng **[công cụ
> kiểm thử hiệu năng JMeter trong môi trường staging]**."

So sánh với câu mơ hồ ban đầu "hệ thống phải nhanh" — câu viết theo công thức trên cho QA đủ thông
tin để viết test case cụ thể (liên hệ Chương 34), và cho Dev/kiến trúc sư biết chính xác mục tiêu
kỹ thuật cần đạt được.

## 21.5 Kỹ thuật elicitation riêng cho yêu cầu phi chức năng

Vì stakeholder ít khi tự nói ra yêu cầu phi chức năng rõ ràng, BA cần **chủ động hỏi**, gợi ý bằng
kịch bản cụ thể thay vì hỏi trừu tượng:

- Thay vì hỏi "Anh/chị cần hệ thống bảo mật đến mức nào?" (quá trừu tượng, khó trả lời) → hỏi "Nếu
  có người cố đăng nhập sai mật khẩu 10 lần liên tiếp vào tài khoản khách hàng, anh/chị mong muốn
  hệ thống xử lý thế nào?"
- Thay vì hỏi "Hệ thống cần nhanh đến mức nào?" → hỏi "Trong giờ cao điểm trưa, ước tính có bao
  nhiêu khách đặt hàng cùng lúc? Nếu app load chậm 5 giây vào lúc đó, ảnh hưởng ra sao đến doanh thu?"

## Bài tập

1. Viết lại yêu cầu "Ứng dụng phải dễ dùng" thành một yêu cầu Usability đo lường được, theo công
   thức ở mục 21.4.
2. Với dự án FoodNow, hệ thống cần lưu trữ ảnh món ăn (dung lượng lớn, nhiều chi nhánh upload liên
   tục). Viết một yêu cầu Scalability liên quan đến việc lưu trữ này, đo lường được.

## Sai lầm thường gặp

- **Chỉ hỏi yêu cầu chức năng khi elicitation, quên hẳn phi chức năng**: dẫn đến hệ thống "chạy
  đúng" nhưng chậm, dễ bị tấn công, hoặc không mở rộng được khi cần.
- **Viết yêu cầu phi chức năng nhưng không nêu cách đo**: "hệ thống phải bảo mật" không đo được —
  luôn cần gắn với con số/phương pháp đo cụ thể như công thức mục 21.4.
- **Đặt mục tiêu phi chức năng phi thực tế** (ví dụ "uptime 100%, không bao giờ được lỗi") — không
  hệ thống nào đạt 100% tuyệt đối; nên đặt mục tiêu khả thi, có thể đàm phán dựa trên chi phí/kỹ
  thuật thực tế (liên hệ tiêu chí "Feasible" ở Chương 17).

## Tóm tắt & tiếp theo

FRD (nếu tách riêng) tập trung phần chức năng của SRS; yêu cầu phi chức năng (hiệu năng, bảo mật,
khả dụng, mở rộng, bảo trì, tương thích, tuân thủ) cần được viết đo lường được theo công thức "đối
tượng - hành vi - điều kiện - cách đo", và BA cần chủ động hỏi vì stakeholder ít khi tự nói ra rõ
ràng. Chương 22 sẽ học cách viết **Use Case Specification** — đặc tả chi tiết từng luồng tương tác
cụ thể giữa actor và hệ thống.
