# Chương 22: Use Case Specification: actor, flow chính/phụ, exception, mẫu

## Mục tiêu học

- Nắm được cấu trúc chuẩn của một Use Case Specification.
- Viết được Main Flow (luồng chính), Alternate Flow (luồng phụ), và Exception Flow (luồng ngoại lệ)
  cho một use case cụ thể.
- Biết mức độ chi tiết phù hợp — không quá sơ sài, không quá rườm rà.

## 22.1 Use Case Specification là gì?

Nếu Use Case Diagram (Chương 15) cho cái nhìn tổng quan "có những chức năng gì, ai dùng", **Use
Case Specification** đi sâu mô tả **từng bước tương tác cụ thể** giữa actor và hệ thống cho MỘT
use case, bao gồm cả những gì xảy ra khi mọi thứ suôn sẻ (main flow) và khi có vấn đề phát sinh
(alternate/exception flow).

## 22.2 Cấu trúc chuẩn

| Mục | Nội dung |
|---|---|
| **Tên Use Case** | Ngắn gọn, dạng động từ + tân ngữ (ví dụ: "Đặt món") |
| **ID** | Để truy vết (liên hệ RTM — Chương 16) |
| **Actor chính** | Ai khởi tạo use case này |
| **Actor phụ** | Hệ thống/vai trò khác tham gia (nếu có) |
| **Mô tả ngắn** | 1-2 câu tóm tắt mục đích |
| **Điều kiện tiên quyết (Precondition)** | Trạng thái hệ thống phải có trước khi use case bắt đầu |
| **Điều kiện kết thúc (Postcondition)** | Trạng thái hệ thống sau khi use case hoàn tất thành công |
| **Luồng chính (Main Flow)** | Các bước khi mọi thứ diễn ra suôn sẻ (happy path) |
| **Luồng phụ (Alternate Flow)** | Các nhánh khác vẫn dẫn đến kết quả thành công, nhưng đi đường khác |
| **Luồng ngoại lệ (Exception Flow)** | Các trường hợp lỗi, dẫn đến use case không hoàn thành như mong đợi |
| **Yêu cầu đặc biệt** | Ràng buộc phi chức năng riêng cho use case này (nếu có) |

## 22.3 Ví dụ đầy đủ: Use Case "Đặt món và thanh toán" (FoodNow)

> **UC-01: Đặt món và thanh toán**
>
> **Actor chính**: Khách hàng
> **Actor phụ**: Cổng thanh toán VNPay, Hệ thống quản trị chi nhánh
>
> **Mô tả ngắn**: Khách hàng chọn món, thêm vào giỏ hàng, chọn hình thức giao nhận, và hoàn tất
> thanh toán để tạo đơn hàng.
>
> **Điều kiện tiên quyết**: Khách hàng đã đăng nhập hoặc đặt hàng dưới dạng khách vãng lai (guest).
>
> **Điều kiện kết thúc**: Đơn hàng được tạo thành công và gửi đến hệ thống quản trị chi nhánh.
>
> **Luồng chính (Main Flow)**:
> 1. Khách hàng mở app, xem danh sách món theo danh mục.
> 2. Khách hàng chọn món, thêm vào giỏ hàng với số lượng mong muốn.
> 3. Khách hàng xem lại giỏ hàng, xác nhận tiếp tục.
> 4. Khách hàng chọn hình thức giao nhận: giao tận nơi hoặc lấy tại quán.
> 5. Nếu giao tận nơi, khách hàng nhập/chọn địa chỉ.
> 6. Khách hàng chọn phương thức thanh toán (online hoặc COD).
> 7. Nếu online, hệ thống chuyển hướng đến cổng thanh toán VNPay, khách hàng hoàn tất giao dịch.
> 8. Hệ thống xác nhận thanh toán thành công, tạo đơn hàng.
> 9. Hệ thống gửi đơn hàng đến hệ thống quản trị chi nhánh tương ứng.
> 10. Hệ thống hiển thị màn hình xác nhận đơn hàng thành công cho khách hàng.
>
> **Luồng phụ (Alternate Flow)**:
> - **3a. Khách hàng muốn sửa giỏ hàng**: quay lại bước 2, sau khi sửa xong tiếp tục từ bước 3.
> - **6a. Khách hàng nhập mã giảm giá hợp lệ trước khi thanh toán**: hệ thống áp dụng giảm giá vào
>   tổng tiền, tiếp tục từ bước 6.
> - **6b. Khách hàng chọn thanh toán COD**: bỏ qua bước 7 (không cần cổng thanh toán), chuyển
>   thẳng đến bước 8, đơn hàng được tạo với trạng thái "Chờ thanh toán khi giao".
>
> **Luồng ngoại lệ (Exception Flow)**:
> - **4a. Một món trong giỏ hàng hết hàng tại chi nhánh được chọn**: hệ thống thông báo, yêu cầu
>   khách hàng xoá hoặc thay thế món đó trước khi tiếp tục (liên hệ FR-CART-04, Chương 20).
> - **5a. Địa chỉ giao hàng nằm ngoài bán kính phục vụ của mọi chi nhánh**: hệ thống thông báo
>   không thể giao đến địa chỉ này, không cho phép tiếp tục (liên hệ FR-DELIVERY-02).
> - **7a. Giao dịch thanh toán online thất bại**: hệ thống hiển thị lỗi, giữ nguyên giỏ hàng, quay
>   lại bước 6 để khách hàng thử lại hoặc chọn phương thức khác (liên hệ FR-PAY-03).
>
> **Yêu cầu đặc biệt**: Toàn bộ luồng từ bước 1 đến bước 10 (trường hợp happy path) phải hoàn tất
> trong dưới 2 phút theo thao tác thông thường của người dùng (liên hệ BR-01, Chương 19).

