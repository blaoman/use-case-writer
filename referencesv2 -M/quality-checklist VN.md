# Danh sách Kiểm tra Chất lượng (Quality Checklist) — 20 Điểm để Đánh giá một Use Case

Hãy chạy danh sách kiểm tra này TRƯỚC KHI bàn giao một UC. Mỗi mục bao gồm: định nghĩa, cách kiểm tra, và các ví dụ đỗ/trượt (pass/fail).

> Tổng hợp bởi **Phúc NT** · BA Zone · Digital School

## Cách sử dụng

1. Sau khi viết xong UC, hãy duyệt qua các mục từ C1 đến C20
2. Đánh dấu Trạng thái: ✅ Đạt (Pass) / ❌ Không đạt (Fail) / ⚠️ Cần xem xét lại (Needs review)
3. Nếu Không đạt → hãy sửa nó hoặc đánh dấu báo lại cho người dùng
4. Xuất ra một bảng tóm tắt ở cuối

```
| Mục | Trạng thái | Ghi chú |
| C1  | ✅         | Tên UC "Đăng ký khóa học Digital School" đúng định dạng |
| C2  | ⚠️         | UC có thể được chia nhỏ thêm — cần xác nhận với PO |
| ... | ...        | ... |
```

---

## NHÓM A: Phạm vi & Nhận diện (C1-C5)

### C1. Tên UC theo cấu trúc "động từ + tân ngữ", thể chủ động
**Định nghĩa**: Tên UC bắt đầu bằng một động từ hành động + một danh từ làm tân ngữ, không bao gồm tên tác nhân.

**Cách kiểm tra**: Phân tích Tên UC → xác định động từ đứng đầu → kiểm tra xem đó có phải là động từ hành động hay không.

**Đạt (Pass)**: "Đăng ký khóa học Digital School", "Phê duyệt yêu cầu buổi hẹn cố vấn", "Cấp chứng chỉ hoàn thành"
**Không đạt (Fail)**: "Sự đăng ký" (không có động từ), "Học viên đặt lịch hẹn" (bao gồm tác nhân), "Quản lý khóa học" (động từ chung chung)

---

### C2. UC nằm ở mức mục tiêu người dùng (vượt qua bài kiểm tra giờ nghỉ giải lao)
**Định nghĩa**: Sau khi hoàn thành UC, tác nhân có thể dừng lại và đi nghỉ giải lao — mục tiêu đã đạt được.

**Cách kiểm tra**: Đọc phần Hậu điều kiện (Postconditions) → tự hỏi "Đây có phải là một kết quả có ý nghĩa về mặt nghiệp vụ không?"
- Nếu kết quả chỉ là một bước phụ (VD: "OTP được xác thực") → UC quá nhỏ
- Nếu kết quả kéo dài qua nhiều phiên làm việc → UC quá lớn

**Đạt (Pass)**:
- "Đăng ký khóa học Digital School" → hậu điều kiện: bản ghi đăng ký đang hoạt động, học viên có quyền truy cập khóa học
- "Đặt lịch hẹn cố vấn" → hậu điều kiện: yêu cầu đặt lịch đã được gửi, cố vấn nhận được thông báo

**Không đạt (Fail)**:
- "Xác thực OTP" (quá nhỏ — chỉ là một bước phụ của một UC khác) → nên là một mục Includes
- "Quản lý toàn bộ vòng đời học viên" (quá lớn — kéo dài nhiều phiên) → cần chia thành nhiều UC nhỏ

---

### C3. Mã UC là duy nhất và tuân theo quy ước đặt tên
**Định nghĩa**: Mã (ID) là duy nhất trong dự án và khớp với định dạng chuẩn.

**Cách kiểm tra**:
- Kiểm tra danh sách UC tổng (master UC list) — mã ID có duy nhất không?
- Định dạng có khớp với `UC-<module>-<seq>` không?

**Đạt (Pass)**: "UC-LEARN-01" (duy nhất, đúng định dạng), "UC-MENTOR-03"
**Không đạt (Fail)**: "UC1" (không có module), "UseCase_CourseEnroll" (bị gắn cả tên vào mã)

---

### C4. Có chính xác 1 tác nhân chính + mục tiêu nghiệp vụ rõ ràng
**Định nghĩa**: Một UC có 1 tác nhân chính (người khởi xướng) và 1 mục tiêu cụ thể.

