# Sign-off Document — Increment 1

## FoodNow App — Epic A: Đặt món & Thanh toán

| | |
|---|---|
| **Mã tài liệu** | FN-SO-001 |
| **Ngày trình sign-off** | 2024-04-28 |
| **Người trình** | Nguyễn Văn A — Business Analyst |
| **Tài liệu căn cứ** | FN-BRD-001, FN-SRS-001, Kết quả UAT (`templates/uat/FoodNow-UAT-Checklist.md`) |

---

## 1. Tóm tắt kết quả UAT

- Tổng số kịch bản kiểm thử: 11
- Đạt: 9
- Không đạt (đã sửa và test lại, đạt): 1 (UAT-06 — thông báo lỗi thanh toán ban đầu chưa rõ ràng,
  đã cập nhật nội dung thông báo, test lại đạt)
- Không đạt (còn tồn đọng): 1 (UAT-09 — thông báo lỗi mã giảm giá hết hạn hiển thị đúng nhưng chưa
  đúng theo bộ nhận diện thương hiệu; đánh giá là vấn đề nhỏ, không ảnh hưởng chức năng)

## 2. Đề xuất

Đề xuất **sign-off có điều kiện**: cho phép go-live Increment 1 tại 2 chi nhánh thí điểm đúng kế
hoạch, với điều kiện vấn đề UAT-09 được khắc phục trong vòng 1 tuần sau go-live (không chặn go-live
vì không ảnh hưởng chức năng cốt lõi).

## 3. Vấn đề còn tồn đọng và kế hoạch xử lý

| ID | Mô tả | Mức độ | Kế hoạch xử lý | Hạn xử lý |
|---|---|---|---|---|
| UAT-09 | Giao diện thông báo lỗi mã giảm giá hết hạn chưa đúng bộ nhận diện thương hiệu | Thấp | Designer cập nhật giao diện thông báo lỗi | 2024-05-05 |

## 4. Xác nhận Sign-off

| Vai trò | Họ tên | Quyết định | Ngày |
|---|---|---|---|
| Sponsor (Giám đốc điều hành) | Trần Thị B | Đồng ý, có điều kiện (xem mục 3) | 2024-04-28 |
| Quản lý chi nhánh Quận 1 | *(đại diện chi nhánh thí điểm)* | Đồng ý | 2024-04-28 |
| Quản lý chi nhánh Quận 3 | *(đại diện chi nhánh thí điểm)* | Đồng ý | 2024-04-28 |
| Trưởng nhóm Dev | *(đại diện đội phát triển)* | Xác nhận đã hoàn thành theo SRS | 2024-04-28 |

*(Xem quy trình đầy đủ tại Chương 35.)*
