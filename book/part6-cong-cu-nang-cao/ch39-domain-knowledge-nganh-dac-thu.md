# Chương 39: Domain knowledge: BA trong Banking, E-commerce, Insurance

## Mục tiêu học

- Hiểu vì sao domain knowledge (hiểu biết chuyên sâu về một ngành) là lợi thế cạnh tranh lớn của BA.
- Nắm được đặc điểm nghiệp vụ đặc thù của 3 ngành phổ biến: Banking, E-commerce, Insurance.
- Biết cách bắt đầu xây dựng domain knowledge cho một ngành mới khi chuyển việc/chuyển dự án.

## 39.1 Vì sao domain knowledge quan trọng?

Các kỹ thuật đã học xuyên suốt cuốn sách (elicitation, viết User Story, RTM...) là **kỹ năng tổng
quát**, áp dụng được cho mọi ngành. Nhưng một BA có thêm **domain knowledge** — hiểu sâu về đặc thù
nghiệp vụ, quy định, thuật ngữ riêng của một ngành cụ thể — sẽ:

- Elicitation hiệu quả hơn nhiều: biết trước câu hỏi nào quan trọng, tránh bỏ sót yêu cầu đặc thù
  ngành mà người ngoài ngành không biết để hỏi.
- Được tin tưởng hơn từ stakeholder: nói đúng thuật ngữ, hiểu đúng ràng buộc, tạo cảm giác "đây là
  người hiểu việc của chúng tôi", không chỉ là "người biết viết tài liệu".
- Phát hiện rủi ro/quy định tuân thủ mà BA thiếu domain knowledge dễ bỏ sót — hậu quả có thể rất
  nghiêm trọng ở các ngành có quy định pháp lý chặt (Banking, Insurance).

## 39.2 Banking (Ngân hàng)

**Đặc điểm nghiệp vụ đặc thù**:
- Quy định pháp lý rất chặt chẽ (Ngân hàng Nhà nước, chống rửa tiền — AML, xác thực khách hàng —
  KYC/eKYC).
- Yêu cầu bảo mật cực cao (giao dịch tài chính, dữ liệu nhạy cảm).
- Quy trình phê duyệt nhiều lớp (ví dụ: một khoản vay cần qua nhiều bước thẩm định, không chỉ 1
  người quyết định).
- Thường ưu tiên mô hình Waterfall hoặc Hybrid (Chương 6, 11) cho các hệ thống lõi (core banking)
  vì yêu cầu tài liệu hoá đầy đủ phục vụ kiểm toán, nhưng có thể dùng Agile cho các kênh số
  (mobile banking, ứng dụng khách hàng) ít ràng buộc pháp lý hơn.

**Thuật ngữ đặc thù BA cần biết**: KYC (Know Your Customer), AML (Anti-Money Laundering), core
banking system, giao dịch treo (pending transaction), hạn mức tín dụng (credit limit).

**Ví dụ tình huống**: khi phân tích yêu cầu "Cho phép khách hàng chuyển khoản qua app", BA có domain
knowledge ngân hàng sẽ tự động hỏi thêm: hạn mức chuyển khoản/ngày là bao nhiêu? Có cần xác thực
2 lớp (OTP) cho giao dịch trên một ngưỡng nhất định không? Giao dịch có cần được ghi log phục vụ
audit theo quy định không? — những câu hỏi này không phải ai cũng tự nghĩ ra nếu chưa quen ngành.

## 39.3 E-commerce (Thương mại điện tử)

**Đặc điểm nghiệp vụ đặc thù**:
- Quản lý tồn kho (inventory) phức tạp, đặc biệt khi bán trên nhiều kênh cùng lúc (đa kênh —
  omnichannel).
- Logistics và vận chuyển: nhiều đối tác giao hàng, tính phí ship theo khu vực/trọng lượng.
- Khuyến mãi/giá phức tạp: mã giảm giá, flash sale, giá theo số lượng mua, chương trình thành viên.
- Thường ưu tiên Agile/Scrum (Chương 8) vì thị trường thay đổi nhanh, cần phản hồi liên tục.

**Thuật ngữ đặc thù BA cần biết**: SKU (Stock Keeping Unit — mã quản lý từng biến thể sản phẩm),
cart abandonment (bỏ giỏ hàng giữa chừng), fulfillment (quy trình xử lý đơn từ lúc đặt đến lúc
giao), omnichannel.

**Liên hệ trực tiếp**: dự án FoodNow xuyên suốt sách này chính là một ví dụ e-commerce dạng đặt đồ
ăn (food delivery) — các khái niệm như quản lý tồn kho món ăn theo chi nhánh (FR-CART-04, Chương
20), tính phí/bán kính giao hàng (FR-DELIVERY-02) đều là ví dụ domain knowledge đặc thù ngành này.

## 39.4 Insurance (Bảo hiểm)

**Đặc điểm nghiệp vụ đặc thù**:
- Quy trình thẩm định rủi ro (underwriting) phức tạp trước khi phát hành hợp đồng bảo hiểm.
- Quy trình xử lý bồi thường (claims processing) — nhiều bước xác minh, có thể liên quan điều tra
  gian lận.
