# Chương 16: Requirements Traceability Matrix (RTM)

## Mục tiêu học

- Giải thích được RTM là gì và giải quyết vấn đề gì.
- Xây dựng được một RTM đơn giản, liên kết từ Business Requirement đến test case.
- Dùng RTM để trả lời 2 câu hỏi quan trọng: "yêu cầu này có bị bỏ sót không?" và "nếu thay đổi yêu
  cầu này, những gì khác bị ảnh hưởng?"

## 16.1 RTM là gì, giải quyết vấn đề gì?

**Requirements Traceability Matrix (RTM)** là một bảng theo dõi, liên kết mỗi yêu cầu với các
"đối tượng" liên quan xuyên suốt vòng đời dự án: yêu cầu đó bắt nguồn từ đâu (nguồn), được thiết
kế ở đâu, được code ở phần nào, được test bởi test case nào. Nói cách khác, RTM là hiện thực hoá
kỹ thuật "truy ngược" đã giới thiệu ở Chương 14, nhưng mở rộng theo cả 2 chiều: **truy ngược lên**
(yêu cầu này từ đâu ra) và **truy xuôi xuống** (yêu cầu này ảnh hưởng đến gì ở các giai đoạn sau).

RTM giải quyết 2 vấn đề lớn:

1. **Không bỏ sót yêu cầu**: mọi yêu cầu trong BRD/SRS đều phải xuất hiện trong RTM, và cuối dự án
   phải có ít nhất một test case xác nhận yêu cầu đó đã được hiện thực đúng — nếu một yêu cầu
   không có dòng nào trong RTM khớp với test case, đó là dấu hiệu yêu cầu đó **có thể đã bị quên**.
2. **Quản lý ảnh hưởng khi có thay đổi (impact analysis)**: khi một yêu cầu thay đổi (Chương 18),
   RTM giúp trả lời nhanh "những use case, thiết kế, đoạn code, test case nào cần xem lại?" thay vì
   phải dò tìm thủ công trong toàn bộ tài liệu.

## 16.2 Cấu trúc một RTM đơn giản

| ID yêu cầu | Mô tả yêu cầu | Nguồn (Business/Stakeholder) | Use Case liên quan | Thiết kế/Module | Test Case ID | Trạng thái |
|---|---|---|---|---|---|---|
| BO-01 | Giảm phụ thuộc app bên thứ ba, tăng biên lợi nhuận | BRD, mục 2 (Ban giám đốc) | — | — | — | Mục tiêu tổng thể |
| BR-01 | Khách hàng đặt và thanh toán trong dưới 2 phút | BO-01 | UC-01 Đặt món | Module Giỏ hàng | TC-01, TC-02 | Đã hiện thực |
| FR-CART-03 | Hệ thống cho phép sửa số lượng hoặc xoá món trong giỏ hàng | BR-01 | UC-01 Đặt món | Module Giỏ hàng | TC-03 | Đã hiện thực |
| FR-PAY-04 | Hệ thống cho phép áp dụng mã giảm giá khi thanh toán | BR-01 | UC-01 Đặt món | Module Thanh toán | TC-05, TC-06 | Đang phát triển |
| NFR-01 | Màn hình thực đơn tải xong dưới 2 giây (4G) | BR-01 | UC-01 Đặt món | Module Giỏ hàng | TC-04 | Chưa test hiệu năng |

