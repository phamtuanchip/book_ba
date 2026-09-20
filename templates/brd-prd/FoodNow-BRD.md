# Business Requirements Document (BRD)

## FoodNow — Ứng dụng đặt đồ ăn trực tuyến

| | |
|---|---|
| **Mã tài liệu** | FN-BRD-001 |
| **Phiên bản** | 1.0 |
| **Ngày soạn thảo** | 2024-02-01 |
| **Người soạn thảo** | Nguyễn Văn A — Business Analyst |
| **Trạng thái** | Đã phê duyệt |

### Lịch sử phiên bản

| Phiên bản | Ngày | Người sửa | Mô tả thay đổi |
|---|---|---|---|
| 0.1 | 2024-01-15 | Nguyễn Văn A | Bản nháp đầu tiên |
| 0.2 | 2024-01-25 | Nguyễn Văn A | Cập nhật sau workshop với quản lý 12 chi nhánh |
| 1.0 | 2024-02-01 | Nguyễn Văn A | Bản chính thức, đã Ban giám đốc phê duyệt |

---

## 1. Bối cảnh & vấn đề nghiệp vụ

Chuỗi nhà hàng FoodNow hiện có 12 chi nhánh tại TP.HCM, nhận đặt hàng qua điện thoại (tổng đài nội
bộ) và các ứng dụng giao đồ ăn của bên thứ ba (chiếm khoảng 65% tổng số đơn hàng online). Việc phụ
thuộc vào app bên thứ ba gây ra 3 vấn đề:

1. **Chi phí hoa hồng cao**: 20-25% giá trị mỗi đơn hàng, ăn trực tiếp vào biên lợi nhuận.
2. **Không sở hữu dữ liệu khách hàng**: không thể xây dựng chương trình khách hàng thân thiết hiệu
   quả vì dữ liệu khách hàng thuộc về nền tảng bên thứ ba.
3. **Không kiểm soát được trải nghiệm thương hiệu**: giao diện, quy trình đặt hàng theo chuẩn của
   nền tảng bên thứ ba, không thể tuỳ biến theo bản sắc FoodNow.

## 2. Mục tiêu kinh doanh

| ID | Mục tiêu | Chỉ số đo lường | Hạn hoàn thành |
|---|---|---|---|
| BO-01 | Giảm phụ thuộc vào app bên thứ ba | Tỷ trọng đơn hàng qua app riêng đạt tối thiểu 40% tổng đơn online trong 6 tháng sau go-live | 6 tháng sau go-live |
| BO-02 | Tăng biên lợi nhuận trên mỗi đơn hàng | Biên lợi nhuận trung bình/đơn tăng tối thiểu 15% so với đơn qua app bên thứ ba | 12 tháng sau go-live |
| BO-03 | Xây dựng dữ liệu khách hàng riêng | Thu thập được thông tin và lịch sử mua hàng của tối thiểu 10.000 khách hàng | 6 tháng sau go-live |

## 3. Phạm vi

### Trong phạm vi (In scope)

- Ứng dụng di động (iOS + Android) cho khách hàng đặt món, thanh toán, theo dõi đơn hàng.
- Hệ thống quản trị (web) cho nhân viên chi nhánh xác nhận và xử lý đơn hàng.
- Tích hợp cổng thanh toán online (thẻ, ví điện tử) và thanh toán khi nhận hàng (COD).
- Chương trình khách hàng thân thiết cơ bản (tích điểm, đổi ưu đãi).
- Thông báo trạng thái đơn hàng theo thời gian thực.

### Ngoài phạm vi (Out of scope) — cho phiên bản đầu tiên

- Tính năng đặt bàn trước để ăn tại quán (đề xuất cho phiên bản sau, xem CR-01 nếu được phê duyệt).
- Giao hàng liên tỉnh/ngoài TP.HCM.
- Đa ngôn ngữ (chỉ tiếng Việt ở phiên bản đầu).
- Tích hợp với hệ thống kế toán/ERP hiện có (sẽ đánh giá ở giai đoạn sau).
- Chương trình giới thiệu bạn bè (referral program).

## 4. Đối tượng sử dụng (Stakeholders)

