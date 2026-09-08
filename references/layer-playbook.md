# Layer Playbook: tra 5 lớp thế nào cho ra thứ dùng được

Tài liệu này trả lời: với mỗi lớp, tra ở đâu, hỏi câu gì, và sai ở đâu.

---

## Thứ tự ưu tiên nguồn (khác hẳn nghiên cứu một doanh nghiệp)

Xếp theo ROI thực tế, cao xuống thấp. Đây là điểm khác biệt lớn nhất so với `customer-research-poc`:
nghiên cứu ngành ăn nguồn vận hành, không ăn nguồn tài chính.

| # | Nguồn | Nuôi lớp nào | Vì sao mạnh |
|---|---|---|---|
| 1 | Tin tuyển dụng của doanh nghiệp trong ngành | 3, 4 | Mô tả chính xác công việc hằng ngày, công cụ đang chạy, và KPI được đo. Là nguồn duy nhất nói thẳng "quản lý X cửa hàng, báo cáo Y hằng ngày, sử dụng phần mềm Z". Bị bỏ qua nhiều nhất. |
| 2 | Mục "Rủi ro" + "Thảo luận của Ban điều hành" trong báo cáo thường niên / bản cáo bạch của doanh nghiệp niêm yết cùng ngành | 1, 5 | Doanh nghiệp tự khai điểm yếu vận hành bằng ngôn ngữ chính xác và có số. Bỏ qua phần marketing đầu báo cáo. |
| 3 | Trang sản phẩm / B2B / tuyển dụng trên site của chính doanh nghiệp | 1, 2 | Thường là chỗ cập nhật nhất về quy mô vận hành (số điểm bán, số nhân sự, vùng phủ), mới hơn trang "Về chúng tôi", mới hơn nhiều so với báo chí. |
| 4 | Văn bản pháp lý, quy chuẩn, thông tư ngành | 5 | Ràng buộc cứng là thứ giết POC nhiều nhất. Nguồn này chính xác và không phân rã nhanh. |
| 5 | Diễn đàn / hội nhóm nghề, hội chợ ngành, bài chia sẻ của người trong nghề | 3, 4 | Ngôn ngữ thật và than phiền thật. Là nơi lấy được cách người ta thật sự gọi một thứ. |
| 6 | Nhà cung cấp phần mềm chuyên ngành (trang khách hàng, case study) | 2, 4 | Họ mô tả quy trình ngành rất sát để bán hàng. Đọc phần mô tả quy trình, bỏ qua phần con số hiệu quả vì đó là marketing. |
| 7 | Báo cáo thị trường, phân tích ngành | bối cảnh | Để cuối. Hữu ích cho câu mở đầu, gần như vô dụng cho việc thiết kế POC. |

---

## Bản địa hoá truy vấn

Mẫu truy vấn trong tài liệu này viết bằng tiếng Việt làm ví dụ. Dịch sang ngôn ngữ thị trường trước
khi chạy, và đừng dịch từng chữ: dùng đúng cách người bản địa gọi tên chức danh, tên tài liệu, tên
loại giấy tờ.

- **Tra bằng tiếng bản địa:** tin tuyển dụng, diễn đàn nghề, văn bản pháp lý, trang doanh nghiệp nội
  địa. Đây đúng là nhóm 1, 4, 5 trong bảng trên, tức nhóm ROI cao nhất, và gần như không có bản tiếng
  Anh.
- **Tra bằng tiếng Anh:** doanh nghiệp niêm yết có công bố song ngữ, báo cáo ngành cấp khu vực, nhà
  cung cấp phần mềm quốc tế.
- Không hardcode tên trang cụ thể của bất kỳ thị trường nào. Tìm theo *loại nguồn*: sàn tuyển dụng
  lớn nhất thị trường, cổng công bố thông tin của sàn chứng khoán, cổng văn bản của cơ quan quản lý
  ngành, hội nhóm nghề. Đó là thứ giữ cho skill dùng được ở thị trường mới mà không phải sửa file.

---

## Lớp 1 · Kinh tế đơn vị

Cần ra được: họ kiếm tiền trên đơn vị gì, biên lợi nhuận mỏng hay dày, chu kỳ mùa vụ, đâu là mùa rảnh
để triển khai, chi phí lớn nhất trong cơ cấu.

Mẫu truy vấn:
- `"<ngành>" biên lợi nhuận gộp báo cáo thường niên`
- `"<ngành>" doanh thu trên mỗi <đơn vị: cửa hàng / m2 / giường / lô>`
- `"<ngành>" mùa cao điểm thấp điểm Việt Nam`
- `<công ty niêm yết trong ngành> báo cáo thường niên "rủi ro" filetype:pdf`