**Cách kiểm tra**:
- Trường Tác nhân (Actor) → có ghi rõ "Tác nhân chính: [X]" không?
- Phần Mô tả (Description) → có nêu rõ mục tiêu không?
- Nếu bạn thấy có 2 tác nhân chính → đánh dấu để tách UC

**Đạt (Pass)**: Tác nhân chính: Học viên. Mục tiêu: đăng ký một khóa học Digital School và có ngay quyền truy cập vào tài liệu.
**Không đạt (Fail)**: Tác nhân chính: Học viên + Quản lý Nhân sự (2 tác nhân). → Chia tách: "Học viên tự đăng ký" và "Quản lý Nhân sự chỉ định khóa học cho nhân viên" thành 2 UC.

---

### C5. Ranh giới hệ thống rõ ràng
**Định nghĩa**: UC mô tả sự tương tác với một hệ thống cụ thể, không trộn lẫn nhiều hệ thống với nhau.

**Cách kiểm tra**: Đọc Luồng cơ bản (Normal Course) → các bước "Hệ thống..." có nhất quán chỉ về một hệ thống không?

**Đạt (Pass)**: Tất cả các bước đều đề cập tới "BA Zone Platform". LMS và Cổng thanh toán (Payment Gateway) đóng vai trò là các tác nhân phụ.
**Không đạt (Fail)**: Lẫn lộn giữa web platform BA Zone + mobile app + API của LMS bên thứ ba như thể chúng là một hệ thống duy nhất. → Hãy chia theo ranh giới hệ thống hoặc làm rõ hệ thống chính.

---

## NHÓM B: Tác nhân & Ngữ cảnh (C6-C8)

### C6. Tác nhân là một vai trò/lớp cụ thể
**Cách kiểm tra**: Tác nhân có phải là một vai trò/lớp cụ thể thay vì chỉ là "Người dùng" (User) không?

**Đạt (Pass)**: "Học viên (người đăng ký gói Digital School Premium)", "Cố vấn (được cấp chứng chỉ BA Zone, tài khoản đang hoạt động)"
**Không đạt (Fail)**: "Người dùng" (User), "Người" (Person), "Actor 1"

---

### C7. Mô tả trả lời câu hỏi TẠI SAO + LÀM GÌ + KẾT QUẢ (WHY + WHAT + OUTCOME)
**Cách kiểm tra**: Đọc phần Mô tả (Description) → kiểm tra xem có mặt đủ cả 3 yếu tố này không.

**Đạt (Pass)**:
"Khi học viên hoàn thành tất cả các bài học và vượt qua bài kiểm tra cuối khóa [TẠI SAO], học viên điều hướng đến mục Chứng chỉ để yêu cầu cấp chứng chỉ hoàn thành [LÀM GÌ]. UC kết thúc khi một file PDF chứng chỉ cá nhân hóa được tạo ra với một mã xác minh duy nhất và được gửi email cho học viên [KẾT QUẢ]."

**Không đạt (Fail)**: "UC này nói về việc cấp phát chứng chỉ." (thiếu TẠI SAO và KẾT QUẢ)

---

### C8. Tần suất sử dụng được định lượng
**Cách kiểm tra**: Trường Tần suất (Frequency) có chứa một CON SỐ cụ thể không?

**Đạt (Pass)**: "~500 lượt đăng ký/ngày trên toàn nền tảng; đỉnh điểm ~100 lượt/giờ trong các chiến dịch khuyến mãi"
**Không đạt (Fail)**: "Thường xuyên", "Hay xảy ra khi ra mắt khóa học" (không có số lượng)

⚠️ Có thể chấp nhận: "TBD — đang đợi dữ liệu phân tích từ đội ngũ vận hành" + ghi chú lại trong phần Notes dưới dạng [TBD-N]

---

## NHÓM C: Tiền/Hậu Điều kiện (C9-C11)

### C9. Tiền điều kiện có thể xác minh được
**Cách kiểm tra**: Mỗi tiền điều kiện có thể được kiểm chứng bằng một truy vấn (query) / bài test đúng sai (boolean) không?

**Đạt (Pass)**: "Học viên đã hoàn thành 100% các bài học (tiến độ = 100%)" (truy vấn DB), "Cổng thanh toán đang sẵn sàng" (health check)
**Không đạt (Fail)**: "Học viên có động lực học tập" (động lực — không xác minh được), "Hệ thống đã sẵn sàng" (quá chung chung)

---

