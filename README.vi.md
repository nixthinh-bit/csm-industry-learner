# csm-industry-learner (Tiếng Việt)

> Bản chính bằng tiếng Anh: [README.md](README.md)

Skill cho Claude Code: từ **tên một ngành** → **báo cáo ngành có trích nguồn**, dựng theo khung vận
hành 5 lớp — sau đó, nếu muốn, thêm **bảng mapping sản phẩm** kèm giả thuyết POC xếp hạng và bộ câu
hỏi discovery.

> Gõ / Trigger: **`/csm-industry-learner`**

---

## Skill này giải quyết việc gì

Trước khi bước vào một ngành mới, phần lớn CSM và sales đọc báo cáo quy mô thị trường và danh sách
top player. Nghe rất thạo tin. Nhưng gần như không giúp hỏi được câu hỏi sắc trong buổi discovery.

Skill này học một ngành theo đúng cách công việc thật sự chảy qua nó:

1. **Kinh tế đơn vị** — họ kiếm tiền trên đơn vị gì, biên mỏng hay dày, mùa thấp điểm rơi vào lúc
   nào (và vì vậy khách có thực sự rảnh để chạy một dự án triển khai hay không).
2. **Chuỗi quy trình lõi** — từng bước từ lúc phát sinh nhu cầu tới lúc thu tiền, đặc biệt là **chỗ
   nào bàn giao giữa hai phòng ban hoặc hai ca**. Pain gần như luôn nằm ở chỗ bàn giao, không nằm
   trong lòng một quy trình của một đội.
3. **Vai trò × KPI × pain** — mỗi vai trò bị đo bằng con số nào, ai đánh giá họ. Người dùng chỉ đổi
   hành vi khi công cụ mới giúp họ đẹp KPI — đây là lớp quyết định adoption, nên không được phép mỏng.
4. **Từ vựng & hệ thống** — 20–30 từ người trong nghề thật sự dùng (không phải định nghĩa sách vở) và
   hệ thống đang chạy (ERP/POS/CRM/phần mềm chuyên ngành), để biết mình đang ở vị thế tích hợp hay
   thay thế.
5. **Ràng buộc cứng** — pháp lý, kiểm toán, an toàn, ca kíp, thiết bị người dùng cuối. Thứ hay giết
   POC nhất và thường bị phát hiện quá muộn.

**Điểm khác biệt quan trọng nhất: skill từ chối đoán mò.** Mọi số, ngày, tên hệ thống đều mang trích
dẫn nguồn. Cái gì không verify được thì ghi thẳng *"Chưa tìm được trong nguồn đã tra."* Cái gì là suy
luận thì gắn nhãn **H** (giả thuyết) kèm câu hỏi discovery để kiểm chứng.

**Nghiên cứu ngành có một cách hỏng mà nghiên cứu một công ty không có: suy một công ty ra cả ngành.**
Mọi khẳng định cấp ngành phải hoặc trích dẫn ≥3 doanh nghiệp khác nhau, hoặc bị hạ cấp thành ví dụ có
tên. Đây là luật cứng, không phải gợi ý về văn phong — và là cách nhanh nhất làm mất uy tín trước
người thật sự làm trong ngành.

## Quy trình hai giai đoạn

**Giai đoạn 1 — Báo cáo ngành (luôn chạy).**
Chốt phạm vi trong 1–2 dòng (lát cắt ngành, địa lý, độ sâu) → nghiên cứu web song song theo 5 lớp,
ưu tiên tin tuyển dụng và mục "Rủi ro" trong báo cáo thường niên hơn là các báo cáo quy mô thị
trường → tự kiểm theo quality bar, bao gồm **phép thử "một ngày"**: có kể được một ngày làm việc của
người dùng *tuyến đầu* (không phải người ký hợp đồng) không? Nếu không thì nghiên cứu chưa xong → cho
xem bản nháp để duyệt → ghi ra file Markdown, append một dòng (kèm mô-típ pain lặp lại nếu có) vào
chỉ mục thư viện đang tích luỹ.

