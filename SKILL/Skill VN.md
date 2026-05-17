---
name: use-case-writer
description: Tạo tài liệu đặc tả Use Case bằng Markdown tiếng Anh theo chuẩn mẫu 13 trường của IT BA (Karl Wiegers / IIBA). Sử dụng khi BA cần xác định phạm vi, phân tích, viết tài liệu, tinh chỉnh hoặc review một Use Case. Các trigger bao gồm "write a use case", "draft UC", "use case specification", "analyze UC scope", "split feature into use cases", "review my UC", "write normal course / alternative course / exceptions", "define actors", và các từ tương đương tiếng Việt như "viết use case", "viết UC", "đặc tả use case", "phân tích use case", "review UC". Cũng trigger khi người dùng dán một tính năng/BRD/PRD và yêu cầu chuyển nó thành các Use Case. Skill áp dụng các nguyên tắc của Cockburn (bài kiểm tra giờ nghỉ giải lao, các cấp độ mục tiêu) và chạy danh sách kiểm tra chất lượng 20 điểm. Đầu ra là Markdown tiếng Anh với 13 trường (Actor, Description, Pre/Postconditions, Priority, Frequency, Normal/Alternative Courses, Exceptions, Includes, Special Req, Assumptions, Notes). KHÔNG sử dụng cho Agile User Stories, PRD/URD/SRS hoặc sơ đồ UML.
author: Phúc NT @ BA Zone
source: https://github.com/ba-zone
---

# Use Case Writer — Kỹ năng dành cho IT Business Analyst
> bởi **Phúc NT** · BA Zone · Digital School

Kỹ năng này giúp các IT BA **xác định phạm vi, phân tích và tài liệu hóa các Use Case** bằng Markdown tiếng Anh theo chuẩn mẫu 13 trường (phong cách Karl Wiegers / IIBA), với các best practice từ "Writing Effective Use Cases" của Alistair Cockburn và IIBA BABOK Guide.

Được phát triển bởi **Phúc NT** như một phần của chương trình đào tạo **Digital School** bởi **BA Zone** — Cộng đồng Business Analyst & Product Owner Việt Nam.

## Khi nào nên sử dụng kỹ năng này

Kích hoạt kỹ năng này bất cứ khi nào người dùng cần:
- Lên bản thảo một Use Case mới từ mô tả tính năng, BRD, hoặc PRD
- Tinh chỉnh hoặc review một Use Case hiện có (tính đầy đủ, tính chính xác)
- Chia một tính năng lớn thành nhiều Use Case nhỏ hơn (xác định phạm vi)
- Viết một phần cụ thể: Normal Course (Luồng cơ bản), Alternative Course (Luồng thay thế), Exceptions (Ngoại lệ)
- Đánh giá một Use Case dựa trên danh sách kiểm tra chất lượng

## Quy tắc đầu ra (bắt buộc)

1. **Ngôn ngữ**: Tiếng Anh. Ngay cả khi người dùng gõ bằng tiếng Việt, hãy tạo tài liệu Use Case bằng tiếng Anh. Chỉ sử dụng tiếng Việt khi trò chuyện với người dùng về quy trình.
2. **Định dạng**: Markdown (`.md`). Sử dụng bố cục bảng 2 cột phản ánh bản mẫu gốc.
3. **Chế độ**: Tuần tự — tạo ra từng phần một, **dừng lại và đợi người dùng xác nhận** trước khi tiếp tục. Không bao giờ xuất toàn bộ Use Case trong một lần trừ khi người dùng yêu cầu rõ ràng "hãy đưa cho tôi toàn bộ Use Case cùng lúc".

---

## Quy trình làm việc: 4 Bước

```
Bước 1: PHÂN LOẠI ĐẦU VÀO  →  xác định người dùng đang ở chế độ nào
Bước 2: PHẠM VI USE CASE   →  áp dụng 4 quy tắc phạm vi + bài kiểm tra giờ nghỉ giải lao
Bước 3: VIẾT USE CASE      →  điền 13 trường TỪNG PHẦN MỘT
Bước 4: ĐÁNH GIÁ           →  chạy danh sách kiểm tra 20 điểm trước khi bàn giao
```

---

## Bước 1: Phân loại đầu vào và chọn chế độ

Trước khi viết bất cứ thứ gì, hãy xác định xem người dùng đang ở chế độ nào:

