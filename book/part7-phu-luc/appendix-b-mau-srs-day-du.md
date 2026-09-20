# Phụ lục B: Mẫu SRS đầy đủ theo IEEE 830 (dự án FoodNow)

> Nội dung dưới đây in lại đầy đủ từ file mẫu gốc: `templates/srs/FoodNow-SRS.md`. Xem giải thích
> cấu trúc IEEE 830 và nguyên tắc viết yêu cầu chất lượng cao tại Chương 20.

---

# Software Requirements Specification (SRS)

## FoodNow App — Module: Đặt món & Thanh toán

| | |
|---|---|
| **Mã tài liệu** | FN-SRS-001 |
| **Phiên bản** | 1.0 |
| **Ngày soạn thảo** | 2024-02-20 |
| **Người soạn thảo** | Nguyễn Văn A — Business Analyst |
| **Tài liệu tham chiếu** | FN-BRD-001, FN-PRD-001 |

## 1. Giới thiệu

**Mục đích**: đặc tả chi tiết yêu cầu chức năng và phi chức năng cho module "Đặt món & Thanh toán"
của FoodNow App, làm cơ sở cho đội phát triển hiện thực và đội kiểm thử xây dựng test case.

**Phạm vi**: bao gồm xem thực đơn, quản lý giỏ hàng, chọn phương thức giao nhận, thanh toán, áp
dụng mã giảm giá. Không bao gồm theo dõi đơn hàng (FN-SRS-002) hay chương trình khách hàng thân
thiết (FN-SRS-003).

**Định nghĩa & thuật ngữ**: Giỏ hàng (Cart) — danh sách món chưa thanh toán; COD — Cash On
Delivery; Đơn hàng (Order) — giỏ hàng sau khi hoàn tất thanh toán.

## 2. Mô tả tổng quan

Module vận hành trên ứng dụng di động (iOS/Android). Khách hàng tương tác trực tiếp; hệ thống
tương tác với cổng thanh toán bên thứ ba (VNPay) và hệ thống quản trị chi nhánh.

## 3. Yêu cầu chức năng

**3.1 Xem thực đơn & Giỏ hàng**

- **FR-CART-01**: Hệ thống PHẢI hiển thị danh sách món ăn theo danh mục (Khai vị, Món chính, Tráng
  miệng, Đồ uống), mỗi món hiển thị tên, ảnh, giá, mô tả ngắn.
- **FR-CART-02**: Hệ thống PHẢI cho phép khách hàng thêm một món vào giỏ hàng với số lượng tuỳ chọn
  (tối thiểu 1, tối đa 20 một loại món).
- **FR-CART-03**: Hệ thống PHẢI cho phép khách hàng sửa số lượng hoặc xoá một món khỏi giỏ hàng bất
  kỳ lúc nào trước khi thanh toán.
- **FR-CART-04**: Nếu một món trong giỏ hàng hết hàng tại chi nhánh được chọn, hệ thống PHẢI thông
  báo cho khách hàng và yêu cầu xoá hoặc thay thế món đó trước khi tiếp tục thanh toán.

**3.2 Chọn phương thức giao nhận**

- **FR-DELIVERY-01**: Hệ thống PHẢI cho phép khách hàng chọn giao hàng tận nơi hoặc lấy tại quán.
- **FR-DELIVERY-02**: Nếu chọn giao hàng tận nơi, hệ thống PHẢI tự động xác định chi nhánh gần nhất
  trong bán kính phục vụ tối đa 5km; nếu không có chi nhánh phù hợp, hệ thống PHẢI thông báo rõ và
  không cho phép tiếp tục đặt hàng.

**3.3 Thanh toán**

- **FR-PAY-01**: Hệ thống PHẢI cho phép thanh toán bằng thẻ nội địa/quốc tế hoặc ví điện tử (MoMo,
  ZaloPay) qua cổng thanh toán VNPay.
- **FR-PAY-02**: Hệ thống PHẢI cho phép thanh toán COD, chỉ áp dụng cho giao hàng tận nơi.
- **FR-PAY-03**: Nếu giao dịch online thất bại, hệ thống PHẢI hiển thị lỗi rõ ràng, giữ nguyên giỏ
  hàng, cho phép thử lại hoặc chọn phương thức khác.
- **FR-PAY-04**: Hệ thống PHẢI cho phép nhập một mã giảm giá hợp lệ, tối đa 1 mã/đơn hàng.
- **FR-PAY-05**: Sau khi thanh toán thành công (hoặc xác nhận COD), hệ thống PHẢI tạo đơn hàng và
  gửi thông báo đến hệ thống quản trị chi nhánh trong vòng dưới 5 giây.

## 4. Yêu cầu giao diện bên ngoài

- **EXT-01**: Tích hợp cổng thanh toán VNPay qua API REST.
- **EXT-02**: Gửi dữ liệu đơn hàng mới đến Hệ thống quản trị chi nhánh qua API nội bộ.

## 5. Yêu cầu phi chức năng

| ID | Yêu cầu | Ghi chú |
|---|---|---|
| NFR-01 | Màn hình thực đơn tải xong dưới 2 giây với kết nối 4G | Đo bằng công cụ kiểm thử hiệu năng chuẩn |
| NFR-02 | Thông tin thẻ thanh toán không lưu trực tiếp trên hệ thống FoodNow, chỉ qua tokenization của cổng thanh toán | Yêu cầu bảo mật bắt buộc |
| NFR-03 | Hệ thống chịu tải tối thiểu 500 đơn hàng đồng thời trong giờ cao điểm | Kiểm thử tải trước go-live |

## 6. Phụ lục kỹ thuật

Sơ đồ Activity Diagram cho luồng đặt món & thanh toán: xem Chương 15, mục 15.3.
