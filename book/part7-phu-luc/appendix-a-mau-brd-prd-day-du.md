# Phụ lục A: Mẫu BRD & PRD đầy đủ (dự án FoodNow)

> Nội dung dưới đây in lại đầy đủ từ file mẫu gốc, dùng được ngay để sao chép/điều chỉnh cho dự án
> thật của bạn: `templates/brd-prd/FoodNow-BRD.md` và `templates/brd-prd/FoodNow-PRD.md`. Xem giải
> thích cấu trúc và cách viết từng phần tại Chương 19.

---

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

## 1. Bối cảnh & vấn đề nghiệp vụ

Chuỗi nhà hàng FoodNow hiện có 12 chi nhánh tại TP.HCM, nhận đặt hàng qua điện thoại (tổng đài nội
bộ) và các ứng dụng giao đồ ăn của bên thứ ba (chiếm khoảng 65% tổng số đơn hàng online). Việc phụ
thuộc vào app bên thứ ba gây ra 3 vấn đề: chi phí hoa hồng cao (20-25% giá trị mỗi đơn hàng), không
sở hữu dữ liệu khách hàng, và không kiểm soát được trải nghiệm thương hiệu.

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

- Tính năng đặt bàn trước để ăn tại quán.
- Giao hàng liên tỉnh/ngoài TP.HCM.
- Đa ngôn ngữ (chỉ tiếng Việt ở phiên bản đầu).
- Tích hợp với hệ thống kế toán/ERP hiện có.
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

**Giả định:** toàn bộ 12 chi nhánh có kết nối Internet ổn định; khách hàng mục tiêu chủ yếu dùng
smartphone (iOS/Android).

**Ràng buộc:** ngân sách phát triển giai đoạn 1 tối đa 1.5 tỷ VNĐ; ra mắt phiên bản đầu trong vòng
6 tháng; tuân thủ quy định bảo vệ dữ liệu cá nhân khách hàng hiện hành.

## 7. Rủi ro sơ bộ

| Rủi ro | Mức độ | Biện pháp giảm thiểu sơ bộ |
|---|---|---|
| Khách hàng quen dùng app bên thứ ba, ngại chuyển sang app mới | Cao | Chương trình khuyến mãi ra mắt, ưu đãi độc quyền trên app riêng |
| Nhân viên chi nhánh khó thích nghi hệ thống mới | Trung bình | Đào tạo kỹ trước go-live |
| Trễ tiến độ do tích hợp cổng thanh toán phức tạp hơn dự kiến | Trung bình | Ưu tiên tích hợp cổng thanh toán ở sprint đầu để phát hiện rủi ro sớm |

*(Xem RAID Log đầy đủ tại Phụ lục còn lại và Chương 31.)*

## 8. Tiêu chí thành công

- Đạt được BO-01, BO-02, BO-03 trong khung thời gian đề ra.
- Ứng dụng đạt điểm đánh giá trung bình tối thiểu 4.2/5 trên App Store/Google Play sau 3 tháng.
- Tỷ lệ đơn hàng lỗi/khiếu nại dưới 2% tổng số đơn.

## 9. Phê duyệt

| Vai trò | Họ tên | Chữ ký/Xác nhận | Ngày |
|---|---|---|---|
| Sponsor (Giám đốc điều hành) | Trần Thị B | Đã phê duyệt | 2024-02-01 |
| Trưởng phòng Marketing | Lê Văn C | Đã phê duyệt | 2024-02-01 |
| Trưởng phòng Vận hành | Phạm Thị D | Đã phê duyệt | 2024-02-01 |

---

# Product Requirements Document (PRD)

## FoodNow App — Phiên bản 1.0

| | |
|---|---|
| **Mã tài liệu** | FN-PRD-001 |
| **Phiên bản** | 1.0 |
| **Ngày soạn thảo** | 2024-02-10 |
| **Người soạn thảo** | Nguyễn Văn A — Business Analyst |
| **Tài liệu gốc liên quan** | FN-BRD-001 |

## 1. Tóm tắt sản phẩm

FoodNow App là ứng dụng di động cho phép khách hàng của chuỗi nhà hàng FoodNow đặt món, thanh
toán, và theo dõi đơn hàng trực tiếp — không qua nền tảng giao đồ ăn bên thứ ba, đi kèm hệ thống
quản trị web cho nhân viên chi nhánh xử lý đơn hàng.

## 2. Đối tượng người dùng & Persona

**Persona 1 — "Chị Hương" (Khách hàng thân thiết)**: 32 tuổi, nhân viên văn phòng, đặt đồ ăn trưa
3-4 lần/tuần. Ưu tiên tốc độ đặt hàng, theo dõi đơn, tích điểm đổi ưu đãi.

**Persona 2 — "Anh Tùng" (Nhân viên chi nhánh)**: 24 tuổi, thu ngân kiêm xử lý đơn hàng tại chi
nhánh Quận 1. Ưu tiên nhận đơn rõ ràng, nhanh, không phải vừa nghe điện thoại vừa ghi chép tay.

## 3. Danh sách tính năng (theo Epic)

**Epic A — Đặt món & Thanh toán**: xem thực đơn, giỏ hàng, chọn giao nhận, thanh toán online/COD,
áp dụng mã giảm giá.

**Epic B — Theo dõi đơn hàng**: trạng thái real-time, thông báo đẩy, lịch sử đơn hàng.

**Epic C — Chương trình khách hàng thân thiết**: tích điểm tự động, xem điểm/lịch sử, đổi điểm lấy
ưu đãi.

**Epic D — Quản trị đơn hàng**: nhận thông báo đơn mới, xác nhận/từ chối, cập nhật trạng thái, báo
cáo doanh thu.

## 4. Yêu cầu phi chức năng (tổng quan)

| Nhóm | Yêu cầu tổng quan |
|---|---|
| Hiệu năng | Thao tác chính phản hồi dưới 2 giây |
| Bảo mật | Dữ liệu thanh toán/cá nhân được mã hoá, tuân thủ quy định bảo vệ dữ liệu |
| Khả năng mở rộng | Chịu tải gấp 3 lần hiện tại khi mở rộng chi nhánh |

## 5. Ưu tiên hoá tính năng (MoSCoW)

| Tính năng | Mức ưu tiên |
|---|---|
| Đặt món, thanh toán (Epic A) | Must have |
| Theo dõi đơn hàng real-time (Epic B) | Must have |
| Quản trị đơn hàng (Epic D) | Must have |
| Chương trình khách hàng thân thiết (Epic C) | Should have |
| Đặt bàn trước tại quán | Won't have (phiên bản 1.0) |
| Đa ngôn ngữ | Won't have (phiên bản 1.0) |

## 6. Lộ trình phát hành sơ bộ

| Giai đoạn | Nội dung | Thời gian dự kiến |
|---|---|---|
| Increment 1 | Epic A — thử nghiệm 2 chi nhánh | Tháng 1-2 |
| Increment 2 | Epic B + D — mở rộng 12 chi nhánh | Tháng 3-4 |
| Increment 3 | Epic C — ra mắt công khai đầy đủ | Tháng 5-6 |

## 7. Chỉ số đo lường thành công của sản phẩm

- Tỷ lệ hoàn tất đặt hàng ≥ 60%.
- Thời gian trung bình hoàn tất đơn hàng < 2 phút.
- Tỷ lệ khách hàng quay lại đặt đơn thứ 2 trong vòng 30 ngày ≥ 35%.