| Chế độ | Dấu hiệu | Hành động |
|--------|----------|-----------|
| **Chế độ A: Viết mới từ tính năng** | Người dùng dán mô tả tính năng, BRD, PRD, hoặc nói "viết UC cho tính năng X" | Chuyển đến Bước 2 (phạm vi) → Bước 3 (viết tuần tự) |
| **Chế độ B: Chia tính năng lớn thành danh sách UC** | Người dùng nói "chia thành danh sách UC", "tính năng này cần bao nhiêu UC", tải lên một PRD lớn | Đi sâu vào Bước 2 (áp dụng 3 kỹ thuật xác định), đầu ra là **Danh sách UC trước**, sau đó hỏi người dùng muốn viết chi tiết UC nào |
| **Chế độ C: Tinh chỉnh / review UC hiện có** | Người dùng dán một UC hiện có và hỏi "review cái này", "nó có đầy đủ không", "thiếu cái gì" | Bỏ qua Bước 2, đi thẳng tới Bước 4 (đánh giá theo danh sách) |
| **Chế độ D: Viết một phần cụ thể** | Người dùng nói "viết Normal Course cho UC này", "thêm Exceptions" | Đọc ngữ cảnh của UC, nhảy tới phần tương ứng của Bước 3 |

**Quy tắc vàng**: Nếu đầu vào không rõ ràng (chỉ một dòng), **HỎI trước khi viết** — không bao giờ bịa đặt. Hỏi tối đa 3 câu:
1. Ai là tác nhân chính (primary actor)? (vai trò cụ thể / lớp người dùng)
2. Mục tiêu cụ thể của tác nhân trong UC này là gì?
3. UC này thuộc về hệ thống / module nào?

Giao tiếp với người dùng bằng ngôn ngữ của họ (Tiếng Việt hoặc Tiếng Anh), nhưng tài liệu Use Case luôn luôn là Tiếng Anh.

---

## Bước 2: Xác định phạm vi của Use Case

Đây là phần **quan trọng nhất và dễ mắc lỗi nhất** khi viết UC. Đọc thật cẩn thận.

### 2.1. Bốn quy tắc phạm vi

**Quy tắc 1 - Bài kiểm tra giờ nghỉ giải lao (Coffee-break test - Alistair Cockburn)**
Sau khi hoàn thành UC, tác nhân có thể đi uống cà phê giải lao mà không cảm thấy công việc đang dang dở không? Nếu KHÔNG → UC này đang ở mức quá thấp (chức năng phụ/sub-function), hãy gộp nó lại. Nếu CÓ → phạm vi đã chuẩn (mức mục tiêu người dùng/user-goal level).

**Quy tắc 2 - Cấp độ mục tiêu (3 cấp độ của Cockburn)**
- **Mức tóm tắt (đám mây/cloud)**: UC kéo dài qua nhiều phiên (session). VD: "Quản lý vòng đời đăng ký khóa học" → quá cao, KHÔNG viết dưới dạng một UC đơn lẻ.
- **Mức mục tiêu người dùng (mặt biển/sea level)** ✅: 1 tác nhân, 1 phiên, đạt được 1 mục tiêu nghiệp vụ. VD: "Đăng ký một khóa học Digital School" → cấp độ đúng cho một UC.
- **Mức chức năng phụ (con cá/fish)**: Một bước nhỏ bên trong một UC khác. VD: "Xác thực mã OTP" → quá thấp, nên coi nó là phần Includes bên trong một UC khác.

**Quy tắc 3 - Một tác nhân, Một mục tiêu, Một phiên**
Mỗi UC phải CÓ CHÍNH XÁC: 1 tác nhân chính + 1 mục tiêu nghiệp vụ + hoàn thành trong 1 phiên liên tục. Nếu bạn thấy 2 mục tiêu khác nhau → tách thành 2 UC.

**Quy tắc 4 - Ranh giới hệ thống**
Một UC mô tả sự **tương tác** giữa tác nhân và hệ thống, KHÔNG phải chi tiết bên trong của hệ thống. Mỗi bước phải là một trong những điều sau:
- Tác nhân làm điều gì đó với hệ thống (đầu vào)
- Hệ thống phản hồi lại tác nhân (đầu ra)
Nếu một bước không có tác nhân cũng không có giao diện (UI) → đó là chi tiết thiết kế, không nằm trong phần mô tả của UC.

### 2.2. Ba kỹ thuật để xác định UC (dành cho Chế độ B)

Khi chia một tính năng lớn thành danh sách UC:

**Kỹ thuật 1: Dựa trên mục tiêu (từ trên xuống)**
Liệt kê tất cả các mục tiêu của từng tác nhân → mỗi mục tiêu = 1 UC tiềm năng.

