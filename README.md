# book_ba — Kế hoạch biên soạn sách "IT Business Analyst — Từ Zero Đến Thành Thạo"

Sách dạy nghề Business Analyst (BA) trong ngành phần mềm bằng tiếng Việt, dành cho người
**chưa biết gì về BA**, đi từ quy trình phát triển phần mềm (SDLC), Agile/XP/Waterfall, vai trò
BA trong từng giai đoạn dự án, đến bộ tài liệu mẫu điền sẵn dùng được ngay (SRS, BRD/PRD, Epic,
User Story, Incremental Delivery Document...).

> **Trạng thái: đã viết xong toàn bộ 40 chương + 6 phụ lục, đã rà soát, có bản HTML và PDF sẵn sàng
> phát hành.** Xem `dist/index.html` để đọc bản HTML, hoặc `dist/it-business-analyst-tu-zero-den-
> thanh-thao.pdf` cho bản in — cả hai commit sẵn trong repo, chạy `npm run build:all` để build lại
> từ nguồn Markdown khi nội dung thay đổi. Còn lại duy nhất: EPUB (mục 6).

## 1. Mục tiêu

- Dạy nghề BA từ con số 0 đến mức thành thạo — làm việc được ngay trong một dự án phần mềm thật.
- Bao phủ đầy đủ: SDLC, quy trình quản lý phần mềm (Agile/Scrum/XP, Waterfall), vai trò và vị trí
  của BA trong từng giai đoạn SDLC, định hướng nghề nghiệp (lộ trình, chứng chỉ, kỹ năng).
- Mỗi chương liên quan đến tài liệu BA có **mẫu tài liệu thật, điền sẵn nội dung ví dụ**, lưu
  trong `templates/`, dùng được ngay cho công việc thực tế — không phải chỉ mô tả lý thuyết suông.
- Xuất bản dạng "release" — chất lượng đủ để công bố công khai kèm bộ tài liệu mẫu.
- Định dạng phát hành: **HTML** và **PDF** trước, **EPUB** ở giai đoạn sau.

## 2. Đối tượng độc giả

- Chưa biết gì về BA, kể cả chưa từng làm việc trong dự án phần mềm — sách giải thích từ khái
  niệm nền (SDLC là gì, dự án phần mềm vận hành ra sao) trước khi vào chuyên môn BA.
- Không yêu cầu biết lập trình — BA là vai trò cầu nối nghiệp vụ/kỹ thuật, không viết code.
  Chương về SQL/data (Chương 38) chỉ ở mức đọc hiểu, không yêu cầu biết lập trình trước đó.
- Phù hợp cho: sinh viên định hướng nghề BA, người trái ngành muốn chuyển sang BA, hoặc
  Dev/Tester muốn hiểu thêm vai trò BA để phối hợp tốt hơn.
- Cần có phần thực chiến: mẫu tài liệu điền sẵn, case study xuyên suốt một dự án giả định.

## 3. Cấu trúc thư mục dự kiến

```
book_ba/
├── book/                        # Nội dung sách (Markdown), 1 file/chương + manifest.json (mục lục)
│   ├── part0-nhap-mon/          # Chương 1-5
│   ├── part1-quy-trinh-phat-trien/  # Chương 6-11
│   ├── part2-thu-thap-phan-tich-yeu-cau/  # Chương 12-18
│   ├── part3-tai-lieu-ba-cot-loi/   # Chương 19-25
│   ├── part4-quan-ly-du-an-giao-hang/  # Chương 26-31
│   ├── part5-giao-tiep-kiem-thu-nghiem-thu/  # Chương 32-36
│   ├── part6-cong-cu-nang-cao/  # Chương 37-40
│   └── part7-phu-luc/           # Phụ lục A-F
├── templates/                   # Bộ tài liệu mẫu — file thật, điền sẵn nội dung ví dụ,
│   │                             # tương ứng 1-1 với chương giới thiệu tài liệu đó
│   ├── brd-prd/, srs/, use-case/, user-story-epic/, incremental-delivery/, uat/, sign-off/, raid-log/
├── tools/                       # Script build HTML (build.js) + PDF (build-pdf.js) + CSS
├── dist/                        # HTML + PDF đã build — commit sẵn trong repo, chạy `npm run build:all` để cập nhật
└── README.md                    # File kế hoạch này
```