### C10. Hậu điều kiện bao gồm cả trạng thái thành công + mọi thay đổi
**Cách kiểm tra**: Hậu điều kiện có mô tả toàn bộ sự thay đổi sau khi UC chạy xong không?
- Thay đổi dữ liệu (những bản ghi nào, trường dữ liệu nào)
- Trạng thái bên ngoài (gửi thông báo, khóa lịch, tạo file)
- Trạng thái người dùng thấy được (màn hình mới, mở khóa huy hiệu)

**Đạt (Pass)**:
```
1. Bản ghi đăng ký được tạo với trạng thái='Đang hoạt động'
2. Học viên được cấp quyền truy cập vào tất cả bài học đã xuất bản
3. Giao dịch thanh toán được lưu với trạng thái='Đã hoàn thành'
4. Email chào mừng + thông báo trong ứng dụng được gửi trong vòng 60s
5. Lượt đăng ký khóa học tăng thêm 1
```

**Không đạt (Fail)**: Chỉ ghi "Đăng ký thành công" → thiếu toàn bộ chi tiết về trạng thái.

---

### C11. Tiền điều kiện không bị nhầm lẫn với Giả định (Assumptions)
**Cách kiểm tra**: Phân biệt:
- Tiền điều kiện: BẮT BUỘC ĐÚNG, hệ thống có thể kiểm tra
- Giả định: ĐƯỢC TIN là đúng, không kiểm tra được

**Lỗi thường gặp ở Digital School**: Đưa "Học viên có kiến thức tin học căn bản" vào Tiền điều kiện → SAI, đây là một Giả định. Hệ thống không thể kiểm tra điều này.

---

## NHÓM D: Luồng cơ bản (C12-C15)

### C12. Danh sách đánh số, một hành động cho mỗi bước
**Cách kiểm tra**: Có phải mỗi bước đều:
- Bắt đầu bằng một con số (1., 2., 3...)
- Chứa duy nhất một hành động chính
- Tránh dùng từ "và" để nối 2 hành động khác loại

**Đạt (Pass)**: "3. Học viên nhập chủ đề buổi hẹn, ngày mong muốn, và khung giờ." (cùng loại — trường nhập liệu)
**Không đạt (Fail)**: "3. Học viên nhập chủ đề và click Gửi và đợi phản hồi." (3 hành động trong một bước)

---

### C13. Luân phiên giữa Tác nhân / Hệ thống với các chủ ngữ rõ ràng
**Cách kiểm tra**: Đọc các bước — có sự luân phiên xen kẽ (pattern) giữa Tác nhân/Hệ thống không?

**Đạt (Pass)**:
```
1. Học viên click Đăng ký ngay                   ← Tác nhân
2. Hệ thống hiển thị Tóm tắt Đơn hàng            ← Hệ thống
3. Học viên chọn phương thức thanh toán          ← Tác nhân
4. Học viên click Tiếp tục Thanh toán            ← Tác nhân
5. Hệ thống gọi Cổng thanh toán                  ← Hệ thống
```
(Chấp nhận 2 bước liên tiếp của Tác nhân khi cả hai đều là việc nhập liệu — vẫn rõ ràng)

**Không đạt (Fail)**: Chỉ có "Học viên làm X, sau đó làm Y, sau đó làm Z" mà không thấy hệ thống phản hồi ở đâu cả.

---

### C14. KHÔNG CÓ lồng ghép if/else/vòng lặp trong Luồng cơ bản
**Cách kiểm tra**: Tìm trong Luồng cơ bản các từ "nếu" (if), "trong trường hợp" (in case), "nếu không thì" (otherwise) → đánh dấu lỗi.

**Đạt (Pass)**:
```
5. Hệ thống kiểm tra hạn mức số buổi hẹn còn lại của học viên.
6. Hệ thống tạo yêu cầu buổi hẹn với trạng thái='Chờ_Cố_Vấn_Duyệt'.
```

**Không đạt (Fail)**:
```
5. Nếu học viên có gói Premium, hệ thống hiển thị toàn bộ cố vấn; nếu gói Free, hệ thống chỉ hiển thị cố vấn miễn phí; nếu hạn mức bằng 0, hệ thống chặn hành động.
```
→ Chia nhỏ thành: Luồng cơ bản (luồng mặc định Premium) + AC (gói Free) + Ngoại lệ (hết hạn mức).

---

