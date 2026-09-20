# Incremental Delivery Plan

## FoodNow App

| | |
|---|---|
| **Mã tài liệu** | FN-IDP-001 |
| **Phiên bản** | 1.0 |
| **Ngày soạn thảo** | 2024-02-25 |
| **Người soạn thảo** | Nguyễn Văn A — Business Analyst |
| **Tài liệu liên quan** | FN-BRD-001, FN-PRD-001 |

---

## 1. Tổng quan

Kế hoạch này chia việc phát triển FoodNow App thành 3 increment, mỗi increment mang lại giá trị sử
dụng được ngay, theo chiến lược kết hợp "theo tính năng" và "theo phân khúc người dùng" (mở rộng
dần từ 2 chi nhánh thí điểm ra toàn bộ 12 chi nhánh). Mục tiêu: kiểm chứng sớm các giả định quan
trọng (khách hàng có chấp nhận dùng app riêng không, quy trình vận hành tại chi nhánh có phù hợp
không) trước khi đầu tư toàn bộ ngân sách.

## 2. Bảng chi tiết các Increment

### Increment 1: Nền tảng đặt món & thanh toán (thí điểm)

| | |
|---|---|
| **Nội dung** | Epic A — Đặt món & Thanh toán (US-101 đến US-106) |
| **Đối tượng nhận** | Khách hàng tại 2 chi nhánh thí điểm (Quận 1, Quận 3) |
| **Thời gian dự kiến** | Tháng 3-4 (2 tháng) |
| **Tiêu chí thành công để chuyển sang Increment 2** | Tỷ lệ hoàn tất đặt hàng (conversion) đạt tối thiểu 50%; không có lỗi nghiêm trọng (critical bug) nào tồn đọng quá 48 giờ; phản hồi từ 2 chi nhánh thí điểm không có vấn đề vận hành lớn |
| **Rủi ro chính** | Tích hợp cổng thanh toán VNPay phức tạp hơn dự kiến — giảm thiểu bằng cách ưu tiên làm sprint đầu tiên |

### Increment 2: Theo dõi đơn hàng & Quản trị chi nhánh (mở rộng toàn bộ)

| | |
|---|---|
| **Nội dung** | Epic B — Theo dõi đơn hàng (US-201 đến US-204), Epic D — Quản trị đơn hàng (US-301 đến US-304) |
| **Đối tượng nhận** | Toàn bộ 12 chi nhánh |
| **Thời gian dự kiến** | Tháng 5 (đầu tháng 5 đến giữa tháng 6) |
| **Tiêu chí thành công để chuyển sang Increment 3** | 12/12 chi nhánh vận hành ổn định qua hệ thống quản trị mới trong tối thiểu 2 tuần liên tục; tỷ lệ đơn hàng bị xử lý sai/khiếu nại dưới 2% |
| **Rủi ro chính** | Nhân viên các chi nhánh còn lại (10 chi nhánh chưa thí điểm) cần thời gian đào tạo — giảm thiểu bằng kế hoạch đào tạo chi tiết ở mục 4 |

### Increment 3: Chương trình khách hàng thân thiết (ra mắt công khai đầy đủ)

| | |
|---|---|
| **Nội dung** | Epic C — Chương trình khách hàng thân thiết (US-401 đến US-406) |
| **Đối tượng nhận** | Toàn bộ khách hàng, công khai trên App Store/Google Play |
| **Thời gian dự kiến** | Tháng 6-7 (giữa tháng 6 đến cuối tháng 7) |
| **Tiêu chí thành công** | Đạt các chỉ số ở BRD mục "Tiêu chí thành công" (FN-BRD-001): 40% tỷ trọng đơn qua app riêng trong 6 tháng, biên lợi nhuận tăng 15% trong 12 tháng |
| **Rủi ro chính** | Khách hàng có thể chưa quen thao tác tích/đổi điểm — giảm thiểu bằng hướng dẫn trong app (onboarding) và chương trình khuyến mãi ra mắt |

## 3. Timeline trực quan

*(Xem sơ đồ Gantt tại Chương 29, mục 29.3 — dùng chung làm sơ đồ tham chiếu cho tài liệu này.)*

## 4. Kế hoạch truyền thông/đào tạo đi kèm

| Increment | Đối tượng đào tạo | Nội dung | Thời điểm |
|---|---|---|---|
| 1 | Nhân viên 2 chi nhánh thí điểm | Sử dụng hệ thống quản trị đơn hàng cơ bản | Tuần cuối trước go-live Increment 1 |
| 2 | Nhân viên 10 chi nhánh còn lại | Sử dụng hệ thống quản trị đơn hàng đầy đủ | 2 tuần trước go-live Increment 2 |
| 2 | Toàn bộ khách hàng hiện tại (qua email/SMS) | Giới thiệu app mới, hướng dẫn tải và đặt hàng lần đầu | Trùng thời điểm go-live Increment 2 |
| 3 | Toàn bộ khách hàng | Giới thiệu chương trình tích điểm, cách đổi ưu đãi | Trùng thời điểm go-live Increment 3 |

## 5. Điều kiện điều chỉnh kế hoạch

Mọi thay đổi về nội dung hoặc thứ tự các increment phải qua quy trình Change Request (xem Chương
18), được phê duyệt bởi Ban giám đốc (đối với thay đổi ảnh hưởng phạm vi/ngân sách tổng thể) hoặc
Product Owner (đối với điều chỉnh thứ tự ưu tiên trong phạm vi ngân sách đã duyệt).
