# Chương 20: SRS theo chuẩn IEEE 830: cấu trúc, cách viết, mẫu đầy đủ

## Mục tiêu học

- Hiểu vị trí của SRS trong chuỗi tài liệu BRD → PRD → SRS.
- Nắm được cấu trúc chuẩn IEEE 830 (và biến thể thực tế thường dùng) cho SRS.
- Viết được yêu cầu chức năng chi tiết đủ để Dev hiện thực chính xác, không cần đoán thêm.
- Có sẵn mẫu SRS đầy đủ trong `templates/srs/` để tham khảo.

## 20.1 SRS là gì, vì sao cần chuẩn hoá?

**SRS (Software Requirements Specification)** là tài liệu đặc tả **chi tiết nhất** về mặt chức
năng và phi chức năng của phần mềm — đây là tài liệu mà Dev dựa vào để code, và QA dựa vào để viết
test case. Nếu BRD/PRD (Chương 19) nói "vì sao" và "cái gì ở mức khái niệm", SRS nói **"cụ thể như
thế nào"** — đủ chi tiết để hai người Dev khác nhau đọc SRS và hiểu ra **cùng một cách**, không có
khoảng trống để tự suy đoán khác nhau.

**IEEE 830** là chuẩn công nghiệp lâu đời (từ IEEE — Institute of Electrical and Electronics
Engineers) định nghĩa cấu trúc và tiêu chí chất lượng cho SRS. Dù ra đời từ thời Waterfall thịnh
hành, cấu trúc này vẫn hữu ích làm khung tham khảo, kể cả khi đội áp dụng Agile chỉ dùng một phần
rút gọn của nó.

## 20.2 Cấu trúc chuẩn IEEE 830 (rút gọn, thực chiến)

1. **Giới thiệu (Introduction)**
   - Mục đích tài liệu, phạm vi sản phẩm, định nghĩa thuật ngữ viết tắt, tài liệu tham chiếu (liên
     kết ngược về BRD/PRD).
2. **Mô tả tổng quan (Overall Description)**
   - Bối cảnh sản phẩm, các chức năng chính, đặc điểm người dùng, các ràng buộc chung, giả định.
3. **Yêu cầu cụ thể (Specific Requirements)** — phần quan trọng và dài nhất:
   - **Yêu cầu chức năng (Functional Requirements)**: mô tả từng chức năng, thường tổ chức theo
     use case hoặc theo module — mỗi yêu cầu có ID riêng để truy vết (Chương 16).
   - **Yêu cầu giao diện bên ngoài (External Interface Requirements)**: giao diện người dùng, giao
     diện phần cứng (nếu có), giao diện phần mềm khác (API bên thứ ba như cổng thanh toán).
   - **Yêu cầu phi chức năng (Non-functional Requirements)**: hiệu năng, bảo mật, độ tin cậy, khả
     năng bảo trì (chi tiết đầy đủ ở Chương 21).
4. **Phụ lục**: mô hình dữ liệu sơ bộ, sơ đồ hỗ trợ (liên hệ Chương 15), bảng thuật ngữ.

## 20.3 Nguyên tắc viết yêu cầu chức năng chất lượng cao

Áp dụng lại bộ tiêu chí Verification đã học ở Chương 17 (rõ ràng, đầy đủ, nhất quán, khả thi, đo
lường được, truy vết được), cộng thêm các nguyên tắc riêng cho SRS:

- **Mỗi yêu cầu có ID duy nhất**: ví dụ `FR-CART-01` (Functional Requirement, module Cart, số 01)
  — giúp truy vết trong RTM và tham chiếu khi trao đổi (Dev có thể hỏi "FR-CART-03 nghĩa là gì?"
  thay vì mô tả dài dòng lại).
- **Một yêu cầu, một hành vi**: tránh gộp nhiều hành vi vào một câu bằng chữ "và" — nếu một trong
  hai phần thay đổi/cần test riêng, việc gộp chung gây khó theo dõi.
- **Ưu tiên câu chủ động, chủ ngữ rõ ràng**: "Hệ thống PHẢI gửi email xác nhận..." rõ ràng hơn
  "Email xác nhận sẽ được gửi..." (câu bị động dễ làm mất chủ thể chịu trách nhiệm).
