# UC-01: Đặt món và thanh toán

| | |
|---|---|
| **Mã Use Case** | UC-01 |
| **Dự án** | FoodNow App |
| **Tài liệu liên quan** | FN-SRS-001 |
| **Người soạn thảo** | Nguyễn Văn A — Business Analyst |

**Actor chính**: Khách hàng
**Actor phụ**: Cổng thanh toán VNPay, Hệ thống quản trị chi nhánh

**Mô tả ngắn**: Khách hàng chọn món, thêm vào giỏ hàng, chọn hình thức giao nhận, và hoàn tất
thanh toán để tạo đơn hàng.

**Điều kiện tiên quyết**: Khách hàng đã đăng nhập hoặc đặt hàng dưới dạng khách vãng lai (guest).

**Điều kiện kết thúc**: Đơn hàng được tạo thành công và gửi đến hệ thống quản trị chi nhánh.

## Luồng chính (Main Flow)

1. Khách hàng mở app, xem danh sách món theo danh mục.
2. Khách hàng chọn món, thêm vào giỏ hàng với số lượng mong muốn.
3. Khách hàng xem lại giỏ hàng, xác nhận tiếp tục.
4. Khách hàng chọn hình thức giao nhận: giao tận nơi hoặc lấy tại quán.
5. Nếu giao tận nơi, khách hàng nhập/chọn địa chỉ.
6. Khách hàng chọn phương thức thanh toán (online hoặc COD).
7. Nếu online, hệ thống chuyển hướng đến cổng thanh toán VNPay, khách hàng hoàn tất giao dịch.
8. Hệ thống xác nhận thanh toán thành công, tạo đơn hàng.
9. Hệ thống gửi đơn hàng đến hệ thống quản trị chi nhánh tương ứng.
10. Hệ thống hiển thị màn hình xác nhận đơn hàng thành công cho khách hàng.

## Luồng phụ (Alternate Flow)

- **3a. Khách hàng muốn sửa giỏ hàng**: quay lại bước 2, sau khi sửa xong tiếp tục từ bước 3.
- **6a. Khách hàng nhập mã giảm giá hợp lệ trước khi thanh toán**: hệ thống áp dụng giảm giá vào
  tổng tiền, tiếp tục từ bước 6.
- **6b. Khách hàng chọn thanh toán COD**: bỏ qua bước 7, chuyển thẳng đến bước 8, đơn hàng được
  tạo với trạng thái "Chờ thanh toán khi giao".

## Luồng ngoại lệ (Exception Flow)

- **4a. Một món trong giỏ hàng hết hàng tại chi nhánh được chọn**: hệ thống thông báo, yêu cầu
  khách hàng xoá hoặc thay thế món đó trước khi tiếp tục (FR-CART-04).
- **5a. Địa chỉ giao hàng nằm ngoài bán kính phục vụ của mọi chi nhánh**: hệ thống thông báo không
  thể giao đến địa chỉ này, không cho phép tiếp tục (FR-DELIVERY-02).
- **7a. Giao dịch thanh toán online thất bại**: hệ thống hiển thị lỗi, giữ nguyên giỏ hàng, quay
  lại bước 6 để khách hàng thử lại hoặc chọn phương thức khác (FR-PAY-03).

## Yêu cầu đặc biệt

Toàn bộ luồng từ bước 1 đến bước 10 (happy path) phải hoàn tất trong dưới 2 phút theo thao tác
thông thường của người dùng (BR-01).
