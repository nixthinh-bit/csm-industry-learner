---
name: csm-industry-learner
description: Học nhanh một ngành/domain mới theo khung 5 lớp (kinh tế đơn vị · chuỗi quy trình lõi · vai trò×KPI · từ vựng & hệ thống · ràng buộc cứng) bằng nghiên cứu web có trích nguồn, rồi (tuỳ chọn) mapping sang sản phẩm của user thành bảng giá trị + giả thuyết POC + câu hỏi discovery làm rõ doanh nghiệp cụ thể khác chuẩn ngành ở đâu. Dùng khi CSM/pre-sales/sales chuẩn bị bước vào một ngành mới, cần hiểu quy trình vận hành và ngôn ngữ của ngành trước khi gặp khách, cần chuẩn bị kế hoạch triển khai/onboarding/POC phù hợp ngành, hoặc cần biết sản phẩm mình gắn vào chỗ nào trong ngành đó. Đầu ra là file Markdown local, viết theo ngôn ngữ user đang dùng. Kích hoạt bằng /csm-industry-learner.
---

# CSM Industry Learner: học một ngành theo 5 lớp, rồi mapping vào sản phẩm

> **⚠️ LUẬT CÔNG CỤ (bắt buộc).** Nghiên cứu công khai đi qua **WebSearch / WebFetch**. Skill này
> không dùng `lark-cli` và không tạo Lark Doc. Đầu ra là file Markdown trên máy. Nếu user muốn đưa
> lên Lark, chỉ đường sang skill khác chứ không tự làm.

> **⚠️ LUẬT BẰNG CHỨNG (bắt buộc).** Mọi sự thật người đọc có thể hành động theo (một con số, một
> ngày, một tên hệ thống, một khẳng định về cách ngành vận hành) đều phải mang `[S#]` trỏ về nguồn đã
> tra trong lượt này. Không verify được thì viết thẳng **"Chưa tìm được trong nguồn đã tra."** Đang
> suy luận thì gắn `H#` (giả thuyết, có ID, đánh số chạy suốt báo cáo) kèm câu hỏi discovery kiểm
> chứng nó. Không được lấp khoảng
> trống bằng trung bình ngành, bằng lẽ thường, hay bằng kiến thức nhớ mà không tra lại trong lượt này.

> **⚠️ LUẬT CỠ MẪU (bắt buộc, đặc thù của skill ngành).** Phân biệt "chuẩn ngành" với "cách làm của
> một doanh nghiệp". Không được suy 1 công ty ra cả ngành. Mỗi khẳng định ở cấp ngành phải hoặc (a)
> dựa trên từ 3 doanh nghiệp trở lên và nói rõ cỡ mẫu, hoặc (b) bị hạ cấp thành ví dụ có tên công ty
> kèm theo. Đây là cách hỏng phổ biến nhất của nghiên cứu ngành, và là thứ làm mất uy tín nhanh nhất
> khi ngồi trước người trong nghề.

`SKILL_DIR` là thư mục chứa file này (thường `~/.claude/skills/csm-industry-learner`).

`LIBRARY` là `~/Downloads/industry-library`, thư viện ngành tích luỹ qua nhiều lần chạy.

## Ngôn ngữ

Ba thứ khác nhau, đừng gộp làm một:

- **Ngôn ngữ báo cáo.** Theo ngôn ngữ user đang dùng trong hội thoại, tự nhận, không hỏi.
- **Ngôn ngữ tra cứu.** Tiếng bản địa của thị trường, cộng tiếng Anh cho bối cảnh xuyên biên giới.
  Độc lập với ngôn ngữ báo cáo: tra thị trường Indonesia thì chạy truy vấn tiếng Indonesia dù báo cáo
  viết tiếng Việt. Ba nhóm nguồn ROI cao nhất của skill này là tin tuyển dụng, diễn đàn nghề và văn
  bản pháp lý, gần như không có bản tiếng Anh.
- **Ngôn ngữ thuật ngữ.** Glossary luôn giữ thuật ngữ gốc kèm cách người trong nghề thật sự gọi, kể
  cả khi phần còn lại viết bằng ngôn ngữ khác. Thuật ngữ có cả dạng bản địa lẫn dạng Anh thì ghi cả
  hai và nói rõ cái nào dùng khi nói chuyện.

