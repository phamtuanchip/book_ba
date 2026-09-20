# Software Requirements Specification (SRS)

## FoodNow App — Module: Đặt món & Thanh toán

| | |
|---|---|
| **Mã tài liệu** | FN-SRS-001 |
| **Phiên bản** | 1.0 |
| **Ngày soạn thảo** | 2024-02-20 |
| **Người soạn thảo** | Nguyễn Văn A — Business Analyst |
| **Tài liệu tham chiếu** | FN-BRD-001, FN-PRD-001 |

*(Cấu trúc theo chuẩn IEEE 830, rút gọn cho phù hợp thực tế — xem giải thích cấu trúc đầy đủ ở
Chương 20 sách chính.)*

---

## 1. Giới thiệu

### 1.1 Mục đích

Tài liệu này đặc tả chi tiết yêu cầu chức năng và phi chức năng cho module "Đặt món & Thanh toán"
của FoodNow App, làm cơ sở cho đội phát triển hiện thực và đội kiểm thử xây dựng test case.

### 1.2 Phạm vi

Module bao gồm: xem thực đơn, quản lý giỏ hàng, chọn phương thức giao nhận, thanh toán, áp dụng mã
giảm giá. Không bao gồm: theo dõi đơn hàng sau khi đặt (xem FN-SRS-002), chương trình khách hàng
thân thiết (xem FN-SRS-003).

### 1.3 Định nghĩa & thuật ngữ

| Thuật ngữ | Giải thích |
|---|---|
| Giỏ hàng (Cart) | Danh sách món khách hàng đã chọn nhưng chưa thanh toán |
| COD | Cash On Delivery — thanh toán tiền mặt khi nhận hàng |
| Đơn hàng (Order) | Giỏ hàng sau khi đã hoàn tất thanh toán, được gửi đến chi nhánh xử lý |

## 2. Mô tả tổng quan

Module vận hành trên ứng dụng di động (iOS/Android). Khách hàng tương tác trực tiếp; hệ thống
tương tác với cổng thanh toán bên thứ ba (VNPay) và hệ thống quản trị chi nhánh (nhận đơn hàng mới).

## 3. Yêu cầu chức năng

### 3.1 Xem thực đơn & Giỏ hàng

**FR-CART-01**: Hệ thống PHẢI hiển thị danh sách món ăn theo danh mục (Khai vị, Món chính, Tráng
miệng, Đồ uống), mỗi món hiển thị tên, ảnh, giá, mô tả ngắn.

**FR-CART-02**: Hệ thống PHẢI cho phép khách hàng thêm một món vào giỏ hàng với số lượng tuỳ chọn
(tối thiểu 1, tối đa 20 một loại món).

**FR-CART-03**: Hệ thống PHẢI cho phép khách hàng sửa số lượng hoặc xoá một món khỏi giỏ hàng bất
kỳ lúc nào trước khi thanh toán.

**FR-CART-04**: Nếu một món trong giỏ hàng hết hàng tại chi nhánh được chọn (dữ liệu tồn kho cập
nhật real-time), hệ thống PHẢI thông báo cho khách hàng và yêu cầu xoá hoặc thay thế món đó trước
khi tiếp tục thanh toán.

### 3.2 Chọn phương thức giao nhận

**FR-DELIVERY-01**: Hệ thống PHẢI cho phép khách hàng chọn một trong hai hình thức: (a) giao hàng
tận nơi — yêu cầu nhập/chọn địa chỉ, (b) lấy tại quán — yêu cầu chọn chi nhánh.

**FR-DELIVERY-02**: Nếu chọn giao hàng tận nơi, hệ thống PHẢI tự động xác định chi nhánh gần nhất
có thể phục vụ địa chỉ đó (bán kính phục vụ tối đa 5km); nếu không có chi nhánh nào trong bán kính
phục vụ, hệ thống PHẢI thông báo rõ và không cho phép tiếp tục đặt hàng.

### 3.3 Thanh toán

**FR-PAY-01**: Hệ thống PHẢI cho phép khách hàng thanh toán bằng thẻ nội địa/quốc tế hoặc ví điện
tử (MoMo, ZaloPay) thông qua cổng thanh toán VNPay.

**FR-PAY-02**: Hệ thống PHẢI cho phép khách hàng chọn thanh toán tiền mặt khi nhận hàng (COD) chỉ
áp dụng cho hình thức giao hàng tận nơi, không áp dụng cho lấy tại quán.

**FR-PAY-03**: Nếu giao dịch thanh toán online thất bại, hệ thống PHẢI hiển thị thông báo lỗi rõ
ràng, giữ nguyên giỏ hàng, và cho phép khách hàng thử lại hoặc chọn phương thức thanh toán khác.

**FR-PAY-04**: Hệ thống PHẢI cho phép khách hàng nhập một mã giảm giá hợp lệ trước khi xác nhận
thanh toán; hệ thống chỉ chấp nhận tối đa 1 mã giảm giá cho mỗi đơn hàng (quyết định XP — xem ví
dụ Chương 9).

**FR-PAY-05**: Sau khi thanh toán thành công (hoặc xác nhận COD), hệ thống PHẢI tạo đơn hàng và
gửi thông báo đến hệ thống quản trị của chi nhánh tương ứng trong vòng dưới 5 giây.

## 4. Yêu cầu giao diện bên ngoài

**EXT-01**: Hệ thống tích hợp với cổng thanh toán VNPay qua API REST — theo tài liệu tích hợp
VNPay phiên bản mới nhất tại thời điểm phát triển.

**EXT-02**: Hệ thống gửi dữ liệu đơn hàng mới đến Hệ thống quản trị chi nhánh qua API nội bộ
(chi tiết endpoint xem tài liệu thiết kế kỹ thuật riêng, ngoài phạm vi SRS này).

## 5. Yêu cầu phi chức năng

*(Danh sách rút gọn — xem đầy đủ tại Chương 21 và Phụ lục B)*

| ID | Yêu cầu | Ghi chú |
|---|---|---|
| NFR-01 | Màn hình thực đơn tải xong dưới 2 giây với kết nối 4G | Đo bằng công cụ kiểm thử hiệu năng chuẩn |
| NFR-02 | Thông tin thẻ thanh toán không được lưu trữ trực tiếp trên hệ thống FoodNow, chỉ qua tokenization của cổng thanh toán | Yêu cầu bảo mật bắt buộc |
| NFR-03 | Hệ thống chịu tải tối thiểu 500 đơn hàng đồng thời trong giờ cao điểm | Kiểm thử tải trước go-live |

## 6. Phụ lục

Sơ đồ Activity Diagram cho luồng đặt món & thanh toán: xem Chương 15, mục 15.3 (dùng chung làm sơ
đồ tham chiếu cho tài liệu này).
