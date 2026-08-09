# Mapping Template: nối ngành vào sản phẩm

Ghi ra `LIBRARY/<slug>/<slug>-product-mapping.md`. Đây là tài liệu nội bộ, chiến thuật, tách khỏi báo
cáo ngành để báo cáo ngành có thể chia sẻ rộng hơn.

Nguồn sản phẩm dùng tiền tố `P#`, tách hẳn khỏi nguồn ngành `S#`.

---

```markdown
# Mapping: <Sản phẩm> × <Ngành, lát cắt>

> **Dựa trên:** `<slug>-industry-report.md` (tra ngày <YYYY-MM-DD>)
> **Hồ sơ sản phẩm dựng từ:** <chọn một>
>   - nguồn công khai [P1–Pn]. ⚠️ có thể thiếu năng lực chưa lên web hoặc chỉ có ở bản enterprise
>   - nguồn công khai [P1–Pn] **+ tài liệu do user cung cấp** (`<tên file>`). Tài liệu user thắng khi
>     mâu thuẫn
> **Ngày lập:** <YYYY-MM-DD>

## Hồ sơ năng lực sản phẩm (rút gọn)

| Năng lực | Tính năng/module hiện thực nó | Nguồn |
|---|---|---|
| | | [P#] |

<Nếu có mâu thuẫn giữa tài liệu user và web, nêu ra ở đây và nói rõ đã lấy cái nào.>

---

## Bảng mapping

> **Luật cứng:** dòng nào không điền được cột *Chỉ số cải thiện* thì không được nằm trong bảng này,
> chuyển xuống mục "Tính năng chưa chứng minh được giá trị". Đây là cơ chế chống bán theo tính năng.

| Bước quy trình (Lớp 2) | Pain cụ thể | Bằng chứng | Năng lực sản phẩm | Tính năng/module | Chỉ số cải thiện | Ai được lợi (Lớp 3) |
|---|---|---|---|---|---|---|
| | | [S#] | | [P#] | <đo bằng gì, đo ở đâu> | <vai trò + KPI của họ> |

**Tính năng chưa chứng minh được giá trị** (giữ lại để không quên, nhưng không mang đi bán):

| Tính năng | Vì sao chưa gắn được vào chỉ số nào |
|---|---|
| | |

---

## 3 giả thuyết POC (xếp hạng)

Mỗi POC phải thoả cả 6 ràng buộc, nếu không thì không phải POC mà là dự án: 1 quy trình, 1 vai trò,
1 con số, 2–4 tuần, dữ liệu thật của khách, không phụ thuộc phòng ban thứ ba (nguyên nhân số một
khiến POC chết giữa chừng).

### POC #1: <tên>
- **Quy trình:** <một bước duy nhất trong Lớp 2>
- **Vai trò dùng thật:** <một vai trò, số người dự kiến>
- **Con số chứng minh:** <chỉ số duy nhất, đo trước và sau, lấy ở đâu>
- **Thời lượng:** <2–4 tuần>
- **Sponsor cần có:** <chức danh>
- **Tiêu chí thành công (viết trước, khách xác nhận):** <ngưỡng cụ thể>
- **Tiêu chí thất bại:** <ngưỡng cụ thể, dám viết ra thì POC mới có giá trị>
- **Ngoài phạm vi:** <nêu rõ hệ thống nào vẫn là hệ thống của sự thật>
- **Phụ thuộc phòng ban khác?** Không / <nếu có thì đây không phải POC ưu tiên>

### POC #2: <tên>
<như trên>

### POC #3: <tên>
<như trên>

---

## 10 câu hỏi discovery, làm rõ doanh nghiệp này khác chuẩn ngành ở đâu

> Mỗi câu phải: (a) neo vào một khẳng định trong báo cáo ngành, (b) hỏi doanh nghiệp này lệch chuẩn
> ngành ở chỗ nào, (c) là câu chỉ người hiểu ngành mới hỏi được.
>
> Mẫu tốt: *"Khi ca đêm bàn giao cho ca sáng, biên bản đó đang ghi ở đâu và ai đọc nó?"*
> Mẫu xấu: *"Anh gặp khó khăn gì trong quản lý?"*
>
> Mọi **H** trong báo cáo ngành phải có ít nhất một câu ở đây kiểm chứng nó.

| # | Câu hỏi | Neo vào | Nếu trả lời khác chuẩn ngành thì sao |
|---|---|---|---|
| 1 | | Lớp <n> / **H** <…> | <đổi POC nào, đổi lập luận nào> |

---

## Landmine, chỗ dễ chết

| Landmine | Nguồn gốc | Dấu hiệu sớm | Xử lý |
|---|---|---|---|
| <ràng buộc Lớp 5 va vào sản phẩm> | | | |
| <hệ thống lõi không thay được> | | | |
| <vai trò sẽ phản đối và vì sao, KPI của họ bị đụng> | | | |

---

## Sản phẩm KHÔNG làm được gì cho ngành này

> Mục bắt buộc, không được rỗng. Biết trước ranh giới đáng giá hơn một bảng mapping toàn màu xanh, và
> giữ được uy tín khi khách hỏi ngược.

| Nhu cầu của ngành | Sản phẩm không đáp ứng vì | Khách thường giải quyết bằng gì |
|---|---|---|

---

## Phụ lục · Nguồn sản phẩm

| ID | URL / tên file | Tài liệu | Ngày |
|---|---|---|---|
| P1 | | | |
```

---

## Quality bar, chạy hết trước khi cho user xem

- [ ] Mọi dòng trong bảng mapping có `[S#]` ở cột bằng chứng (pain phải có nguồn từ báo cáo ngành).
- [ ] Mọi dòng trong bảng mapping có cột *Chỉ số cải thiện* được điền. Dòng nào không có đã bị chuyển
      xuống mục "chưa chứng minh được giá trị".
- [ ] Cột *Ai được lợi* nêu đúng vai trò có trong bảng Lớp 3, kèm KPI của họ, không ghi chung chung
      kiểu "toàn công ty".
- [ ] Mọi năng lực sản phẩm có `[P#]`; không có tính năng nào được nêu từ trí nhớ mà không có nguồn.
- [ ] Header nói rõ hồ sơ sản phẩm dựng từ nguồn công khai hay có tài liệu user bổ sung.
- [ ] Đủ 3 POC, mỗi cái thoả cả 6 ràng buộc, có tiêu chí thất bại viết trước.
- [ ] Đủ 10 câu hỏi discovery; mỗi câu neo được vào một mục cụ thể trong báo cáo ngành.
- [ ] Mọi **H** trong báo cáo ngành có ít nhất một câu hỏi kiểm chứng.
- [ ] Mục "sản phẩm không làm được gì" không rỗng.
- [ ] Không có tuyên bố hiệu quả nào lấy từ case study marketing của bất kỳ nhà cung cấp nào.
