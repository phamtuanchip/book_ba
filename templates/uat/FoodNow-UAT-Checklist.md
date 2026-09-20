# UAT Checklist — FoodNow App, Increment 1 (Đặt món & Thanh toán)

| | |
|---|---|
| **Dự án** | FoodNow App |
| **Phạm vi UAT** | Increment 1 — Epic A: Đặt món & Thanh toán |
| **Người tham gia UAT** | 2 nhân viên chi nhánh thí điểm (Quận 1, Quận 3), 5 khách hàng thân thiết tình nguyện, 1 đại diện Phòng Marketing |
| **Thời gian thực hiện** | 2024-04-20 đến 2024-04-26 |
| **Người điều phối** | Nguyễn Văn A — Business Analyst |

## Hướng dẫn sử dụng checklist

Với mỗi kịch bản, người tham gia UAT thực hiện thao tác thực tế trên ứng dụng, đánh dấu Đạt/Không
đạt, và ghi chú chi tiết nếu Không đạt. Mọi mục "Không đạt" cần được BA phân loại: lỗi cần sửa
trước go-live, hay cải tiến có thể làm ở increment sau (xem Chương 34, mục 34.4).

## Danh sách kịch bản kiểm thử

| ID | Kịch bản | Liên kết yêu cầu | Đạt/Không đạt | Ghi chú |
|---|---|---|---|---|
| UAT-01 | Khách hàng xem thực đơn theo danh mục, tìm được món mong muốn trong dưới 30 giây | US-101 | | |
| UAT-02 | Khách hàng thêm 3 món khác nhau vào giỏ hàng, sửa số lượng 1 món, xoá 1 món — giỏ hàng cập nhật đúng | US-102 | | |
| UAT-03 | Khách hàng chọn giao hàng tận nơi, nhập địa chỉ trong bán kính phục vụ — hệ thống xác định đúng chi nhánh xử lý | US-103, FR-DELIVERY-02 | | |
| UAT-04 | Khách hàng chọn địa chỉ ngoài bán kính phục vụ — hệ thống thông báo rõ ràng, không cho tiếp tục | FR-DELIVERY-02 (exception) | | |
| UAT-05 | Khách hàng thanh toán bằng thẻ qua VNPay thành công, đơn hàng được tạo | US-104 | | |
| UAT-06 | Khách hàng nhập sai thông tin thẻ, giao dịch thất bại — hệ thống thông báo lỗi rõ ràng, giữ nguyên giỏ hàng | FR-PAY-03 | | |
| UAT-07 | Khách hàng chọn thanh toán COD cho đơn giao tận nơi — đơn hàng tạo thành công với trạng thái "Chờ thanh toán khi giao" | US-105, FR-PAY-02 | | |
| UAT-08 | Khách hàng nhập mã giảm giá hợp lệ — tổng tiền giảm đúng theo mã | US-106 | | |
| UAT-09 | Khách hàng nhập mã giảm giá đã hết hạn — hệ thống thông báo lỗi, tổng tiền không đổi | US-106 (exception) | | |
| UAT-10 | Nhân viên chi nhánh nhận thông báo đơn hàng mới trong vòng dưới 5 giây sau khi khách thanh toán | FR-PAY-05 | | |
| UAT-11 | Toàn bộ luồng đặt món - thanh toán (happy path) hoàn tất trong dưới 2 phút | BR-01 | | |

## Tổng hợp kết quả

| Tổng số kịch bản | Đạt | Không đạt (cần sửa trước go-live) | Không đạt (cải tiến làm sau) |
|---|---|---|---|
| 11 | | | |

## Kết luận & đề xuất

*(BA điền sau khi tổng hợp: sản phẩm đủ điều kiện go-live Increment 1 hay cần thêm thời gian sửa
lỗi. Nếu đủ điều kiện, chuyển sang quy trình Sign-off — xem `templates/sign-off/` và Chương 35.)*