- **Nêu rõ điều kiện và trường hợp ngoại lệ**: không chỉ mô tả "đường đi thành công" (happy path)
  mà cả các trường hợp lỗi/ngoại lệ (liên hệ Activity Diagram — Chương 15).

### Ví dụ: yêu cầu viết kém vs viết tốt

**Viết kém**: "Khách hàng có thể thanh toán online."

**Viết tốt** (FR-PAY-01): "Hệ thống PHẢI cho phép khách hàng thanh toán bằng thẻ nội địa/quốc tế
hoặc ví điện tử (MoMo, ZaloPay) thông qua cổng thanh toán tích hợp. Nếu giao dịch thất bại, hệ
thống PHẢI hiển thị thông báo lỗi rõ ràng và cho phép khách hàng thử lại hoặc chọn phương thức
thanh toán khác, không được huỷ giỏ hàng đã chọn."

## 20.4 Mối quan hệ SRS — Use Case — User Story

Nhiều người mới nhầm lẫn SRS với Use Case Specification (Chương 22) hoặc User Story (Chương 23).
Phân biệt:

| | SRS | Use Case Spec | User Story |
|---|---|---|---|
| Mức chi tiết | Đặc tả đầy đủ cả module/hệ thống | Đặc tả một luồng tương tác cụ thể (actor - hệ thống) | Mô tả ngắn gọn một nhu cầu, dưới góc nhìn người dùng |
| Định dạng | Văn bản đặc tả có cấu trúc, ID hoá | Các bước tương tác (main flow, alternate flow) | "Là [vai trò], tôi muốn [nhu cầu], để [lợi ích]" |
| Phù hợp mô hình | Waterfall, dự án lớn cần tài liệu hoá đầy đủ | Cả hai, thường đi kèm SRS ở dự án Waterfall | Agile (Scrum/Kanban) |

Trong thực tế, một SRS đầy đủ **có thể chứa nhiều Use Case Specification** làm chi tiết bổ sung
cho từng luồng nghiệp vụ phức tạp.

## 20.5 Mẫu tài liệu đầy đủ cho FoodNow

Một bản SRS đầy đủ theo cấu trúc IEEE 830, điền sẵn cho module "Đặt món & Thanh toán" của FoodNow
App, được lưu tại:

> **`templates/srs/FoodNow-SRS.md`**

Xem thêm bản đầy đủ tại Phụ lục B (cuối sách).

## Bài tập

1. Viết lại yêu cầu sau theo đúng nguyên tắc ở mục 20.3 (có ID, rõ ràng, có trường hợp ngoại lệ):
   "Khách hàng nhận thông báo khi đơn hàng được giao."
2. Mở `templates/srs/FoodNow-SRS.md`, chọn 1 yêu cầu chức năng bất kỳ, thử viết 2 test case (Chương
   34 sẽ nói kỹ hơn về viết test case) để xác nhận yêu cầu đó đã được hiện thực đúng.

## Sai lầm thường gặp

- **Viết SRS như một bản sao chép PRD, chỉ dài hơn**: SRS cần đi sâu đến mức chi tiết Dev không
  cần hỏi lại — nếu chỉ lặp lại ý PRD với câu chữ dài hơn, không tạo thêm giá trị.
- **Bỏ qua yêu cầu giao diện bên ngoài (External Interface)**: quên mô tả rõ tích hợp với hệ thống
  bên thứ ba (cổng thanh toán, SMS OTP) — nguồn gốc phổ biến của lỗi tích hợp phát hiện muộn.
- **Không đánh ID cho từng yêu cầu**: khiến việc truy vết (RTM — Chương 16) và trao đổi giữa các
  bên trở nên khó khăn, dễ nhầm lẫn đang nói về yêu cầu nào.

## Tóm tắt & tiếp theo

SRS đặc tả chi tiết nhất về chức năng và phi chức năng của phần mềm theo chuẩn IEEE 830 (hoặc biến
thể rút gọn), là tài liệu Dev/QA dựa vào trực tiếp để làm việc — cần viết rõ ràng, có ID, có
trường hợp ngoại lệ. Chương 21 sẽ đi sâu vào phần dễ bị viết sơ sài nhất của SRS: **yêu cầu phi
chức năng (Non-functional Requirements)** và FRD.
