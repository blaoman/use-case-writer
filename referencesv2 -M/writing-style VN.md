# Hướng dẫn Phong cách Viết (Writing Style Guide)

Được tổng hợp từ tài liệu của Alistair Cockburn ("Writing Effective Use Cases") + IIBA BABOK + thực tiễn của BA Zone trong lĩnh vực EdTech và phần mềm doanh nghiệp.

> Tổng hợp bởi **Phúc NT** · BA Zone · Digital School

## Nguyên tắc tối thượng: TÍNH DỄ ĐỌC LÀ ƯU TIÊN HÀNG ĐẦU

Trích dẫn nổi tiếng của Cockburn: "Hãy viết rõ ràng. Tính dễ đọc là điều quan trọng nhất."

Một UC tốt là khi:
- Các bên liên quan không chuyên về kỹ thuật cũng có thể nắm bắt được ý nghĩa
- Đội ngũ lập trình viên (Developer) có đủ thông tin để viết code
- Đội ngũ kiểm thử (QA) có đủ thông tin để viết test case
- Một BA mới (hoặc học viên tốt nghiệp Digital School sau này) có thể cập nhật nó khi có sự thay đổi

---

## Quy tắc 1: Thể chủ động + Thì hiện tại

### Thể chủ động
Sử dụng các câu chủ động nơi chủ ngữ thực hiện hành động.

- ✅ "Học viên click vào nút **Đăng ký ngay**"
- ❌ "Nút **Đăng ký ngay** được click bởi học viên"

- ✅ "Hệ thống lưu bản ghi đăng ký vào cơ sở dữ liệu"
- ❌ "Bản ghi đăng ký được lưu vào cơ sở dữ liệu bởi hệ thống"

### Thì hiện tại
Sử dụng thì hiện tại đơn, tránh thì tương lai/quá khứ.

- ✅ "Hệ thống hiển thị màn hình xác nhận khóa học"
- ❌ "Hệ thống sẽ hiển thị màn hình xác nhận khóa học"
- ❌ "Hệ thống đã hiển thị màn hình xác nhận khóa học"

---

## Quy tắc 2: Chủ ngữ rõ ràng — Chủ ngữ + Động từ + Tân ngữ

Mỗi bước phải bắt đầu bằng một **chủ ngữ cụ thể**: tên của một tác nhân hoặc "Hệ thống".

- ✅ "Học viên chọn một khung giờ hẹn với cố vấn (mentor session slot) mong muốn"
- ❌ "Chọn một khung giờ hẹn mong muốn" (không có chủ ngữ)

- ✅ "Hệ thống kiểm tra hạn mức số buổi hẹn còn lại của học viên"
- ❌ "Kiểm tra hạn mức còn lại" (bị động, không rõ ai đang thực hiện)

---

## Quy tắc 3: Một bước = một hành động

Mỗi bước trong Luồng cơ bản (Normal Course) chỉ thực hiện chính xác một việc. Nếu bạn thấy từ "và" kết nối các loại hành động khác nhau → hãy chia tách bước đó ra.

- ✅ "3. Học viên nhập tài khoản đích, khung giờ mong muốn, và chủ đề buổi hẹn." (cùng một loại hành động — điền form)
- ❌ "3. Học viên điền chủ đề buổi hẹn và click Xác nhận." → chia thành 2 bước:
  - "3. Học viên nhập chủ đề buổi hẹn (tối đa 500 ký tự)."
  - "4. Học viên click vào nút **Gửi yêu cầu**."

**Lý do**: Hành động "Click Gửi yêu cầu" thường sẽ kích hoạt sự kiểm tra từ hệ thống → nó cần phải là một bước tách biệt để một Ngoại lệ (Exception) như "vượt quá hạn mức" có thể được gắn vào nó.

---

## Quy tắc 4: Tránh các động từ chung chung

Các động từ chung chung = các động từ không truyền tải một hành động cụ thể.