### C15. Luồng chạy từ lúc kích hoạt cho tới hậu điều kiện
**Cách kiểm tra**:
- Bước 1 có khớp với yếu tố kích hoạt (trigger) trong phần Mô tả không?
- Bước cuối cùng có đạt được Hậu điều kiện không?
- Có bước nào đang bị "lơ lửng" không?

**Đạt (Pass)**: Bước 1 "Học viên click Đăng ký ngay" (yếu tố kích hoạt) → bước 9 "Hệ thống gửi thông báo chào mừng" (đạt được hậu điều kiện).
**Không đạt (Fail)**: Bước cuối cùng là "Hệ thống lưu thông tin đăng ký" nhưng hậu điều kiện lại nói "Thông báo chào mừng được gửi" → luồng đang không hoàn chỉnh.

---

## NHÓM E: Thay thế & Ngoại lệ (C16-C18)

### C16. Mỗi luồng thay thế (AC) có chỉ định rõ "tại bước N" + điều kiện
**Cách kiểm tra**: Mỗi Luồng thay thế có đáp ứng:
- Mã định dạng `UC-XX.AC.N`
- Câu mở đầu: "Tại bước Y của Luồng cơ bản, nếu [điều kiện]..."
- Các bước phụ đánh số 5a, 5b...
- Câu kết thúc: "tiếp tục từ bước Z của Luồng cơ bản"

**Đạt (Pass)**:
```
UC-LEARN-01.AC.1: Đăng ký bằng voucher doanh nghiệp
Tại bước 5 của Luồng cơ bản, nếu học viên chọn Voucher Doanh nghiệp:
5a. Hệ thống hiển thị trường nhập mã voucher.
5b. Học viên nhập mã và click Áp dụng.
5c. Hệ thống xác thực voucher → tiếp tục từ bước 7 của Luồng cơ bản.
```

**Không đạt (Fail)**:
```
AC1: Nếu học viên có voucher, họ có thể dùng nó thay vì thanh toán.
```
(Quá chung chung, không tham chiếu bước gốc, không có bước phụ, không có hướng dẫn quay lại luồng chính)

---

### C17. Mỗi Ngoại lệ có điều kiện kích hoạt + phản hồi + trạng thái cuối cùng
**Cách kiểm tra**: Mỗi ngoại lệ có đủ 3 phần không?

**Đạt (Pass)**:
```
UC-LEARN-01.EX.2: Khóa học kín chỗ giữa chừng
Kích hoạt: Tại bước 7, LMS trả về lỗi CAPACITY_EXCEEDED (VƯỢT_QUÁ_SỨC_CHỨA).
Phản hồi: Hệ thống hiển thị "Khóa học này vừa hết chỗ. Hãy tham gia danh sách chờ."
Trạng thái cuối cùng: Hoàn tiền trong vòng 1 ngày làm việc. Không tạo bản ghi đăng ký. Hiển thị đề xuất vào danh sách chờ.
```

**Không đạt (Fail)**:
```
EX1: Nếu có lỗi xảy ra, hệ thống hiển thị thông báo lỗi.
```
(Chung chung — không có điều kiện kích hoạt, không mô tả phản hồi chi tiết, không rõ trạng thái cuối cùng)

---

### C18. Các chế độ lỗi thường gặp đều được bao phủ
**Cách kiểm tra**: UC có bao hàm tối thiểu các loại lỗi phổ biến có liên quan trong Digital School không?

| Loại lỗi | Bắt buộc cho UC của Digital School? |
|---|---|
| Lỗi xác thực dữ liệu (đầu vào không hợp lệ) | ✅ |
| Vi phạm quy tắc nghiệp vụ (hết hạn mức, khóa học đầy chỗ) | ✅ |
| Dịch vụ bên ngoài lỗi (cổng thanh toán, LMS, lịch hết hạn) | ✅ |
| Lỗi xác thực/phân quyền người dùng | ✅ nếu UC có yêu cầu đăng nhập |
| Vấn đề kết nối mạng | ✅ cho các luồng trên mobile app |
| Xung đột đồng thời (hai người tranh một suất cuối) | ✅ cho các UC đăng ký/đặt lịch |
| Hết thời gian chờ (mentor mở trang chi tiết quá lâu) | ✅ cho các UC duyệt hồ sơ/đánh giá |

**Mẹo**: Nếu UC chỉ có 1-2 Ngoại lệ → cần xem xét lại. Các UC đăng ký hay đặt lịch thường cần tới 3-5 Ngoại lệ.