**Kỹ thuật 2: Dựa trên sự kiện (trigger bên ngoài + bên trong)**
- Sự kiện bên ngoài: hành động của người dùng (click, gửi đi, đến giờ đã lên lịch)
- Sự kiện bên trong: do hệ thống kích hoạt (cron job, quy trình hàng loạt/batch process)
Mỗi sự kiện tạo ra một phản hồi của hệ thống → một UC tiềm năng.

**Kỹ thuật 3: Dựa trên CRUD (tập trung vào dữ liệu)**
Đối với mỗi thực thể nghiệp vụ (Học viên, Khóa học, Đăng ký, Chứng chỉ…), kiểm tra xem hệ thống có cần Create (Tạo mới) / Read (Đọc) / Update (Cập nhật) / Delete (Xóa) hay không. Mỗi hành động = 1 UC tiềm năng (có thể gộp R-U-D cho cùng một thực thể nếu logic tương tự nhau).

### 2.3. Đầu ra của Bước 2

**Chế độ A**: Một câu xác nhận phạm vi, sau đó YÊU CẦU NGƯỜI DÙNG XÁC NHẬN trước khi chuyển sang Bước 3:
> "Đã xác nhận phạm vi: UC này ở mức mục tiêu người dùng. Tác nhân chính: [X]. Mục tiêu: [Y]. Ranh giới hệ thống: [Z]. Bạn có xác nhận để tiếp tục sang Bước 3 không?"

**Chế độ B**: Một bảng Danh sách UC:
```
| Mã UC | Tên UC (động từ + danh từ)             | Tác nhân chính   | Mục tiêu | Mức ưu tiên |
| UC-01 | Đăng ký khóa học Digital School        | Học viên         | ...      | Cao         |
| UC-02 | Đặt lịch tư vấn 1-kèm-1                | Học viên         | ...      | Cao         |
| UC-03 | Phê duyệt hồ sơ KYC của học viên       | Người duyệt BO   | ...      | Trung bình  |
```
Sau đó hỏi: "Bạn muốn tôi viết chi tiết UC nào trước?"

---

## Bước 3: Viết Use Case — theo từng phần

**RẤT QUAN TRỌNG**: Chỉ tạo MỘT NHÓM PHẦN tại một thời điểm, sau đó **DỪNG LẠI và yêu cầu người dùng xác nhận** trước khi tiếp tục. Không đưa ra toàn bộ UC trong một lần.

Đọc `references/template-guide.md` để biết hướng dẫn chi tiết khi điền từng trường.
Đọc `references/writing-style.md` cho các quy ước viết (thể chủ động, đánh số, các lỗi cần tránh).

### 3.1. Template (cấu trúc đầu ra)

```markdown
| **Mã Use Case:**        | UC-XX-YY                                   |
| **Tên Use Case:**       | [Động từ hành động + danh từ]              |
| **Người tạo:**          |          | **Cập nhật lần cuối bởi:**|       |
| **Ngày tạo:**           |          | **Ngày cập nhật:**        |       |

| **Tác nhân (Actor):**         | [Tác nhân chính] / [Tác nhân phụ]          |
| **Mô tả (Description):**      | [2-3 câu: tại sao + làm gì + kết quả]      |
| **Tiền điều kiện:**     | 1. ... 2. ...                              |
| **Hậu điều kiện:**      | 1. ... 2. ...                              |
| **Mức ưu tiên:**        | Cao (High) / Trung bình (Medium) / Thấp (Low)|
| **Tần suất sử dụng:**   | [X lần / đơn vị thời gian]                 |
| **Luồng cơ bản:**       | 1. Tác nhân... 2. Hệ thống... 3. ...       |
| **Luồng thay thế:**     | UC-XX-YY.AC.1: [tên]                       |
| **Ngoại lệ (Exceptions):**| UC-XX-YY.EX.1: [tên]                       |
| **Bao gồm (Includes):** | UC-AA-BB                                   |
| **Yêu cầu đặc biệt:**   | [Phi chức năng: hiệu suất, bảo mật…]       |
| **Giả định (Assumptions):**| 1. ...                                     |
| **Ghi chú & Vấn đề:**   | TBD-1: [câu hỏi mở] / Người phụ trách / Hạn chót |
```

Template sẵn sàng để sao chép nằm ở `assets/uc-template.md`.

### 3.2. Quá trình tạo tuần tự — 5 nhóm phần