**Giai đoạn 2 — Mapping sản phẩm (tuỳ chọn, luôn được hỏi).**
Nêu tên sản phẩm → skill tự tra các trang tính năng công khai → luôn hỏi thêm bạn có file/tài liệu
tính năng muốn bổ sung không, và tài liệu đó thắng web khi mâu thuẫn → bảng mapping mà mỗi dòng bắt
buộc có chỉ số đo được (dòng nào không có bị chuyển sang mục "chưa chứng minh được giá trị") → 3 giả
thuyết POC xếp hạng, mỗi cái ràng buộc 1 quy trình · 1 vai trò · 1 con số · 2–4 tuần · dữ liệu thật ·
không phụ thuộc phòng ban thứ ba → 10 câu hỏi discovery làm rõ đúng chỗ doanh nghiệp *này* lệch chuẩn
ngành → landmine → và mục bắt buộc: sản phẩm KHÔNG làm được gì cho ngành này.

## Đầu ra

Chỉ Markdown trên máy. Không tạo Lark Doc, không đụng `lark-cli` — skill này không bao giờ chạm vào
tenant Lark của bạn. File nằm ở:

```
~/Downloads/industry-library/
├── _index.md
└── <slug-ngành>/
    ├── <slug>-industry-report.md
    └── <slug>-product-mapping.md   (chỉ khi bạn chạy Giai đoạn 2)
```

`_index.md` là thứ khiến ngành thứ ba nhanh hơn ngành thứ nhất — mỗi lần chạy đều đọc nó trước khi
scoping, và bổ sung mô-típ pain lặp lại nếu nhận ra.

## Guardrails

- Không bao giờ bịa số, tên, ngày, tên hệ thống. Không verify được → *"Chưa tìm được trong nguồn đã
  tra."* Suy luận → **H** kèm câu hỏi kiểm chứng.
- Không bao giờ suy một công ty ra cả ngành.
- Không viết bằng giọng chuyên gia ngành — báo cáo luôn tự nhận "đủ để hỏi đúng chỗ", không phải kết
  luận thay khách hàng.
- Không ghi đè file báo cáo đã có mà chưa đọc và chưa hỏi.
- Không đụng `lark-cli`, không tạo Lark Doc, không gửi tin nhắn.

## Cần chuẩn bị gì

- **Tìm kiếm web** khả dụng trong Claude Code (`WebSearch` / `WebFetch`) — skill này lấy nghiên cứu
  làm gốc; không có thì không có gì để trích dẫn.

Chỉ vậy thôi. Không cần CLI, không cần auth, không cần API key.

## Cài đặt

```bash
git clone https://github.com/nixthinh-bit/csm-industry-learner.git
mkdir -p ~/.claude/skills
cp -R csm-industry-learner ~/.claude/skills/csm-industry-learner
```

Khởi động lại Claude Code để nó nạp skill mới.

### Là một phần của plugin

Đặt thư mục này dưới `skills/` của plugin:

```
your-plugin/
  skills/
    csm-industry-learner/
      SKILL.md
      references/
```

## Kiểm tra

Trong Claude Code:

```
/csm-industry-learner logistics tại Việt Nam
```

Kỳ vọng: skill hỏi 2–4 câu scoping ngắn, rồi nghiên cứu bằng nhiều `WebSearch` song song, rồi cho
xem bản nháp báo cáo kèm trích dẫn `[S#]` trước khi ghi bất kỳ file nào ra đĩa.

## Cách dùng

```
/csm-industry-learner <tên ngành, ví dụ "bán lẻ tiện lợi tại Việt Nam">
```

Bạn sẽ được hỏi vài câu scoping ngắn (lát cắt ngành, địa lý/quy mô, độ sâu nghiên cứu, có sẵn tài
liệu gì không). Trả lời gọn — phần giá trị nằm ở bước nghiên cứu.

Skill sau đó tự nghiên cứu, tự kiểm, rồi cho bạn xem bản nháp để duyệt trước khi ghi file. Sau khi
báo cáo được lưu, skill hỏi bạn có muốn chạy Giai đoạn 2 (mapping sản phẩm) không — đồng ý và nêu tên
sản phẩm, hoặc từ chối và bạn đã có một deliverable hoàn chỉnh, độc lập.

## Skill liên quan

Skill này đứng **trước** bước nghiên cứu từng khách hàng cụ thể: nó xây kiến thức ngành dùng lại
được, không phải một bản brief cho một công ty. Khi đã chọn được công ty mục tiêu trong ngành đó,
chuyển sang skill nghiên cứu cấp doanh nghiệp (ví dụ `customer-research-poc`) để ra brief riêng cho
account đó.

## Giấy phép

MIT — xem [LICENSE](LICENSE).