| ❌ Chung chung | ✅ Cụ thể |
|--------------|-----------|
| Quản lý (Manage) | Tạo mới (Create) / Cập nhật (Update) / Lưu trữ (Archive) / Xem (View) |
| Xử lý (Handle) | Xác thực (Validate) / Tiến hành (Process) / Từ chối (Reject) / Nâng cấp (Escalate) |
| Làm (Do) | Gửi (Submit) / Phê duyệt (Approve) / Giao việc (Assign) / Khởi tạo (Generate) |
| Tạo ra (Make) | Cấp phát (Issue) / Xây dựng (Build) / Hiển thị (Render) / Tính toán (Compute) |
| Lấy (Get) | Lấy về (Retrieve/Fetch) / Truy vấn (Query) / Tải xuống (Download) |
| Sử dụng (Use) | Áp dụng (Apply) / Gọi (Invoke) / Thực thi (Execute) / Quy đổi (Redeem) |
| Đảm nhiệm (Take care of)| Dùng động từ cụ thể |

**Áp dụng điều này cho cả Tên UC và phần nội dung các bước.**

---

## Quy tắc 5: Tránh các chi tiết triển khai

Một UC mô tả **LÀM GÌ** (WHAT - hành động), không phải **LÀM NHƯ THẾ NÀO** (HOW - cơ chế). Hãy để chữ LÀM NHƯ THẾ NÀO lại cho giai đoạn thiết kế (design).

- ❌ "Hệ thống gọi POST /api/v1/enrollments với header Authorization Bearer {token}, body {course_id, learner_id}…"
- ✅ "Hệ thống tạo bản ghi đăng ký trên hệ thống LMS"

- ❌ "Hệ thống chèn một hàng vào bảng tbl_enrollments với các trường: enroll_id, course_id, learner_id, created_at…"
- ✅ "Hệ thống lưu thông tin đăng ký vào cơ sở dữ liệu"

- ❌ "Hệ thống render component React <EnrollmentSuccessModal> với prop courseTitle='BA Fundamentals'…"
- ✅ "Hệ thống hiển thị màn hình Xác nhận Đăng ký cùng với tên khóa học và link truy cập"

**Ngoại lệ**: Nếu bản thân UC là một tài liệu đặc tả tích hợp, nó có thể chi tiết hơn — nhưng vẫn nên sử dụng ngôn ngữ nghiệp vụ.

---

## Quy tắc 6: Đánh số nhất quán

### Luồng cơ bản (Normal Course)
Danh sách đánh số bắt đầu từ 1.

### Luồng thay thế (Alternative Course)
Đánh số phụ dựa theo bước gốc + chữ cái:
- AC tại bước 5 → bước 5a, 5b, 5c
- Sau khi kết thúc AC, ghi "tiếp tục từ bước N của Luồng cơ bản"

### Mã Ngoại lệ (Exception ID)
Định dạng: `UC-XX.EX.N` (được đánh số độc lập, không gắn liền với một bước cụ thể nào)

### Tiền/Hậu điều kiện (Pre/Postconditions)
Danh sách đánh số bắt đầu từ 1.

---

## Quy tắc 7: Đặt tên các thành phần giao diện (UI)

Khi đề cập đến một thành phần giao diện trong một bước, hãy **in đậm** và sử dụng nhãn hiển thị thực tế trên màn hình:

- ✅ "Học viên click vào nút **Đăng ký ngay**"
- ✅ "Hệ thống hiển thị màn hình **Tóm tắt Đơn hàng**"
- ✅ "Học viên chọn **Voucher Doanh nghiệp** từ danh sách thả xuống phương thức thanh toán"

Lý do: Giúp dễ dàng truy xuất lại từ các wireframe/mockup trong quá trình bàn giao thiết kế.

---

## Quy tắc 8: Tránh các từ ngữ chung chung