## Triết lý thiết kế
1. Học theo dòng chảy công việc, không theo bách khoa toàn thư. Quy mô thị trường và top player nghe
   thạo tin nhưng không giúp hỏi được câu sắc. Chuỗi quy trình và KPI của từng vai trò thì có.
2. Pain nằm ở chỗ bàn giao: giữa hai phòng ban, giữa hai ca, giữa hai hệ thống. Lớp 2 tồn tại để tìm
   đúng những chỗ đó.
3. Người dùng chỉ đổi hành vi khi cái mới giúp họ đẹp KPI. Lớp 3 là lớp quyết định adoption, nên nó
   không được phép mỏng.
4. Khoảng trống là phát hiện. "Không tìm được KPI của trưởng ca" nói cho user biết chính xác phải hỏi
   ai. Một con số bịa thì phá hỏng độ tin của cả báo cáo.
5. Không đóng vai chuyên gia ngành. Vị thế đúng là đủ hiểu để hỏi đúng chỗ, còn đặc thù bên khách thì
   khách dạy. Văn bản phải phản ánh vị thế đó.
6. Cho xem trước khi ghi file. Hồ sơ ngành sẽ được tái dùng nhiều lần, sai một lần thì sai lâu.
7. Mỗi lần chạy phải làm lần sau nhanh hơn. Đó là việc của `_index.md`.

---

## Quy trình 7 bước

### Bước 1: Scope (ngắn, không phỏng vấn dài)

Đọc `LIBRARY/_index.md` nếu có, bỏ qua im lặng nếu chưa có. Rồi chốt trong 1-2 dòng, chỉ hỏi cái
thật sự mơ hồ:

- **Ngành + lát cắt.** "Bán lẻ" quá rộng, chuỗi tiện lợi và điện máy và thời trang vận hành khác hẳn
  nhau. Nếu user nêu ngành rộng, đề xuất 2-3 lát cắt hẹp và để họ chọn.
- **Thị trường, quy mô, ngôn ngữ tra cứu.** Thị trường nào (một nước hay cả khu vực), phân khúc nào
  (SMB hay doanh nghiệp 100+ điểm bán), và tra bằng tiếng gì. Thị trường và quy mô ảnh hưởng nặng tới
  Lớp 1 và Lớp 5. Ngôn ngữ tra mặc định là tiếng bản địa của thị trường cộng tiếng Anh; thị trường đã
  rõ thì tự chốt theo mặc định, nói ra một dòng, không hỏi lại.
- **Độ sâu.** Nhanh (khoảng 8-12 nguồn) hay đầy đủ (18-28 nguồn).
- **Có sẵn gì không.** Link, tài liệu SOP, ghi chú buổi gặp trước, transcript. Nếu user đưa, đọc
  trước tiên và vẫn trích nguồn như mọi nguồn khác, ghi rõ là nguồn nội bộ.
- Nếu `_index.md` đã có ngành lân cận, nói ra và hỏi có tái dùng phần chung không.

Không phỏng vấn quá 4 câu. Nghiên cứu mới là giá trị, scoping chỉ là chốt chặn.

### Bước 2: Nghiên cứu 5 lớp (phần việc chính)

Làm theo `references/layer-playbook.md`: mẫu truy vấn cho từng lớp, thứ tự ưu tiên nguồn, và các cạm
bẫy. Nguyên tắc vận hành:

- Batch song song. Phát nhiều `WebSearch` độc lập trong một lượt, rồi chỉ `WebFetch` những trang có
  vẻ sơ cấp. Đừng fetch tuần tự từng trang một.
- Lấy mẫu từ 3 doanh nghiệp khác nhau trở lên trước khi phát biểu bất kỳ điều gì ở cấp ngành.
- Dừng đúng lúc. Khi truy vấn mới không còn ra sự thật mới thì dừng, kể cả khi chưa chạm trần số
  nguồn. Ngược lại nếu Lớp 3 vẫn rỗng thì chưa được dừng dù đã đủ nguồn, vì Lớp 3 là lớp không thể
  thiếu.
- Sổ nguồn ghi ngay khi đọc được sự thật, trong file scratch của session:
  ```
  S1 | https://…/tuyen-dung-truong-ca | JD Trưởng ca, Công ty A | tuyển dụng | vi | 2026-08-09
  S2 | https://…/bao-cao-thuong-nien-2025.pdf | BCTN 2025 mục Rủi ro, Công ty B | sơ cấp | vi | 2026-08-09
  ```
  Gắn `S#` vào lúc đọc, không gắn sau. Sự thật nào không ghi nguồn ngay thì coi như chưa verify.