Đọc theo hàng ngang, mỗi dòng cho biết **toàn bộ hành trình** của một yêu cầu — từ mục tiêu kinh
doanh (cột "Nguồn"), qua use case, module thiết kế, đến test case xác nhận. Đọc theo cột dọc,
"Trạng thái" giúp nhanh chóng thấy yêu cầu nào còn thiếu bước nào (ví dụ NFR-01 "chưa test hiệu
năng" dù đã có thiết kế và ID test case — cần theo dõi tiếp).

*(ID dùng trong bảng trên khớp với ID chính thức sẽ dùng lại ở BRD — Chương 19 và SRS — Chương 20,
để bạn thấy rõ cùng một yêu cầu được truy vết xuyên suốt nhiều tài liệu như thế nào.)*

## 16.3 Ví dụ dùng RTM để phát hiện yêu cầu bị bỏ sót

Giả sử BRD của FoodNow có thêm một yêu cầu chưa được liệt kê ở ví dụ Chương 19: "BR-06: Nhân viên
chi nhánh cần in được hoá đơn cho khách khi đến lấy tại quán (không giao hàng)." Khi rà soát RTM ở
cuối giai đoạn Design, BA phát hiện **không có dòng Functional Requirement nào truy ngược về
BR-06** — đây là dấu hiệu rõ ràng: yêu cầu này đã bị bỏ sót khi viết SRS chi tiết, cần bổ sung ngay
trước khi Dev bắt đầu code, thay vì để đến giai đoạn Testing mới phát hiện thiếu (nhớ lại chi phí
sửa lỗi tăng theo giai đoạn ở Chương 2).

## 16.4 Ví dụ dùng RTM để phân tích ảnh hưởng khi thay đổi

Giả sử giữa dự án, Ban giám đốc FoodNow yêu cầu thay đổi: "Không giới hạn chỉ 1 mã giảm giá/đơn
hàng nữa — cho phép áp dụng tối đa 2 mã cùng lúc." Đây là thay đổi trực tiếp lên FR-PAY-04. BA tra
RTM, lọc theo Module "Thanh toán", thấy ngay: thay đổi này ảnh hưởng đến UC-01 (Đặt món), các Test
Case TC-05, TC-06 cần viết lại, và cần rà soát thêm các yêu cầu phi chức năng liên quan đến hiệu
năng module Thanh toán (nhóm NFR trong SRS — Chương 20) vì logic tính giá phức tạp hơn có thể ảnh
hưởng thời gian phản hồi. Nhờ RTM, BA đưa ra được đánh giá ảnh hưởng nhanh và đầy đủ hơn nhiều so
với việc dò trí nhớ hoặc đọc lại toàn bộ tài liệu.

## 16.5 Khi nào cần RTM đầy đủ, khi nào không cần?

RTM đầy đủ, chi tiết như bảng ở mục 16.2 phù hợp nhất với:

- Dự án theo Waterfall (Chương 6), nơi tài liệu được chốt và cần theo dõi chặt chẽ suốt dự án dài.
- Ngành có yêu cầu tuân thủ pháp lý nghiêm ngặt (Banking, Y tế, Hàng không) — cần bằng chứng mọi
  yêu cầu đều được kiểm thử đầy đủ cho mục đích audit.
- Dự án quy mô lớn, nhiều module, nhiều người tham gia qua thời gian dài — trí nhớ cá nhân không
  đủ để theo dõi toàn bộ mối liên hệ.

Với dự án Agile nhỏ, nhịp độ nhanh (Chương 7-11), RTM đầy đủ như trên có thể **quá nặng nề** — công
cụ như Jira thường tự động tạo liên kết truy vết ở mức nhẹ hơn (Epic → Story → Task → Test linked)
mà không cần một bảng Excel riêng biệt (xem thêm Chương 37).

## Bài tập

1. Xây dựng một RTM (theo mẫu bảng mục 16.2) cho 3 yêu cầu bất kỳ của tính năng "Chương trình
   khách hàng thân thiết" của FoodNow — từ Business Requirement đến Test Case.
2. Giả sử FoodNow quyết định bỏ hẳn tính năng thanh toán tiền mặt khi giao hàng (COD), chỉ cho
   thanh toán online. Dùng tư duy RTM, liệt kê các use case/module/test case có khả năng bị ảnh
   hưởng bởi thay đổi này.

## Sai lầm thường gặp

- **Xây RTM rồi không cập nhật khi có thay đổi**: RTM lỗi thời gây hại hơn không có RTM, vì tạo
  cảm giác an toàn giả (tưởng đã theo dõi đầy đủ nhưng thực ra dữ liệu đã cũ).
- **Áp dụng RTM đầy đủ cho mọi dự án bất kể quy mô**: gây lãng phí thời gian cho dự án nhỏ, nhịp độ
  nhanh — cần cân nhắc mức độ chi tiết phù hợp (mục 16.5).
- **Chỉ dùng RTM một chiều (chỉ truy xuôi hoặc chỉ truy ngược)**: mất đi một nửa giá trị — cần
  dùng cả hai chiều để vừa kiểm tra tính đầy đủ, vừa phân tích ảnh hưởng khi thay đổi.

## Tóm tắt & tiếp theo

RTM là bảng liên kết yêu cầu xuyên suốt vòng đời dự án, giúp phát hiện yêu cầu bị bỏ sót và phân
tích ảnh hưởng khi có thay đổi — mức độ chi tiết cần điều chỉnh theo quy mô và mô hình dự án.
Chương 17 sẽ học cách xác nhận yêu cầu đã thu thập là **"đúng" và "đủ"** trước khi coi là hoàn
thành, thông qua Requirements Validation & Verification.