## 22.4 Mức độ chi tiết phù hợp

Use Case Specification không cần chi tiết đến mức mô tả từng pixel giao diện (đó là việc của
wireframe — Chương 25) — tập trung vào **luồng logic tương tác và các quyết định rẽ nhánh**. Một
dấu hiệu use case viết vừa đủ chi tiết: một Dev mới, chưa từng nghe về dự án, đọc xong có thể tự
tin liệt kê được toàn bộ các trường hợp cần code (kể cả các trường hợp ngoại lệ) mà không cần hỏi
lại thêm.

## Bài tập

1. Viết đầy đủ Use Case Specification cho "UC-03: Theo dõi đơn hàng" của FoodNow, theo cấu trúc ở
   mục 22.2 — bao gồm ít nhất 1 luồng phụ và 1 luồng ngoại lệ.
2. Với Use Case "UC-01: Đặt món và thanh toán" ở mục 22.3, thử tìm thêm ít nhất 1 luồng ngoại lệ
   chưa được liệt kê (gợi ý: điều gì xảy ra nếu khách hàng thoát app giữa chừng khi đang thanh toán?).

## Sai lầm thường gặp

- **Chỉ viết luồng chính, bỏ qua luồng ngoại lệ**: đây là nguyên nhân phổ biến nhất của lỗi phát
  sinh khi test (Chương 34) — Dev không được thông báo trước nên phải tự đoán xử lý ra sao.
- **Viết use case quá chi tiết đến mức giao diện cụ thể**: làm tài liệu cồng kềnh, khó bảo trì khi
  giao diện thay đổi (mà logic nghiệp vụ không đổi) — tách riêng phần giao diện sang wireframe.
- **Không liên kết use case với yêu cầu chức năng cụ thể trong SRS**: làm mất khả năng truy vết —
  luôn ghi rõ ID yêu cầu liên quan như ví dụ ở mục 22.3.

## Tóm tắt & tiếp theo

Use Case Specification mô tả chi tiết từng bước tương tác actor-hệ thống cho một use case cụ thể,
gồm luồng chính, luồng phụ, và luồng ngoại lệ — quan trọng nhất là không bỏ sót các trường hợp
ngoại lệ. Chương 23 sẽ chuyển sang định dạng phổ biến hơn trong các dự án Agile: **User Story và
Acceptance Criteria**, nhẹ hơn Use Case Specification nhưng vẫn cần đủ rõ ràng để Dev hiện thực đúng.