- Suy luận cũng cấp ID ngay tại chỗ, cùng lúc với `S#`: `H1`, `H2`, … đánh số chạy suốt báo cáo. Cấp
  muộn là quên, và mọi `H#` sau đó phải có đúng một dòng trong sổ giả thuyết ở "Trang mang đi họp".
- Chạy truy vấn bằng ngôn ngữ tra đã chốt ở Bước 1. Mẫu truy vấn trong playbook viết bằng tiếng Việt
  làm ví dụ, phải dịch sang ngôn ngữ thị trường trước khi dùng.
- Nếu một nguồn chỉ còn tồn tại dưới dạng tóm tắt kết quả tìm kiếm vì fetch trực tiếp thất bại, đánh
  dấu điều đó trong sổ nguồn và hạ độ tin của sự thật lấy từ nó.

### Bước 3: Soạn báo cáo theo `references/report-template.md`

Template quy định đầy đủ các mục và các bảng. Năm điều dễ làm ẩu, nhắc lại ở đây:
- Cột bằng chứng trong bảng Lớp 3 phải là số hoặc câu trích nguyên văn có `[S#]`, không được là nhận
  định của người viết.
- `[S#]` nằm trong ô chứa sự thật, không tách thành cột "Nguồn" riêng ở cuối hàng. Ngoại lệ duy nhất
  là cột *Bằng chứng* của Lớp 3.
- Sơ đồ không mang thông tin mới. Mọi node và mọi cạnh phải truy được về một dòng trong bảng ngay
  phía trên nó.
- Ô trống thì ghi "Chưa tìm được trong nguồn đã tra", không để trắng vì người đọc dễ hiểu nhầm thành
  "không có".
- Mâu thuẫn giữa các nguồn thì nêu ra, nói rõ nguồn nào được coi là hiện hành và vì sao. Đừng im lặng
  chọn một cái.

### Bước 4: Tự kiểm trước khi cho user xem

Chạy quality bar trong `references/report-template.md`. Tối thiểu:

- [ ] Mọi số/tên/ngày có `[S#]` tồn tại trong phụ lục; không `S#` nào trong phụ lục bị bỏ không dùng.
- [ ] Mọi khẳng định cấp ngành nêu cỡ mẫu từ 3 doanh nghiệp trở lên, hoặc đã hạ cấp thành ví dụ có
      tên công ty.
- [ ] Bảng Lớp 3 không có ô "bằng chứng" nào là suy đoán không nguồn.
- [ ] Không ô nào bị bỏ trắng; ô thiếu ghi đúng câu "Chưa tìm được trong nguồn đã tra".
- [ ] Có ngày tra cứu và cảnh báo dữ liệu ngành phân rã theo quý.
- [ ] Phép thử "một ngày": báo cáo có đủ chi tiết để kể một ngày làm việc của người dùng cuối (không
      phải người ký hợp đồng) không? Nếu không, Lớp 3 còn mỏng, quay lại Bước 2.
- [ ] Mọi suy luận có ID `H#` duy nhất, và mọi `H#` có đúng một dòng trong sổ giả thuyết, ngược lại
      cũng vậy. Không còn `H` trần nào sót.
- [ ] Bảng độ phủ điền đủ 5 lớp; mỗi lớp có dòng "Chốt lại"; "Trang mang đi họp" không rỗng.
- [ ] Mọi node và cạnh trong mọi sơ đồ truy được về một dòng trong bảng ngay trên nó.
- [ ] Header ghi rõ thị trường và ngôn ngữ tra cứu. Thị trường không nói tiếng Anh mà toàn bộ nguồn
      là tiếng Anh thì bảng độ phủ phải nói thẳng ra.

Sửa hết cái fail rồi mới sang Bước 5.

### Bước 5: Cổng duyệt, rồi mới ghi file

In phần xương của báo cáo trong hội thoại: bảng "Độ phủ nghiên cứu" + "Đọc trong 60 giây" + "Trang
mang đi họp" + Lớp 2 + Lớp 3. Bảng độ phủ thay luôn cho ghi chú độ phủ viết bằng văn xuôi, vì nó đã
nói đủ: lớp nào mỏng, cỡ mẫu bao nhiêu, nguồn bằng tiếng gì. Hỏi duyệt hoặc sửa.

