# RAID Log — FoodNow App

| | |
|---|---|
| **Dự án** | FoodNow App |
| **Người phụ trách cập nhật** | Nguyễn Văn A — Business Analyst |
| **Cập nhật lần cuối** | 2024-03-15 |

| ID | Loại | Mô tả | Xác suất/Trạng thái | Tác động | Người phụ trách | Biện pháp xử lý | Ngày cập nhật |
|---|---|---|---|---|---|---|---|
| R-01 | Risk | Khách hàng ngại chuyển từ app bên thứ ba sang app riêng | Cao | Cao | Phòng Marketing | Chương trình khuyến mãi ra mắt, ưu đãi độc quyền trên app riêng | 2024-03-01 |
| R-02 | Risk | Đội Dev thiếu kinh nghiệm tích hợp cổng thanh toán, có thể trễ tiến độ Increment 1 | Trung bình | Cao | Trưởng nhóm Dev | Ưu tiên làm module thanh toán ở sprint đầu tiên để phát hiện rủi ro sớm | 2024-02-10 |
| A-01 | Assumption | Toàn bộ 12 chi nhánh có kết nối Internet ổn định để dùng hệ thống quản trị | Chưa xác minh | Cao nếu sai | BA | Khảo sát thực tế từng chi nhánh trước Increment 2 | 2024-03-01 |
| A-02 | Assumption | Khách hàng mục tiêu chủ yếu dùng smartphone iOS/Android, không cần hỗ trợ feature phone | Đã xác minh đúng | — | BA | Đã khảo sát 200 khách hàng thân thiết, 98% dùng smartphone | 2024-02-20 |
| I-01 | Issue | Chi nhánh Quận 7 mất kết nối Internet thường xuyên vào giờ cao điểm | Đã xảy ra | Trung bình | IT Admin | Lắp đặt đường truyền dự phòng (4G backup) trước Increment 2 | 2024-03-15 |
| D-01 | Dependency | Tích hợp VNPay phụ thuộc phê duyệt tài khoản merchant, dự kiến 2 tuần xử lý | Đang xử lý | Cao nếu trễ | BA + Trưởng nhóm Dev | Nộp hồ sơ đăng ký merchant ngay từ tuần đầu dự án | 2024-02-05 |
| D-02 | Dependency | Đào tạo nhân viên 12 chi nhánh phụ thuộc lịch làm việc thực tế của từng chi nhánh | Đang lên lịch | Trung bình | Phòng Vận hành | Lên lịch đào tạo theo ca, tránh giờ cao điểm | 2024-03-10 |

*(Xem cách phân loại và ưu tiên hoá RAID Log đầy đủ tại Chương 31.)*