Quy ước: mỗi chương gồm 1 file nội dung trong `book/<part>/chXX-slug.md`. Chương nào giới thiệu
một loại tài liệu BA (BRD/PRD, SRS, Use Case, User Story/Epic, Incremental Delivery Plan, UAT,
Sign-off, RAID log) có kèm **mẫu tài liệu thật** trong `templates/<loai-tai-lieu>/`, dựa trên một
case study xuyên suốt (một dự án app đặt đồ ăn giả định — dùng nhất quán từ Chương 1 đến Chương 40
để người đọc thấy được một tài liệu "sống" qua toàn bộ vòng đời dự án, không phải ví dụ rời rạc
từng chương).

## 4. Quy ước cho mỗi chương

Mỗi chương cần có:
1. Mục tiêu học (đọc xong làm được gì, áp dụng được gì vào công việc).
2. Lý thuyết/khái niệm nền, giải thích ngắn gọn, có sơ đồ (Mermaid) khi cần minh hoạ quy trình.
3. Ví dụ thực tế bám theo case study xuyên suốt (dự án app đặt đồ ăn "FoodNow" — xem mục 8).
4. Liên kết tới mẫu tài liệu tương ứng trong `templates/` (với các chương có tài liệu mẫu).
5. Bài tập/gợi ý thực hành cuối chương.
6. Sai lầm thường gặp của BA mới vào nghề + cách khắc phục (đúc kết thực tế, không lý thuyết suông).

## 5. Mục lục sách (40 chương + phụ lục)

### Phần 0 — Nhập môn & định hướng nghề BA
1. BA là ai, làm gì? Vai trò cầu nối giữa nghiệp vụ và kỹ thuật
2. Tổng quan SDLC (Software Development Life Cycle): các giai đoạn, vì sao dự án phần mềm cần quy trình
3. Hệ sinh thái một dự án phần mềm: PM, Dev, QA, PO, UX/UI, Stakeholder — BA phối hợp với ai, khi nào
4. Định hướng nghề nghiệp BA: lộ trình từ Fresher đến BA Lead/Product Owner, các chứng chỉ (IIBA/CBAP, CCBA, PMI-PBA)
5. Bộ kỹ năng & công cụ của BA: kỹ năng cứng, kỹ năng mềm, công cụ phổ biến (Jira, Confluence, Visio, draw.io, Figma)

### Phần 1 — Quy trình phát triển & quản lý phần mềm
6. Waterfall: đặc điểm, các giai đoạn tuần tự, ưu/nhược điểm, khi nào vẫn nên dùng
7. Agile: Agile Manifesto, 12 nguyên tắc, tư duy Agile khác Waterfall ở đâu
8. Scrum chi tiết: vai trò (PO/SM/Dev Team), sự kiện (sprint, planning, standup, review, retro), artifact
9. Extreme Programming (XP): các thực hành kỹ thuật (TDD, pair programming, CI, refactoring liên tục) và vai trò BA khi làm cùng đội XP
10. Kanban & so sánh các mô hình: Waterfall vs Scrum vs Kanban vs XP — bảng tiêu chí chọn mô hình
11. Vai trò và trách nhiệm cụ thể của BA trong từng mô hình (Waterfall/Scrum/Kanban/XP) — deliverable khác nhau ra sao

### Phần 2 — Thu thập & phân tích yêu cầu
12. Kỹ thuật Elicitation: interview, workshop, survey, observation, brainstorming, document analysis
13. Stakeholder Analysis & ma trận RACI: xác định ai quyết định, ai bị ảnh hưởng
14. Phân loại yêu cầu: Business Requirements, Stakeholder Requirements, Solution Requirements (Functional/Non-functional), Transition Requirements
15. Mô hình hoá yêu cầu: Use Case Diagram, Activity Diagram, Sequence Diagram, BPMN cơ bản
16. Requirements Traceability Matrix (RTM): theo dõi yêu cầu từ gốc đến khi release
17. Requirements Validation & Verification: làm sao biết yêu cầu "đúng" và "đủ"
18. Quản lý thay đổi yêu cầu: scope creep là gì, quy trình Change Request

### Phần 3 — Tài liệu BA cốt lõi (kèm mẫu điền sẵn)
19. BRD (Business Requirements Document) & PRD (Product Requirements Document): khác nhau ở đâu, cấu trúc, mẫu đầy đủ
20. SRS (Software Requirements Specification) theo chuẩn IEEE 830: cấu trúc, cách viết, mẫu đầy đủ
21. FRD (Functional Requirements Document) & yêu cầu phi chức năng (performance, security, usability...)
22. Use Case Specification: cách viết use case chi tiết (actor, flow chính/phụ, exception), mẫu
23. User Story & Acceptance Criteria: nguyên tắc INVEST, cú pháp Gherkin (Given-When-Then), mẫu
24. Epic, Feature, User Story: phân rã backlog (backlog decomposition), mẫu Epic + User Story backlog
25. Wireframe & Prototype cơ bản cho BA: đủ dùng để mô tả ý tưởng, không cần biết thiết kế chuyên sâu