---

## NHÓM F: Tính đầy đủ (C19-C20)

### C19. Các mục Includes (nếu có) phải trỏ đến các UC đã tồn tại
**Cách kiểm tra**: Mỗi UC trong trường Includes có Mã ID hợp lệ + UC đó có thực sự tồn tại không?

**Đạt (Pass)**: "Includes: UC-PAY-01 (Xử lý thanh toán)" → UC-PAY-01 đã được viết và có mặt trong danh sách UC dự án.
**Không đạt (Fail)**: "Includes: UC Thanh toán" → ID không cụ thể, hoặc UC được tham chiếu chưa tồn tại.

---

### C20. Các Yêu cầu đặc biệt không được lặp lại các yêu cầu chức năng
**Cách kiểm tra**: Mỗi mục trong Yêu cầu đặc biệt (Special Requirements) có thực sự là yêu cầu phi chức năng không?

**Đạt (Pass)** (phi chức năng):
- "Danh mục khóa học tải ≤ 2s với 5.000 người dùng truy cập đồng thời"
- "Lịch sử hệ thống (audit log) được lưu trữ trong 3 năm"
- "Tuân thủ các quy định về xuất hóa đơn VAT của Việt Nam"

**Không đạt (Fail)** (chức năng — thuộc về Luồng cơ bản / Quy tắc nghiệp vụ):
- "Kiểm tra mã voucher phải có 16 ký tự" → đây là logic xác thực, thuộc về một bước trong Luồng cơ bản hoặc BR
- "Học viên chỉ có thể đăng ký 10 khóa học mỗi tháng" → đây là quy tắc nghiệp vụ, không phải Yêu cầu đặc biệt

---

## Báo cáo Kiểm tra (Validation Report)

Sau khi kiểm tra toàn bộ 20 mục, xuất báo cáo theo định dạng sau:

```markdown
## Kết quả Đánh giá cho UC-LEARN-01

| # | Mục | Trạng thái | Ghi chú |
|---|------|--------|------|
| C1 | Tên UC đúng định dạng | ✅ | "Đăng ký khóa học Digital School" — động từ + tân ngữ |
| C2 | Mức mục tiêu người dùng | ✅ | Vượt qua bài kiểm tra giờ nghỉ giải lao |
| C3 | Mã UC duy nhất | ✅ | Tuân thủ quy ước |
| C4 | 1 tác nhân chính | ✅ | Học viên |
| C5 | Ranh giới hệ thống | ✅ | BA Zone Platform |
| C6 | Tác nhân cụ thể | ✅ | |
| C7 | Mô tả có TẠI SAO+LÀM GÌ+KẾT QUẢ | ✅ | |
| C8 | Tần suất được định lượng | ⚠️ | TBD — đợi dữ liệu phân tích từ đội vận hành |
| C9 | Tiền điều kiện có thể xác minh | ✅ | 4/4 có thể xác minh |
| C10 | Hậu điều kiện bao phủ trạng thái| ✅ | 5 hậu điều kiện |
| C11 | Không nhầm Tiền/Giả định | ✅ | |
| C12 | Đánh số, 1 hành động/bước | ✅ | 9 bước |
| C13 | Tác nhân/Hệ thống xen kẽ | ✅ | |
| C14 | Không lồng if/else | ✅ | |
| C15 | Luồng hoàn chỉnh | ✅ | |
| C16 | AC có chỉ định "tại bước N" | ✅ | 2 AC, đều được gắn chính xác |
| C17 | Ngoại lệ có đủ 3 phần | ✅ | 4 ngoại lệ, đều hoàn chỉnh |
| C18 | Bao phủ các lỗi thường gặp | ✅ | Lỗi thanh toán, đầy chỗ, LMS lỗi — đều có |
| C19 | Includes hợp lệ | ✅ | UC-PAY-01, UC-NOTI-01 |
| C20 | Req Đặc biệt là phi chức năng | ✅ | |

**Tóm tắt**: 19/20 ✅ + 1 ⚠️. UC đã sẵn sàng để các bên liên quan review.
**Việc cần làm tiếp**: C8 — Tần suất sử dụng chờ dữ liệu từ đội vận hành [TBD-3].
```

---
*Tổng hợp bởi **Phúc NT** · BA Zone · Digital School*  
*Vui lòng ghi nguồn khi chia sẻ hoặc điều chỉnh danh sách kiểm tra này.*