Sau khi user duyệt:
- Ghi `LIBRARY/<slug>/<slug>-industry-report.md`. `<slug>` là tên ngành dạng kebab-case không dấu, ví
  dụ `chuoi-tien-loi-vn`.
- Tạo hoặc append `LIBRARY/_index.md`: một dòng cho ngành này (ngày, lát cắt, số nguồn, đường dẫn) và
  bổ sung vào mục "mô-típ pain lặp lại xuyên ngành" những mô-típ vừa nhận ra.
- Nếu file đã tồn tại, đọc nó trước rồi hỏi user ghi đè hay tạo bản `-v2`. Không ghi đè im lặng, bản
  cũ có thể chứa ghi chú user tự thêm.

### Bước 6: Giai đoạn 2, mapping sản phẩm (tuỳ chọn)

Hỏi: "Có mapping sang sản phẩm của bạn luôn không?" Nếu user không muốn thì dừng ở Bước 5, vẫn là một
lượt hoàn chỉnh.

Nếu có:
1. Hỏi tên sản phẩm. Tra web các trang tính năng / tài liệu chính thức (`WebSearch` + `WebFetch`),
   ghi vào sổ nguồn với tiền tố `P#` để tách hẳn khỏi nguồn ngành `S#`.
2. Luôn hỏi thêm một lần: "Bạn có file hoặc nội dung mô tả tính năng muốn bổ sung không?" Trang công
   khai thường thiếu năng lực mới hoặc năng lực chỉ có trong bản enterprise. Nếu user đưa file hoặc
   dán nội dung, đọc và ưu tiên hơn nguồn web khi mâu thuẫn, ghi rõ điều đó trong header. Nếu user
   không có, nói rõ trong header rằng hồ sơ sản phẩm dựng từ nguồn công khai và có thể thiếu năng lực
   chưa lên web.
3. Soạn theo `references/mapping-template.md`, chạy quality bar trong đó, rồi cho user xem để duyệt.

### Bước 7: Ghi file mapping + đóng lượt

Sau khi duyệt, ghi `LIBRARY/<slug>/<slug>-product-mapping.md`, cùng luật không ghi đè im lặng.

Đóng lượt bằng đúng 4 thứ: đường dẫn 2 file, trỏ user vào mục "Trang mang đi họp" của báo cáo (sổ
giả thuyết cần khách xác nhận, 3 từ phải nói đúng, 1 điều dễ giết POC nhất), khoảng trống bằng chứng
lớn nhất và cách rẻ nhất để lấp nó, và gợi ý chạy `/customer-research-poc` cho một account cụ thể
trong ngành, cùng `/csm-onboarding-plan` khi đã có khách hàng thật.

Dặn thêm một câu: sau buổi gặp quay lại đánh dấu cột *Trạng thái* trong sổ giả thuyết và ghi một dòng
vào "Nhật ký kiểm chứng". Đó là thứ giữ cho hồ sơ ngành lớn lên bằng dữ liệu thật thay vì chỉ cũ đi
theo quý.

---

## Guardrails

- Không bịa số, tên, ngày, tên hệ thống. Không verify được thì ghi "Chưa tìm được trong nguồn đã
  tra"; suy luận thì gắn `H#` có ID kèm câu hỏi kiểm chứng.
- Sơ đồ không phải chỗ lách luật bằng chứng. Vẽ một node hay một mũi tên không có trong bảng phía
  trên nó cũng là bịa.
- Không suy một doanh nghiệp ra cả ngành. Nêu cỡ mẫu cho mọi khẳng định cấp ngành.
- Không nhầm quy mô tập đoàn với công ty con trong nước, không nhầm vốn hoá/định giá với doanh thu.
- Không viết bằng giọng chuyên gia ngành. Header báo cáo phải nhắc lại vị thế "đủ hiểu để hỏi đúng
  chỗ".
- Không ghi đè file hồ sơ ngành đã có mà chưa đọc và chưa hỏi user.
- Không đụng `lark-cli`, không tạo Lark Doc, không gửi tin nhắn, không đăng gì ra ngoài.
- Ghi ngày tra cứu. Cảnh báo user không trích số ngành đã cũ vào mặt khách hàng, họ biết số thật của
  họ. Hồ sơ ngành quá một quý thì nên chạy lại, không nên dùng lại nguyên trạng.
- Nghiên cứu dừng ở mức vai trò và tổ chức. Không tra cứu hay tổng hợp thông tin cá nhân của người cụ
  thể.