Vì sao CSM cần: biên mỏng thì mọi lập luận giá trị phải quy ra tiền, không được nói "tiện lợi hơn".
Mùa vụ quyết định lúc nào khách có thể triển khai. Đưa kế hoạch onboarding vào đúng mùa cao điểm là
cách chắc chắn nhất để dự án đứng hình.

Cạm bẫy: vốn hoá, định giá, vốn huy động không phải doanh thu. Số của tập đoàn không phải số của công
ty con trong nước. Doanh thu không phải lợi nhuận, ngành có doanh thu nghìn tỷ vẫn có thể lãi vài
phần trăm.

---

## Lớp 2 · Chuỗi quy trình lõi

Cần ra được: từ lúc phát sinh nhu cầu đến lúc thu tiền đi qua bao nhiêu bước, phòng ban nào chủ trì
bước nào, chỗ nào bàn giao giữa hai phòng ban hoặc hai ca.

Mẫu truy vấn:
- `quy trình "<ngành>" từ <điểm đầu> đến <điểm cuối>`
- `SOP "<ngành>" <tên công đoạn>`
- `<phần mềm chuyên ngành> "<ngành>" quy trình nghiệp vụ`
- Tin tuyển dụng của các vị trí nối giữa hai phòng ban (điều phối, kế hoạch, QC), JD của họ mô tả
  chính xác các điểm bàn giao.

Vì sao CSM cần: pain gần như luôn nằm ở chỗ bàn giao, không nằm trong lòng một phòng ban. Trong lòng
một phòng ban người ta đã tự tối ưu rồi, chỗ bàn giao thì không ai sở hữu.

Cạm bẫy: quy trình trên giấy không phải quy trình thực tế. Đánh dấu rõ cái nào lấy từ SOP/tài liệu
chuẩn, có thể là lý thuyết, và cái nào lấy từ mô tả của người làm thật. Khi hai cái lệch nhau, chính
khoảng lệch đó là pain, ghi nó lại.

---

## Lớp 3 · Vai trò × KPI × pain (lớp quan trọng nhất, không được mỏng)

Cần ra được: mỗi vai trò bị đo bằng con số nào, ai thưởng/phạt họ, công việc thủ công nào ngốn thời
gian của họ.

Mẫu truy vấn:
- `tuyển dụng "<chức danh>" "<ngành>" mô tả công việc KPI`
- `"<chức danh>" "<ngành>" báo cáo hằng ngày`
- `"<chức danh>" chia sẻ nghề khó khăn` trên diễn đàn, mạng xã hội nghề nghiệp

Cách khai thác JD cho đúng: đọc từ 10 JD trở lên của 3 vị trí khác nhau trở lên (vận hành tuyến đầu,
trưởng nhóm/ca, quản lý cấp trung). Trích ra: động từ lặp lại nhiều nhất là công việc hằng ngày, con
số xuất hiện trong phần "yêu cầu/chỉ tiêu" là KPI, tên phần mềm được nêu là Lớp 4.

Câu "báo cáo cho ai" trong JD là thứ nuôi sơ đồ *ai đo ai* của Lớp 3. Tra là để vẽ được sơ đồ đó,
không phải để có thêm một bảng.

Vì sao CSM cần: người dùng chỉ đổi hành vi khi cái mới giúp họ đẹp KPI. Không biết KPI thì mọi kế
hoạch adoption đều là đoán.

Cạm bẫy: KPI trong JD tuyển dụng là KPI được công bố, KPI thật đôi khi khác. Đánh dấu `H#` khi suy ra
KPI thật, để dành cho câu hỏi discovery. Không được lấy KPI của một công ty làm KPI của cả ngành.

---

## Lớp 4 · Từ vựng & hệ thống đang có

Cần ra được: 20-30 thuật ngữ ngành kèm cách người trong nghề thật sự nói, các hệ thống lõi phổ biến
(ERP, POS, MES, HIS, WMS, CRM, phần mềm chuyên ngành nội địa).

Mẫu truy vấn:
- `tuyển dụng "<ngành>" "sử dụng phần mềm"` hoặc `... "kinh nghiệm <tên hệ thống>"`
- `"<ngành>" Việt Nam phần mềm quản lý phổ biến`
- `thuật ngữ "<ngành>" là gì`
- Diễn đàn nghề: đọc cách người ta viết tắt và nói tắt.

Khi tìm được một hệ thống, tìm luôn xem nó gắn vào bước nào của Lớp 2. Đó là thứ nuôi *bản đồ hệ
thống*, và bước nào không có hệ thống nào gắn vào chính là khoảng trống đáng chú ý nhất.