### Phần 4 — Quản lý dự án & giao hàng
26. Ưu tiên hoá Backlog: MoSCoW, WSJF, mô hình Kano
27. Sprint Planning & vai trò của BA trong sprint: chuẩn bị backlog, làm rõ yêu cầu (refinement)
28. Incremental & Iterative Delivery: khái niệm, phân biệt, vì sao giao hàng từng phần giảm rủi ro
29. Release Plan & Delivery Document: mẫu Incremental Delivery Plan đầy đủ
30. Estimation cơ bản cho BA: story points, T-shirt sizing, phối hợp cùng Dev/QA ước lượng
31. RAID Log: quản lý Risk, Assumption, Issue, Dependency trong dự án — mẫu RAID log

### Phần 5 — Giao tiếp, kiểm thử & nghiệm thu
32. Giao tiếp hiệu quả của BA: viết email, họp, trình bày với stakeholder cấp cao
33. Facilitation: điều phối workshop, requirement review meeting hiệu quả
34. BA & QA: viết test case cơ bản, UAT (User Acceptance Testing) — mẫu UAT checklist
35. Sign-off & nghiệm thu: quy trình ký duyệt tài liệu/tính năng, mẫu Sign-off Document
36. Đo lường thành công sau go-live: KPI, OKR cho sản phẩm, thu thập feedback người dùng

### Phần 6 — Công cụ & kỹ năng nâng cao
37. Jira & Confluence cho BA: quản lý backlog, viết & liên kết tài liệu, dashboard theo dõi tiến độ
38. Data & SQL cơ bản cho BA: đọc hiểu mô hình dữ liệu, viết SELECT query đơn giản để tự tra cứu
39. Domain knowledge: BA trong các ngành đặc thù (Banking, E-commerce, Insurance) — case study ngắn mỗi ngành
40. Case study tổng hợp "FoodNow": nhìn lại toàn bộ vòng đời dự án case study qua lăng kính BA, từ ý tưởng đến sau go-live

### Phụ lục — Bộ tài liệu mẫu đầy đủ
- Phụ lục A — Mẫu BRD & PRD đầy đủ (dự án FoodNow)
- Phụ lục B — Mẫu SRS đầy đủ theo IEEE 830 (dự án FoodNow)
- Phụ lục C — Mẫu Epic + User Story backlog đầy đủ (dự án FoodNow)
- Phụ lục D — Mẫu Incremental Delivery Plan đầy đủ (dự án FoodNow)
- Phụ lục E — Bảng thuật ngữ BA (Glossary) tra cứu nhanh
- Phụ lục F — Tài liệu tham khảo & nguồn học thêm

## 6. Pipeline xuất bản (HTML → PDF → EPUB)

Dùng lại đúng cách tiếp cận đã chứng minh hiệu quả ở dự án `android_book`: script Node.js tự viết
(`tools/build.js`, dùng `markdown-it`) thay vì mdBook/Honkit/Pandoc — và tương tự cho PDF
(`tools/build-pdf.js`, dùng Puppeteer) thay vì Pandoc/LaTeX.

- `npm run build` (hoặc `node tools/build.js`) đọc `book/manifest.json` + từng file
  `book/<part>/chXX-*.md`, sinh HTML đầy đủ vào `dist/` (sidebar điều hướng theo phần/chương,
  prev/next, syntax highlight bằng highlight.js cho các đoạn mã mẫu SQL/Gherkin, sơ đồ Mermaid
  cho các quy trình/mô hình). Trang chủ `dist/index.html` liệt kê mục lục đầy đủ. Đã commit sẵn.
- **PDF**: `npm run build:pdf` (hoặc `node tools/build-pdf.js`) — gộp toàn bộ chương thành một
  trang HTML dài (bìa, mục lục liên kết, mỗi chương một trang in riêng), dùng Puppeteer (Chromium
  headless, đã có sẵn trong `devDependencies`) render Mermaid/highlight.js rồi in thành
  `dist/it-business-analyst-tu-zero-den-thanh-thao.pdf` — không qua Pandoc/LaTeX, tái sử dụng đúng
  CSS/font tinh thần bản HTML (dùng `tools/pdf-style.css` riêng, tối ưu cho in ấn). `npm run
  build:all` chạy cả hai bước liên tiếp. Đã commit sẵn.