Tạo ra theo **đúng thứ tự này**, tạm dừng và hỏi để xác nhận sau mỗi nhóm:

> **Nhóm 1 — Định danh + Tác nhân + Mô tả**
> Đầu ra: Mã Use Case, Tên, Lịch sử (Người tạo / Ngày), Tác nhân, Mô tả.
> Sau đó nói: *"Nhóm 1 đã xong. Bạn có xác nhận để tiếp tục tới tiền điều kiện, hậu điều kiện, mức ưu tiên, tần suất không?"*

> **Nhóm 2 — Các điều kiện + Mức ưu tiên + Tần suất**
> Đầu ra: Tiền điều kiện (Preconditions), Hậu điều kiện (Postconditions), Mức ưu tiên (Priority), Tần suất sử dụng (Frequency of Use).
> Sau đó nói: *"Nhóm 2 đã xong. Bạn có xác nhận để tiếp tục tới Luồng cơ bản (Normal Course) không?"*

> **Nhóm 3 — Luồng cơ bản (Normal Course of Events)**
> Đầu ra: được đánh số, luồng thành công (happy path) theo từng bước.
> Sau đó nói: *"Luồng cơ bản đã xong. Bạn có xác nhận để tiếp tục tới Các luồng thay thế và Ngoại lệ không?"*

> **Nhóm 4 — Các luồng thay thế + Ngoại lệ**
> Đầu ra: AC.1, AC.2…, EX.1, EX.2…
> Sau đó nói: *"Nhóm 4 đã xong. Bạn có xác nhận để chuyển tới nhóm cuối cùng (Bao gồm, Yêu cầu đặc biệt, Giả định, Ghi chú) không?"*

> **Nhóm 5 — Bao gồm + Yêu cầu đặc biệt + Giả định + Ghi chú và Vấn đề**
> Đầu ra: các trường còn lại.
> Sau đó nói: *"Tất cả các phần đã hoàn tất. Tôi có nên chạy đánh giá chất lượng 20 điểm bây giờ không?"*

**Nếu người dùng yêu cầu thay đổi** ở một nhóm trước đó, hãy áp dụng và xác nhận lại trước khi tiếp tục.

**Nếu người dùng nói "bỏ qua" (skip ahead)** hoặc "đưa cho tôi tất cả một lúc", hãy thực hiện — nhưng cảnh báo ngắn gọn rằng chế độ tuần tự sẽ giúp phát hiện lỗi tốt hơn.

### 3.3. Các quy tắc điền trường RẤT QUAN TRỌNG (những lỗi phổ biến nhất)

**Mã Use Case**: Định dạng `UC-<module>-<seq>`, ví dụ: `UC-LEARN-01`. Dùng cấu trúc phân cấp X.Y nếu bạn có các nhóm UC.

**Tên Use Case**: PHẢI là "**Động từ + Tân ngữ**" (thể chủ động).
- ✅ "Đăng ký khóa học Digital School", "Đặt lịch tư vấn", "Cấp chứng chỉ hoàn thành khóa học"
- ❌ "Sự đăng ký" (không có động từ), "Học viên đăng ký" (bao gồm tên tác nhân), "Quản lý khóa học" (động từ quá chung chung)

**Tác nhân**: Phân biệt:
- *Tác nhân chính (Primary actor)*: khởi xướng UC, được hưởng lợi từ kết quả.
- *Tác nhân phụ (Secondary actor)*: hệ thống/người hỗ trợ (cổng thanh toán, dịch vụ OTP, LMS).
Không bao giờ viết "Người dùng" (User) — hãy thật cụ thể (Học viên, Cố vấn, Quản trị viên BO, Quản lý Nhân sự, Đối tác Doanh nghiệp…).

**Tiền điều kiện**: Các điều kiện **PHẢI đúng** trước khi UC bắt đầu. Phân biệt với các quy tắc nghiệp vụ (business rules)!
- ✅ "Học viên đã đăng nhập và có gói đăng ký Digital School còn hiệu lực"
- ❌ "Học viên có động lực để học tập" (động lực — không thể xác minh được)

**Hậu điều kiện**: Trạng thái hệ thống **SAU KHI** UC hoàn tất thành công. Phải có thể xác minh được.
- ✅ "Bản ghi đăng ký được lưu với trạng thái='Hoạt động'; học viên được quyền truy cập vào toàn bộ tài liệu khóa học"
- ❌ "Học viên cảm thấy hài lòng" (không thể xác minh)