| Nhóm | Nhu cầu tổng quan |
|---|---|
| Khách hàng | Đặt món nhanh, theo dõi đơn hàng, tích điểm thành viên |
| Nhân viên chi nhánh | Nhận và xử lý đơn hàng hiệu quả, không thao tác thủ công qua điện thoại |
| Người giao hàng | Nhận thông tin đơn hàng rõ ràng, cập nhật trạng thái giao hàng dễ dàng |
| Ban giám đốc | Theo dõi số liệu kinh doanh tổng thể, biên lợi nhuận theo kênh bán hàng |
| Phòng Marketing | Quản lý chương trình khách hàng thân thiết, gửi khuyến mãi |
| Phòng Kế toán | Đối soát doanh thu, dữ liệu giao dịch chính xác |

## 5. Yêu cầu nghiệp vụ chi tiết

| ID | Yêu cầu | Nguồn |
|---|---|---|
| BR-01 | Khách hàng phải đặt và hoàn tất thanh toán trong một luồng liên tục, không quá 2 phút với đơn hàng thông thường | Ban giám đốc, workshop khách hàng |
| BR-02 | Nhân viên chi nhánh phải nhận được thông báo đơn hàng mới ngay lập tức, không cần thao tác kiểm tra thủ công | Quản lý chi nhánh |
| BR-03 | Hệ thống phải ghi nhận và tích luỹ điểm thưởng cho khách hàng theo giá trị đơn hàng | Phòng Marketing |
| BR-04 | Ban giám đốc phải xem được báo cáo doanh thu, số đơn hàng theo từng chi nhánh, theo ngày/tuần/tháng | Ban giám đốc |
| BR-05 | Hệ thống phải cho phép nhân viên chi nhánh từ chối đơn hàng (hết món, quá tải) kèm lý do rõ ràng gửi lại khách hàng | Quản lý chi nhánh |

## 6. Giả định & ràng buộc

**Giả định:**
- Toàn bộ 12 chi nhánh có kết nối Internet ổn định để dùng hệ thống quản trị.
- Khách hàng mục tiêu chủ yếu dùng smartphone (iOS/Android), không cần hỗ trợ nền tảng feature phone.

**Ràng buộc:**
- Ngân sách phát triển giai đoạn 1: tối đa 1.5 tỷ VNĐ.
- Thời gian ra mắt phiên bản đầu tiên: trong vòng 6 tháng kể từ khi BRD được phê duyệt.
- Phải tuân thủ quy định bảo vệ dữ liệu cá nhân khách hàng theo pháp luật hiện hành.

## 7. Rủi ro sơ bộ

| Rủi ro | Mức độ | Biện pháp giảm thiểu sơ bộ |
|---|---|---|
| Khách hàng quen dùng app bên thứ ba, ngại chuyển sang app mới | Cao | Chương trình khuyến mãi ra mắt, ưu đãi độc quyền trên app riêng |
| Nhân viên chi nhánh khó thích nghi hệ thống mới | Trung bình | Đào tạo kỹ trước go-live (xem Transition Requirements — Chương 14) |
| Trễ tiến độ do tích hợp cổng thanh toán phức tạp hơn dự kiến | Trung bình | Ưu tiên tích hợp cổng thanh toán ở sprint đầu để phát hiện rủi ro sớm |

*(Xem RAID Log đầy đủ tại Phụ lục D / Chương 31 để theo dõi chi tiết trong suốt dự án.)*

## 8. Tiêu chí thành công

- Đạt được BO-01, BO-02, BO-03 ở mục 2 trong khung thời gian đề ra.
- Ứng dụng đạt điểm đánh giá trung bình tối thiểu 4.2/5 trên App Store/Google Play sau 3 tháng.
- Tỷ lệ đơn hàng lỗi/khiếu nại dưới 2% tổng số đơn.

## 9. Phê duyệt

| Vai trò | Họ tên | Chữ ký/Xác nhận | Ngày |
|---|---|---|---|
| Sponsor (Giám đốc điều hành) | Trần Thị B | Đã phê duyệt | 2024-02-01 |
| Trưởng phòng Marketing | Lê Văn C | Đã phê duyệt | 2024-02-01 |
| Trưởng phòng Vận hành | Phạm Thị D | Đã phê duyệt | 2024-02-01 |
