# Chương 23: User Story & Acceptance Criteria: INVEST, Gherkin, mẫu

## Mục tiêu học

- Viết được User Story đúng cấu trúc chuẩn, thể hiện rõ vai trò, nhu cầu, và lợi ích.
- Áp dụng bộ tiêu chí INVEST để đánh giá chất lượng một User Story.
- Viết được Acceptance Criteria theo cú pháp Gherkin (Given-When-Then) đủ cụ thể để Dev/QA dùng
  trực tiếp.

## 23.1 User Story là gì?

**User Story** là định dạng mô tả yêu cầu ngắn gọn, phổ biến trong Agile (Scrum/Kanban — Chương
8-10), viết theo góc nhìn người dùng thay vì mô tả kỹ thuật:

> **Là [vai trò], tôi muốn [nhu cầu/hành động], để [lợi ích/mục đích].**

> Ví dụ FoodNow: "Là khách hàng, tôi muốn xem trạng thái đơn hàng theo thời gian thực, để tôi biết
> chính xác khi nào đồ ăn sẽ đến."

Ba thành phần đều quan trọng: **vai trò** (ai cần), **nhu cầu** (cần gì), **lợi ích** (vì sao cần)
— phần "lợi ích" thường bị bỏ qua bởi người mới, nhưng lại là phần quan trọng nhất: nó giúp Dev
hiểu **mục đích thật sự**, từ đó có thể tự đề xuất giải pháp tốt hơn nếu nhu cầu ban đầu chưa phải
cách tối ưu nhất để đạt lợi ích đó.

## 23.2 Bộ tiêu chí INVEST

Một User Story chất lượng nên đạt các tiêu chí sau (viết tắt INVEST):

| Chữ cái | Tiêu chí | Giải thích |
|---|---|---|
| **I** | Independent (Độc lập) | Có thể phát triển và giao hàng độc lập, không phụ thuộc chặt vào story khác phải làm trước |
| **N** | Negotiable (Có thể thương lượng) | Không phải hợp đồng cứng nhắc — chi tiết cách hiện thực có thể thảo luận giữa BA/PO và Dev |
| **V** | Valuable (Có giá trị) | Mang lại giá trị rõ ràng cho người dùng hoặc nghiệp vụ — không phải "task kỹ thuật" trá hình |
| **E** | Estimable (Ước lượng được) | Đội đủ hiểu để ước lượng được độ phức tạp/thời gian (Chương 30) |
| **S** | Small (Đủ nhỏ) | Đủ nhỏ để hoàn thành trong một sprint, tốt nhất là trong vài ngày |
| **T** | Testable (Kiểm thử được) | Có Acceptance Criteria rõ ràng để xác nhận hoàn thành đúng |

### Ví dụ: User Story không đạt INVEST và cách sửa

**Không đạt (quá lớn, không độc lập)**: "Là khách hàng, tôi muốn có toàn bộ tính năng đặt hàng và
thanh toán." → Vi phạm **S** (quá lớn, cần nhiều sprint) và **I** (gộp nhiều luồng phụ thuộc nhau).

**Sửa lại — chia nhỏ**:
- "Là khách hàng, tôi muốn thêm/xoá món trong giỏ hàng, để tôi kiểm soát đúng đơn hàng trước khi
  thanh toán."
- "Là khách hàng, tôi muốn thanh toán bằng thẻ hoặc ví điện tử, để tôi không cần chuẩn bị tiền mặt."
- "Là khách hàng, tôi muốn áp dụng mã giảm giá khi thanh toán, để tôi tiết kiệm chi phí."

Mỗi story nhỏ hơn giờ có thể ước lượng, phát triển, và giao hàng độc lập hơn nhiều so với story gốc.

## 23.3 Acceptance Criteria — làm rõ "khi nào coi là hoàn thành"

**Acceptance Criteria (AC)** là danh sách điều kiện cụ thể để xác nhận một User Story đã được hiện
thực đúng — đây là cầu nối giữa User Story (mô tả nhu cầu ở mức khái quát) và test case (Chương 34).
Định dạng phổ biến nhất: **Gherkin (Given-When-Then)**.