**Luồng cơ bản** (phần quan trọng nhất):
- Danh sách được đánh số, một hành động cho mỗi bước.
- Luân phiên giữa các bước của Tác nhân / Hệ thống (chủ ngữ phải rõ ràng).
- Mỗi bước bắt đầu bằng một chủ ngữ rõ ràng + động từ chủ động.
- **KHÔNG lồng ghép if/else, vòng lặp, hoặc ngoại lệ** — những cái đó thuộc về phần Luồng thay thế/Ngoại lệ.
- Phong cách kể chuyện: từ yếu tố kích hoạt (trigger) tới lúc đạt được mục tiêu.
- ✅ "1. Học viên chọn khóa học trên danh mục Digital School.  2. Hệ thống hiển thị chi tiết khóa học và tùy chọn đăng ký.  3. Học viên click vào 'Đăng ký ngay'."
- ❌ "1. Nếu học viên có voucher, nhập mã; nếu không tiếp tục tới phần thanh toán…" (phân nhánh lồng ghép)

**Luồng thay thế**: Các nhánh khác nhau **nhưng vẫn dẫn tới thành công**. VD: thanh toán bằng voucher doanh nghiệp thay vì ví cá nhân. Định dạng `UC-XX.AC.N` + "Tại bước Y của Luồng cơ bản, nếu [điều kiện], thực hiện nhánh thay thế: …"

**Ngoại lệ**: Các trường hợp mà **mục tiêu thất bại** (lỗi, xác thực thất bại, hết thời gian chờ (timeout)). Định dạng `UC-XX.EX.N`. Mỗi ngoại lệ cần có: điều kiện kích hoạt + phản hồi của hệ thống + trạng thái cuối cùng.

**Bao gồm (Includes)**: Danh sách các UC con được "gọi" bởi UC này (chức năng dùng chung). VD: UC "Đăng ký khóa học" bao gồm (includes) UC "Xử lý thanh toán".

**Yêu cầu đặc biệt**: Các yêu cầu phi chức năng cụ thể riêng cho UC này:
- Hiệu suất: "Trang danh mục khóa học tải ≤ 2s cho 5.000 học viên truy cập đồng thời"
- Bảo mật: "Dữ liệu thanh toán phải được mã hóa khi truyền tải (TLS 1.3)"
- Tính khả dụng, Tính tin cậy, Tính tuân thủ…

**Giả định**: Những điều được mặc định/giả định trong quá trình phân tích. Khác với Tiền điều kiện — tiền điều kiện là một yêu cầu bắt buộc; còn giả định là một niềm tin chưa được xác minh.

**Ghi chú và Vấn đề**: Danh sách những việc cần quyết định (TBD) với định dạng `[TBD-N] | Người phụ trách | Hạn chót | Giải pháp`.

---

## Bước 4: Đánh giá theo danh sách 20 điểm

**LUÔN LUÔN chạy danh sách kiểm tra này TRƯỚC KHI bàn giao UC.** Nếu bất kỳ mục nào thất bại (fail), hãy sửa lại hoặc báo cho người dùng.

Đọc `references/quality-checklist.md` để xem toàn bộ danh sách kiểm tra cùng với các ví dụ. 20 mục này, được phân nhóm như sau:

### Phạm vi & Nhận diện (5 mục)
- [ ] **C1**: Tên UC theo cấu trúc "động từ + tân ngữ", thể chủ động
- [ ] **C2**: UC nằm ở mức mục tiêu người dùng (vượt qua bài kiểm tra giờ nghỉ giải lao)
- [ ] **C3**: Mã UC là duy nhất và tuân theo quy ước đặt tên
- [ ] **C4**: Có chính xác 1 tác nhân chính + 1 mục tiêu nghiệp vụ rõ ràng
- [ ] **C5**: Ranh giới hệ thống rõ ràng (không bị trộn lẫn với các UC khác)

### Tác nhân & Ngữ cảnh (3 mục)
- [ ] **C6**: Tác nhân là một vai trò/lớp cụ thể, không dùng "Người dùng" (User)
- [ ] **C7**: Mô tả trả lời câu hỏi TẠI SAO (lý do) + LÀM GÌ (hành động) + KẾT QUẢ
- [ ] **C8**: Tần suất sử dụng được định lượng (không dùng "thỉnh thoảng")

### Tiền/Hậu Điều kiện (3 mục)
- [ ] **C9**: Tiền điều kiện có thể xác minh được (không phải là quy tắc nghiệp vụ bị ngụy trang)
- [ ] **C10**: Hậu điều kiện bao gồm cả trạng thái thành công và mọi sự thay đổi của hệ thống
- [ ] **C11**: Tiền điều kiện không bị nhầm lẫn với các Giả định