| ❌ Chung chung | ✅ Cụ thể |
|--------------|-----------|
| Trong một số trường hợp | Khi điều kiện X xảy ra |
| Có thể (May / can) | Khi [điều kiện], hệ thống [hành động] |
| Thỉnh thoảng (Sometimes) | X% số lần / Y lần mỗi Z |
| Nếu cần thiết | Khi [yếu tố kích hoạt cụ thể] |
| Hợp lệ (Valid) | Đáp ứng các tiêu chí: … (liệt kê ra) |
| Phù hợp (Appropriate)| Theo chính sách [tham chiếu] của BA Zone |
| Nhanh chóng (Quickly)| Trong vòng X giây |
| Người dùng (User) | Học viên / Cố vấn / Quản trị viên BO / Quản lý Nhân sự |

---

## Quy tắc 9: Không lồng ghép các quy tắc nghiệp vụ vào các bước

Một bước của Luồng cơ bản mô tả **luồng chạy** (flow). Các quy tắc nghiệp vụ (các quy tắc xác thực, giới hạn, logic kinh doanh) nên:
- Tham chiếu tới phần Yêu cầu đặc biệt (Special Requirements) theo mã số quy tắc (rule ID)
- Hoặc nằm trong một tài liệu Quy tắc Nghiệp vụ riêng biệt (BR-XX-YY)

- ❌ "5. Hệ thống xác thực: chủ đề hẹn phải ≤ 500 ký tự, học viên phải còn ≥ 1 số lượt quota chưa sử dụng, lịch hẹn phải cách hiện tại ≥ 2 giờ, mentor không được đang trong kỳ nghỉ..."
- ✅ "5. Hệ thống xác thực yêu cầu đặt lịch hẹn theo quy tắc nghiệp vụ BR-MENTOR-001."
  - (Sau đó liệt kê BR-MENTOR-001 trong phần Yêu cầu đặc biệt hoặc tài liệu BR riêng biệt)

---

## Quy tắc 10: Hướng dẫn về độ dài

- **Tên UC**: 3-7 từ
- **Mô tả**: 2-4 câu, ~50-100 từ
- **Luồng cơ bản**: 5-15 bước (thường là 7-10 bước cho các UC của Digital School)
- **Mỗi bước**: 1 câu, tối đa 2 câu, < 30 từ
- **Luồng thay thế**: 1-5 AC cho mỗi UC (nếu nhiều hơn → cân nhắc chia nhỏ UC)
- **Ngoại lệ**: 3-7 cho một UC điển hình
- **Tổng tài liệu UC**: 2-5 trang A4

Nếu bạn vượt quá hướng dẫn này:
- UC quá dài → chia nhỏ thông qua phần Bao gồm (Includes)
- Quá nhiều AC/EX → xem lại phạm vi, UC này có thể đang gánh vác quá nhiều

---

## Quy tắc 11: Tính nhất quán trên toàn bộ dự án

Giữ tính nhất quán trên toàn bộ tập tài liệu:
- Tên các tác nhân (đừng chuyển đổi qua lại giữa "Học viên", "Sinh viên", "Người dùng", "Người tham gia")
- Tên các thành phần hệ thống (LMS, Learning Management System, Moodle → hãy chọn một tên)
- Tên màn hình/menu (phải khớp với wireframe hoặc đặc tả sản phẩm)
- Quy ước đặt tên cho Mã UC (UC IDs)

Mẹo: Duy trì một **Bảng thuật ngữ (Glossary)** ở đầu tập tài liệu. Đối với Digital School, hãy thống nhất từ đầu: dùng "Learner" hay "Student"? "Mentor" hay "Instructor"?

---

## Quy tắc 12: Đa ngôn ngữ (Internationalization - i18n)

Nếu nền tảng Digital School có yêu cầu hỗ trợ đa ngôn ngữ:
- Tên các màn hình/nút bấm trong UC có thể sử dụng mã (key) thay vì text tĩnh
- Ví dụ: thay "click vào nút **Đăng ký ngay**" thành "click vào nút {btn.enroll_now}"
- Tuy nhiên, đối với hầu hết các đặc tả UC của BA Zone, dùng nhãn tiếng Anh (hoặc tiếng Việt) thông thường là đủ.

