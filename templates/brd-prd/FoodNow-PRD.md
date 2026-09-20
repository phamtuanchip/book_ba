# Product Requirements Document (PRD)

## FoodNow App — Phiên bản 1.0

| | |
|---|---|
| **Mã tài liệu** | FN-PRD-001 |
| **Phiên bản** | 1.0 |
| **Ngày soạn thảo** | 2024-02-10 |
| **Người soạn thảo** | Nguyễn Văn A — Business Analyst |
| **Tài liệu gốc liên quan** | FN-BRD-001 |

---

## 1. Tóm tắt sản phẩm

FoodNow App là ứng dụng di động cho phép khách hàng của chuỗi nhà hàng FoodNow đặt món, thanh
toán, và theo dõi đơn hàng trực tiếp — không qua nền tảng giao đồ ăn bên thứ ba. Đi kèm là hệ
thống quản trị web cho nhân viên chi nhánh xử lý đơn hàng. Sản phẩm nhằm đạt các mục tiêu kinh
doanh BO-01, BO-02, BO-03 đã nêu trong BRD (FN-BRD-001).

## 2. Đối tượng người dùng & Persona

### Persona 1: "Chị Hương" — Khách hàng thân thiết

- 32 tuổi, nhân viên văn phòng, đặt đồ ăn trưa 3-4 lần/tuần.
- Ưu tiên: tốc độ đặt hàng nhanh, theo dõi được đơn hàng, tích điểm để đổi ưu đãi.
- Điểm đau hiện tại: phải mở nhiều app để so sánh, không tích điểm được vì mỗi lần đặt qua nền
  tảng khác nhau.

### Persona 2: "Anh Tùng" — Nhân viên chi nhánh

- 24 tuổi, thu ngân kiêm xử lý đơn hàng tại chi nhánh Quận 1.
- Ưu tiên: nhận đơn hàng rõ ràng, nhanh, không phải nghe điện thoại liên tục trong giờ cao điểm.
- Điểm đau hiện tại: phải vừa nghe điện thoại, vừa ghi chép tay, dễ nhầm lẫn món/địa chỉ khi đông khách.

## 3. Danh sách tính năng (theo Epic)

### Epic A: Đặt món & Thanh toán

- Xem thực đơn theo danh mục, tìm kiếm món.
- Thêm/sửa/xoá món trong giỏ hàng.
- Chọn địa chỉ giao hàng hoặc lấy tại quán.
- Thanh toán online (thẻ, ví điện tử) hoặc tiền mặt khi nhận hàng.
- Áp dụng mã giảm giá.

### Epic B: Theo dõi đơn hàng

- Xem trạng thái đơn hàng real-time (Đã đặt → Đã xác nhận → Đang chuẩn bị → Đang giao → Đã giao).
- Nhận thông báo đẩy (push notification) khi trạng thái thay đổi.
- Xem lịch sử đơn hàng đã đặt.

### Epic C: Chương trình khách hàng thân thiết

- Tích điểm tự động theo giá trị đơn hàng.
- Xem số điểm hiện có, lịch sử tích/đổi điểm.
- Đổi điểm lấy ưu đãi (giảm giá, món miễn phí).

### Epic D: Quản trị đơn hàng (dành cho nhân viên chi nhánh)

- Nhận thông báo đơn hàng mới ngay lập tức.
- Xác nhận hoặc từ chối đơn hàng (kèm lý do).
- Cập nhật trạng thái xử lý đơn hàng.
- Xem báo cáo doanh thu, số đơn theo ngày/tuần/tháng (dành cho quản lý chi nhánh và Ban giám đốc).

## 4. Yêu cầu phi chức năng (tổng quan)

| Nhóm | Yêu cầu tổng quan | Chi tiết đầy đủ |
|---|---|---|
| Hiệu năng | Các thao tác chính (xem thực đơn, thêm giỏ hàng, thanh toán) phản hồi dưới 2 giây | Xem SRS FN-SRS-001, mục Non-functional Requirements |
| Bảo mật | Thông tin thanh toán và dữ liệu cá nhân khách hàng phải được mã hoá, tuân thủ quy định bảo vệ dữ liệu | Xem SRS FN-SRS-001 |
| Khả năng mở rộng | Hệ thống chịu tải được lượng đơn hàng gấp 3 lần hiện tại khi mở rộng thêm chi nhánh | Xem SRS FN-SRS-001 |

## 5. Ưu tiên hoá tính năng (MoSCoW)

| Tính năng | Mức ưu tiên |
|---|---|
| Đặt món, thanh toán (Epic A) | Must have |
| Theo dõi đơn hàng real-time (Epic B) | Must have |
| Quản trị đơn hàng cho nhân viên chi nhánh (Epic D) | Must have |
| Chương trình khách hàng thân thiết (Epic C) | Should have |
| Đặt bàn trước tại quán | Won't have (phiên bản 1.0) — xem BRD mục "Ngoài phạm vi" |
| Đa ngôn ngữ | Won't have (phiên bản 1.0) |

*(Xem chi tiết kỹ thuật MoSCoW tại Chương 26.)*

## 6. Lộ trình phát hành sơ bộ

| Giai đoạn | Nội dung | Thời gian dự kiến |
|---|---|---|
| Increment 1 | Epic A (Đặt món & Thanh toán) — phát hành nội bộ thử nghiệm tại 2 chi nhánh | Tháng 1-2 |
| Increment 2 | Epic B (Theo dõi đơn hàng) + Epic D (Quản trị đơn hàng) — mở rộng toàn bộ 12 chi nhánh | Tháng 3-4 |
| Increment 3 | Epic C (Khách hàng thân thiết) — phát hành công khai đầy đủ | Tháng 5-6 |

*(Xem kế hoạch giao hàng đầy đủ tại Phụ lục D — Incremental Delivery Plan, Chương 28-29.)*

## 7. Chỉ số đo lường thành công của sản phẩm

- Tỷ lệ hoàn tất đặt hàng (conversion rate từ mở app đến thanh toán thành công) đạt tối thiểu 60%.
- Thời gian trung bình hoàn tất một đơn hàng dưới 2 phút.
- Tỷ lệ khách hàng quay lại đặt đơn thứ 2 trong vòng 30 ngày đạt tối thiểu 35%.