> - **Given** (Bối cảnh): trạng thái hệ thống/dữ liệu trước khi hành động xảy ra.
> - **When** (Hành động): người dùng thực hiện hành động gì.
> - **Then** (Kết quả mong đợi): hệ thống phải phản hồi như thế nào.

### Ví dụ Acceptance Criteria cho User Story "Áp dụng mã giảm giá"

> **User Story**: Là khách hàng, tôi muốn áp dụng mã giảm giá khi thanh toán, để tôi tiết kiệm chi phí.
>
> **Acceptance Criteria:**
>
> ```gherkin
> Scenario 1: Áp dụng mã giảm giá hợp lệ
>   Given giỏ hàng có tổng giá trị 200.000đ
>   And mã giảm giá "FOODNOW10" đang có hiệu lực, giảm 10%
>   When khách hàng nhập mã "FOODNOW10" và bấm Áp dụng
>   Then tổng tiền thanh toán giảm còn 180.000đ
>   And hệ thống hiển thị thông báo "Đã áp dụng mã giảm giá FOODNOW10"
>
> Scenario 2: Nhập mã giảm giá đã hết hạn
>   Given mã giảm giá "TET2024" đã hết hạn sử dụng
>   When khách hàng nhập mã "TET2024" và bấm Áp dụng
>   Then hệ thống hiển thị thông báo lỗi "Mã giảm giá đã hết hạn"
>   And tổng tiền thanh toán không thay đổi
>
> Scenario 3: Nhập mã giảm giá thứ hai sau khi đã áp dụng một mã
>   Given khách hàng đã áp dụng thành công mã "FOODNOW10"
>   When khách hàng nhập thêm mã "SUMMER5" và bấm Áp dụng
>   Then hệ thống hiển thị thông báo "Chỉ được áp dụng 1 mã giảm giá cho mỗi đơn hàng"
>   And mã "FOODNOW10" vẫn được giữ nguyên hiệu lực
> ```

Nhận xét: mỗi Scenario tương ứng gần như trực tiếp với một test case (liên hệ TDD — Chương 9, và
UAT — Chương 34) — đây chính là giá trị lớn nhất của Gherkin: giảm khoảng cách giữa "yêu cầu" và
"kiểm thử được".

## 23.4 Mẫu tài liệu

Xem thêm ví dụ User Story + Acceptance Criteria đầy đủ hơn cho nhiều tính năng khác của FoodNow tại:

> **`templates/user-story-epic/FoodNow-UserStories.md`**

## Bài tập

1. Viết một User Story cho tính năng "khách hàng huỷ đơn hàng trong vòng 2 phút sau khi đặt", kèm
   tối thiểu 2 Acceptance Criteria theo cú pháp Gherkin (1 trường hợp thành công, 1 trường hợp thất
   bại — ví dụ huỷ sau khi đã quá 2 phút).
2. Áp dụng bộ tiêu chí INVEST để đánh giá User Story bạn vừa viết ở câu 1 — nếu vi phạm tiêu chí
   nào, hãy sửa lại.

## Sai lầm thường gặp

- **Viết User Story thiếu phần "để [lợi ích]"**: mất đi ngữ cảnh quan trọng nhất giúp Dev hiểu mục
  đích thật, dễ dẫn đến hiện thực đúng chữ nhưng sai tinh thần.
- **Acceptance Criteria chỉ mô tả happy path, không có trường hợp lỗi**: giống lỗi phổ biến ở Use
  Case (Chương 22) — luôn cần ít nhất 1 kịch bản thất bại/ngoại lệ.
- **User Story quá lớn (không đạt tiêu chí "Small")**: thường là dấu hiệu cần tách thành Epic
  (Chương 24) chứa nhiều User Story nhỏ hơn, thay vì cố nhồi tất cả vào một story.

## Tóm tắt & tiếp theo

User Story mô tả nhu cầu ngắn gọn theo góc nhìn người dùng (vai trò - nhu cầu - lợi ích), đánh giá
chất lượng bằng bộ tiêu chí INVEST, và đi kèm Acceptance Criteria viết theo Gherkin
(Given-When-Then) để làm rõ ràng "khi nào coi là hoàn thành". Chương 24 sẽ học cách tổ chức nhiều
User Story liên quan thành **Epic**, và kỹ thuật phân rã (decomposition) một yêu cầu lớn thành
backlog có thể quản lý được.