- Sản phẩm bảo hiểm thường có nhiều điều khoản, điều kiện loại trừ (exclusion) phức tạp cần mô tả
  chính xác trong hệ thống.
- Thường là mô hình Hybrid: core system (tính phí, quản lý hợp đồng) theo Waterfall vì cần chính
  xác pháp lý cao; các kênh bán hàng số/ứng dụng chăm sóc khách hàng theo Agile.

**Thuật ngữ đặc thù BA cần biết**: underwriting (thẩm định rủi ro), premium (phí bảo hiểm), claim
(yêu cầu bồi thường), policy (hợp đồng bảo hiểm), exclusion (điều khoản loại trừ).

## 39.5 Bảng so sánh nhanh 3 ngành

| | Banking | E-commerce | Insurance |
|---|---|---|---|
| Mức độ ràng buộc pháp lý | Rất cao | Trung bình (bảo vệ dữ liệu, quyền lợi người tiêu dùng) | Rất cao |
| Mô hình phổ biến | Waterfall/Hybrid cho core, Agile cho kênh số | Agile/Scrum | Hybrid |
| Độ phức tạp nghiệp vụ đặc trưng | Quy trình phê duyệt nhiều lớp | Quản lý tồn kho, logistics, khuyến mãi | Thẩm định rủi ro, xử lý bồi thường |
| Rủi ro nếu BA thiếu domain knowledge | Vi phạm quy định pháp lý, lỗ hổng bảo mật | Sai lệch tồn kho, tính phí ship sai | Sai điều khoản hợp đồng, xử lý bồi thường sai |

## 39.6 Cách xây dựng domain knowledge khi vào ngành mới

1. **Đọc tài liệu quy định/chuẩn ngành** (nếu có) — ví dụ thông tư của Ngân hàng Nhà nước cho
   Banking, quy định bảo vệ người tiêu dùng cho E-commerce.
2. **Học từ tài liệu nội bộ của dự án trước đó** (BRD/SRS cũ, nếu có quyền truy cập) — cách nhanh
   nhất để thấy ngôn ngữ/quy trình thực tế công ty đang dùng.
3. **Chủ động hỏi chuyên gia nghiệp vụ (Subject Matter Expert - SME)**: đừng ngại hỏi "cơ bản" khi
   mới vào ngành — SME thường sẵn lòng giải thích nếu thấy bạn thực sự muốn hiểu sâu.
4. **Tự trải nghiệm sản phẩm với tư cách người dùng** (nếu có thể): tự mở tài khoản ngân hàng, tự
   mua hàng online, tự tìm hiểu mua một gói bảo hiểm — trải nghiệm trực tiếp giúp hiểu nhanh hơn
   đọc tài liệu.
5. **Tích luỹ dần qua nhiều dự án cùng ngành**: domain knowledge sâu thường cần thời gian, không có
   đường tắt hoàn toàn — đây cũng là lý do nhiều BA chọn "chuyên sâu" một ngành thay vì nhảy ngành
   liên tục (liên hệ lộ trình sự nghiệp — Chương 4).

## Bài tập

1. Chọn một ngành khác (không phải Banking/E-commerce/Insurance) mà bạn quan tâm, liệt kê 3 thuật
   ngữ đặc thù và 1 đặc điểm nghiệp vụ riêng của ngành đó mà một BA mới vào cần biết.
2. Áp dụng bước 3 ở mục 39.6 (hỏi SME): viết ra 3 câu hỏi bạn sẽ hỏi một chuyên gia vận hành nhà
   hàng thực tế nếu được phỏng vấn để hiểu sâu hơn về domain "chuỗi nhà hàng/F&B" cho dự án FoodNow.

## Sai lầm thường gặp

- **Nghĩ kỹ năng phân tích tổng quát là đủ, không cần đầu tư domain knowledge**: dễ dẫn đến bỏ sót
  yêu cầu đặc thù ngành quan trọng, đặc biệt nguy hiểm ở ngành có ràng buộc pháp lý cao.
- **Ngại hỏi vì sợ bị đánh giá "không biết gì"**: SME thường đánh giá cao người chủ động hỏi để
  hiểu đúng, hơn là người tự đoán sai rồi làm sai.
- **Áp dụng nguyên xi kinh nghiệm từ ngành cũ sang ngành mới mà không kiểm chứng**: mỗi ngành có
  đặc thù riêng — kinh nghiệm cũ là nền tảng tốt nhưng cần xác minh lại, không áp dụng máy móc.

## Tóm tắt & tiếp theo

Domain knowledge tạo lợi thế cạnh tranh lớn cho BA — mỗi ngành (Banking, E-commerce, Insurance...)
có đặc điểm nghiệp vụ, thuật ngữ, mô hình quản lý dự án phổ biến riêng, và xây dựng domain knowledge
cần thời gian tích luỹ qua tài liệu, SME, và trải nghiệm thực tế. Chương 40 — chương cuối cùng của
phần nội dung chính — sẽ tổng kết toàn bộ sách qua một case study xuyên suốt: nhìn lại toàn bộ vòng
đời dự án FoodNow từ góc nhìn BA, từ ý tưởng ban đầu đến sau go-live.