---

## Các lỗi nên tránh (Anti-patterns) — 10 sai lầm phổ biến nhất

### 1. UC là một bản đặc tả giao diện (UI spec) chi tiết tới từng pixel
❌ "Hệ thống hiển thị một hộp thoại (modal) với phần tiêu đề màu xanh #1E88E5 'Xác nhận Đăng ký', một icon dấu tích, và ảnh thu nhỏ của khóa học ở bên trái..."
→ Đó là phần ghi chú dành cho wireframe. Một UC nên viết: "Hệ thống hiển thị màn hình Xác nhận Đăng ký cùng với tên khóa học và một nút Tới khóa học."

### 2. Trộn lẫn tác nhân và hệ thống trong cùng một bước
❌ "3. Học viên chọn lịch hẹn và hệ thống kiểm tra hạn mức."
→ Hãy tách thành 2 bước.

### 3. Bỏ qua phản hồi của hệ thống
❌ "1. Học viên click Đăng ký ngay. 2. Học viên nhập thông tin thanh toán. 3. Học viên xác nhận."
→ Phản hồi của hệ thống giữa các bước đang bị thiếu. Một UC phải thể hiện ĐOẠN HỘI THOẠI giữa tác nhân ↔ hệ thống.

### 4. Lồng ghép logic điều kiện (if-else)
❌ "5. Nếu học viên có gói đăng ký Premium, hệ thống cho phép chọn mentor; nếu không chỉ hiển thị các mentor miễn phí."
→ Tách ra thành Luồng cơ bản (trường hợp mặc định) + AC (nhánh Premium) hoặc Ngoại lệ (truy cập không có quyền).

### 5. Yếu tố kích hoạt (trigger) quá chung chung
❌ "Khi học viên muốn lấy chứng chỉ, họ sẽ..."
→ Hãy cụ thể: "Khi học viên điều hướng tới tab **Chứng chỉ** sau khi hoàn thành khóa học..."

### 6. Hậu điều kiện (Postcondition) là một hành động thay vì là một trạng thái
❌ "Hệ thống gửi chứng chỉ cho học viên" (hành động)
→ "Một email chứa chứng chỉ đã được gửi tới địa chỉ email đăng ký của học viên" (trạng thái) ← có thể xác minh được

### 7. UC có 2 tác nhân chính (primary actors)
❌ Tác nhân chính: Học viên + Quản lý Nhân sự (cả hai đều khởi xướng UC)
→ Hãy tách thành 2 UC: một cho việc tự đăng ký (self-enrollment), và một cho việc quản lý nhân sự chỉ định khóa học.

### 8. Các quy trình xử lý chung chung của hệ thống
❌ "5. Hệ thống xử lý thông tin đăng ký."
→ Hãy cụ thể: "Hệ thống tạo bản ghi đăng ký trên hệ thống LMS và cấp cho học viên quyền truy cập vào toàn bộ các bài học đã xuất bản."

### 9. Lặp lại phần Mô tả (Description) bên trong Luồng cơ bản
Nếu phần Mô tả đã nêu rõ toàn bộ luồng, đừng copy nó vào Luồng cơ bản. Phần Mô tả chỉ là tóm tắt từ 2-3 câu; Luồng cơ bản là phần chi tiết từng bước.

### 10. Quên các chế độ thất bại (failure modes)
Một UC chỉ có Luồng cơ bản + 1 Ngoại lệ "lỗi" chung chung → chưa đủ.
Đối với các UC của Digital School, luôn luôn bao hàm: lỗi thanh toán, hết hạn mức, hết thời gian chờ của dịch vụ bên ngoài, xung đột đồng thời (hai học viên cùng tranh một suất hẹn), và không khớp quyền/vai trò.

---
*Tổng hợp bởi **Phúc NT** · BA Zone · Digital School*  
*Vui lòng ghi nguồn khi chia sẻ hoặc điều chỉnh hướng dẫn này.*