Vì sao CSM cần: sai từ vựng là mất uy tín trong 5 phút đầu. Hệ thống hiện có quyết định bạn ở vị thế
tích hợp hay thay thế, hai câu chuyện bán hàng hoàn toàn khác nhau, và nhầm thì mất deal.

Cạm bẫy: đừng chép định nghĩa sách vở. Một thuật ngữ có định nghĩa chuẩn nhưng người trong nghề gọi
bằng tên khác thì phải ghi cả hai, và ghi rõ cái nào dùng khi nói chuyện. Mỗi mục glossary gắn `[S#]` nếu đã verify,
`H#` nếu là suy luận.

---

## Lớp 5 · Ràng buộc cứng

Cần ra được: pháp lý & tuân thủ, yêu cầu kiểm toán/lưu trữ chứng từ, an toàn lao động, ca kíp & tính
chất "không ngồi bàn giấy" của người dùng, thiết bị họ có trong tay, mức độ số hoá thực tế của người
dùng cuối, rào cản hạ tầng (mạng, thiết bị cũ).

Mẫu truy vấn:
- `quy định pháp luật "<ngành>" Việt Nam thông tư nghị định`
- `"<ngành>" yêu cầu lưu trữ hồ sơ chứng từ bao nhiêu năm`
- `"<ngành>" làm việc theo ca an toàn lao động`

Vì sao CSM cần: đây là thứ giết POC nhiều nhất và gần như luôn bị phát hiện quá muộn. Người dùng
tuyến đầu không có laptop, không có email công ty, hoặc không được dùng điện thoại trong ca. Bất kỳ
điều nào trong đó cũng đủ làm hỏng một kế hoạch triển khai đẹp trên giấy.

Kết mục này bằng một dòng: thứ hay giết POC nhất trong ngành này là gì.

---

## Mô-típ pain lặp lại xuyên ngành

Sau vài ngành sẽ thấy các mô-típ này quay lại với tên gọi khác nhau. Chủ động dò chúng, dò trúng thì
rút ngắn được nhiều giờ tra cứu.

- Bàn giao ca / bàn giao ngày: biên bản ghi ở đâu, ai đọc, mất mát thông tin gì.
- Đối soát chứng từ: giữa hệ thống và giấy, giữa kho và sổ, giữa thu ngân và ngân hàng.
- Duyệt nhiều tầng: thời gian chờ duyệt vượt xa thời gian làm thật.
- Báo cáo thủ công cuối tháng/cuối ngày: người ta chép tay từ hệ thống này sang bảng tính khác.
- Dữ liệu tuyến đầu không lên được hệ thống: vì người ở tuyến đầu không có công cụ nhập.
- Kiến thức nằm trong đầu vài người: nghỉ việc là mất, đào tạo người mới rất lâu.
- Nhiều nguồn sự thật cho cùng một con số: mỗi phòng ban có bản riêng, họp thì cãi nhau về số.

Khi nhận ra một mô-típ trong ngành đang tra, ghi nó vào mục *Mô-típ pain lặp lại* của báo cáo và
append vào `_index.md` để lần sau dò trúng ngay.

---

## Cạm bẫy chung

- Suy một công ty ra cả ngành. Sai lầm số một. Luôn nêu cỡ mẫu.
- Nhầm chuẩn ngành với chuẩn của phân khúc. Chuỗi 500 cửa hàng và chuỗi 15 cửa hàng khác nhau về gần
  như mọi thứ ở Lớp 2 và Lớp 5. Ghi rõ báo cáo này viết cho phân khúc nào.
- Lấy case study của nhà cung cấp phần mềm làm bằng chứng về hiệu quả. Dùng phần mô tả quy trình, bỏ
  phần "giảm 70% thời gian".
- Nội dung do AI sinh ra trên các trang SEO ngành. Dấu hiệu: không có tác giả, không có số cụ thể,
  câu chữ chung chung. Không dùng làm nguồn.
- Dữ liệu cũ. Ghi ngày của mọi số. Ngành thay đổi nhanh nhất ở Lớp 4 (hệ thống) và Lớp 5 (pháp lý).
- Thị trường không nói tiếng Anh mà toàn bộ nguồn lấy được là tiếng Anh. Đó là dấu hiệu nghiên cứu
  hụt, không phải dấu hiệu ngành minh bạch: nghĩa là chưa chạm được vào tin tuyển dụng, diễn đàn nghề
  và văn bản pháp lý bản địa. Nói thẳng điều đó trong bảng độ phủ thay vì im lặng.
- Tra quá lâu. Kiến thức ngành có tỷ suất giảm dần rất nhanh. Hết dấu hiệu ra sự thật mới thì dừng và
  mang bản nháp đi hỏi người thật, đó là cách học nhanh nhất, không phải tra thêm.