- **EPUB**: dự kiến bước tiếp theo, dùng lại đúng nguồn Markdown, không viết lại nội dung.

## 7. Lộ trình biên soạn (milestones)

1. ✅ Chốt kế hoạch (README này) + dựng khung thư mục `book/`, `templates/`, `tools/`.
2. ✅ Viết xong Phần 0 (nhập môn & định hướng nghề) — cột mốc "hiểu BA là ai, làm gì".
3. ✅ Viết xong Phần 1 (quy trình phát triển phần mềm: Waterfall/Agile/Scrum/XP/Kanban + vai trò BA).
4. ✅ Viết xong Phần 2 (thu thập & phân tích yêu cầu).
5. ✅ Viết xong Phần 3 (tài liệu BA cốt lõi) + mẫu tài liệu tương ứng trong `templates/`.
6. ✅ Viết xong Phần 4 (quản lý dự án & giao hàng) + mẫu Incremental Delivery Plan, RAID log.
7. ✅ Viết xong Phần 5 (giao tiếp, kiểm thử, nghiệm thu) + mẫu UAT checklist, Sign-off document.
8. ✅ Viết xong Phần 6 (công cụ & kỹ năng nâng cao) + case study tổng hợp.
9. ✅ Viết xong Phụ lục A-F (bộ tài liệu mẫu đầy đủ + glossary + tài liệu tham khảo).
10. ✅ Build bản HTML hoàn chỉnh (46/46 chương + phụ lục, không còn mục "sắp có").
11. ✅ Rà soát/hiệu đính toàn bộ nội dung một lượt độc lập: kiểm tra tự động toàn bộ 55 file Markdown
    — không còn tham chiếu chương/phụ lục sai số, không link nội bộ nào gãy trong 47 trang HTML,
    code fence cân bằng, sơ đồ Mermaid hợp lệ; đã sửa 1 lỗi trùng mã ID minh hoạ ở RTM (Chương 16)
    và 1 chỗ nhắc nhầm "bản PDF" (Chương 19) — dự án này chỉ có HTML → EPUB, không làm PDF.
12. ✅ Build bản PDF hoàn chỉnh (`dist/it-business-analyst-tu-zero-den-thanh-thao.pdf`) bằng
    Puppeteer, gộp bìa + mục lục + toàn bộ 46 chương/phụ lục, ngắt trang theo từng chương.
13. ⬜ Xuất bản EPUB.

**Bản HTML + PDF final sẵn sàng để phát hành**: `dist/index.html` và
`dist/it-business-analyst-tu-zero-den-thanh-thao.pdf` (build lại bằng `npm run build:all`), 46/46
chương + phụ lục đầy đủ nội dung, điều hướng prev/next liền mạch từ Chương 1 đến Phụ lục F, không
còn placeholder hay link gãy.

## 8. Các quyết định đã chốt trong quá trình viết

- **Case study xuyên suốt**: một dự án app đặt đồ ăn giả định tên **"FoodNow"** — dùng nhất quán
  từ Chương 1 đến Chương 40 và toàn bộ Phụ lục, để mọi tài liệu mẫu (BRD, SRS, backlog, delivery
  plan...) đều là các phiên bản khác nhau của **cùng một dự án**, người đọc thấy được tài liệu
  "sống" và liên kết với nhau qua vòng đời dự án thật, thay vì ví dụ rời rạc mỗi chương một domain.
- **Không dạy công cụ như phần mềm cụ thể chuyên sâu**: Jira/Confluence/Visio chỉ giới thiệu ở
  mức khái niệm và cách dùng cho công việc BA (Chương 37), không phải hướng dẫn cài đặt/cấu hình
  Jira admin — đó là công việc của PM/Admin, không phải trọng tâm sách.
- **Công cụ build tài liệu**: tái sử dụng script Node.js tự viết từ `android_book` (xem mục 6)
  thay vì mdBook/Honkit/Pandoc, để tận dụng lại toàn bộ hạ tầng sidebar/Mermaid/highlight.js, và
  Puppeteer cho PDF thay vì Pandoc/LaTeX.
- **Định dạng phát hành**: HTML và PDF trước, EPUB sau — theo đúng thứ tự của `android_book`.