### Luồng cơ bản (4 mục)
- [ ] **C12**: Danh sách được đánh số, một hành động cho mỗi bước
- [ ] **C13**: Luân phiên giữa Tác nhân / Hệ thống với các chủ ngữ rõ ràng
- [ ] **C14**: KHÔNG CÓ lồng ghép if/else/vòng lặp trong Luồng cơ bản
- [ ] **C15**: Luồng chạy từ lúc kích hoạt (trigger) cho tới hậu điều kiện (không có bước nào lơ lửng)

### Thay thế & Ngoại lệ (3 mục)
- [ ] **C16**: Mỗi luồng thay thế (AC) chỉ định rõ "tại bước N" + điều kiện
- [ ] **C17**: Mỗi Ngoại lệ (Exception) có điều kiện kích hoạt + phản hồi của hệ thống + trạng thái cuối cùng
- [ ] **C18**: Các chế độ lỗi thường gặp đều được bao phủ (hết thời gian chờ, đầu vào không hợp lệ, mạng, từ chối quyền, xung đột đồng thời)

### Tính đầy đủ (2 mục)
- [ ] **C19**: Các mục Includes (nếu có) phải trỏ đến các UC đã tồn tại
- [ ] **C20**: Các Yêu cầu đặc biệt không được lặp lại các yêu cầu chức năng

**Đầu ra khi đánh giá**: Một bảng `Mục | Trạng thái | Ghi chú` sử dụng các biểu tượng ✅ ❌ ⚠️.

---

## Chi tiết định dạng đầu ra

- Luôn sản xuất tài liệu Markdown bằng tiếng Anh
- Sử dụng bố cục bảng 2 cột giống với template gốc
- Lưu đầu ra cuối cùng dưới dạng file `.md` nếu người dùng muốn một file có thể tải xuống; nếu không hãy hiển thị trực tiếp trên đoạn chat
- Quy ước đặt tên file: `<Mã-UC>_<Tên-UC-kebab>.md`, ví dụ: `UC-LEARN-01_enroll-digital-school-course.md`

---

## Tài liệu tham khảo

- `references/template-guide.md` - Hướng dẫn chi tiết cho từng trường (kèm các ví dụ trong lĩnh vực EdTech & Digital School)
- `references/writing-style.md` - Quy ước cách viết (thể chủ động, đánh số, các lỗi nên tránh)
- `references/quality-checklist.md` - Danh sách kiểm tra 20 điểm kèm ví dụ đỗ/trượt (pass/fail)
- `references/examples-edtech.md` - 2 ví dụ UC hoàn chỉnh về EdTech (Đăng ký khóa học, Duyệt phiên hẹn cố vấn)
- `assets/uc-template.md` - Template Markdown sẵn sàng sao chép

---

## Các lỗi nên tránh (Tuyệt đối không làm)

1. **UC = Luồng UI**: Mô tả từng cú click chuột hay popup → đó là đặc tả wireframe, không phải UC.
2. **UC = User Story**: Một UC mô tả chi tiết các tương tác; còn User Story (US) là câu nói gọn trong 1 dòng "Là một… Tôi muốn… Để…".
3. **UC = Quy trình nghiệp vụ**: Quy trình nghiệp vụ (BP) bao hàm toàn bộ quy trình doanh nghiệp (nhiều người, nhiều hệ thống); còn một UC chỉ dành cho 1 tác nhân + 1 hệ thống.
4. **Các động từ chung chung trong Tên UC**: "Quản lý" (Manage), "Xử lý" (Handle), "Tiến hành" (Process) — quá chung chung. Hãy dùng các động từ hành động cụ thể.
5. **Nhồi nhét quá nhiều**: Nhồi nhét cả việc đăng ký, thanh toán, gửi thông báo vào một UC khổng lồ → hãy tách ra và dùng thẻ Includes.
6. **Quên mất ngoại lệ**: Chỉ viết luồng thành công mà không có trường hợp gặp lỗi → không đủ cho dev/QA làm việc.
7. **Tiền điều kiện chung chung**: "Hệ thống đã sẵn sàng" → vô nghĩa. Phải là những điều kiện có thể xác minh được.

---
*Kỹ năng được phát triển bởi **Phúc NT** · BA Zone · Digital School*  
*Vui lòng giữ nguyên thông tin ghi công khi chia sẻ hoặc phân nhánh repo này.*
