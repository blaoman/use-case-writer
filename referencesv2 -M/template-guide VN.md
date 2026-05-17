# Hướng dẫn Template (Template Guide) — Cách điền từng trường

Hướng dẫn chi tiết để điền từng trường trong 13 trường của template, kèm theo các ví dụ đỗ/trượt (pass/fail) trong lĩnh vực EdTech & Digital School.

Tổng hợp bởi **Phúc NT** · BA Zone · Digital School

## Mục lục
1. [Mã Use Case (Use Case ID)](#1-mã-use-case-use-case-id)
2. [Tên Use Case (Use Case Name)](#2-tên-use-case-use-case-name)
3. [Lịch sử Use Case (Use Case History)](#3-lịch-sử-use-case-use-case-history)
4. [Tác nhân (Actor)](#4-tác-nhân-actor)
5. [Mô tả (Description)](#5-mô-tả-description)
6. [Tiền điều kiện (Preconditions)](#6-tiền-điều-kiện-preconditions)
7. [Hậu điều kiện (Postconditions)](#7-hậu-điều-kiện-postconditions)
8. [Mức ưu tiên (Priority)](#8-mức-ưu-tiên-priority)
9. [Tần suất sử dụng (Frequency of Use)](#9-tần-suất-sử-dụng-frequency-of-use)
10. [Luồng cơ bản (Normal Course of Events)](#10-luồng-cơ-bản-normal-course-of-events)
11. [Luồng thay thế (Alternative Courses)](#11-luồng-thay-thế-alternative-courses)
12. [Ngoại lệ (Exceptions)](#12-ngoại-lệ-exceptions)
13. [Bao gồm (Includes)](#13-bao-gồm-includes)
14. [Yêu cầu đặc biệt (Special Requirements)](#14-yêu-cầu-đặc-biệt-special-requirements)
15. [Giả định (Assumptions)](#15-giả-định-assumptions)
16. [Ghi chú và Vấn đề (Notes and Issues)](#16-ghi-chú-và-vấn-đề-notes-and-issues)

---

## 1. Mã Use Case (Use Case ID)

**Mục đích**: Mã định danh duy nhất để các yêu cầu có thể được truy xuất nguồn gốc ngược lại (trace back) tới UC này.

**Quy tắc**:
- Định dạng: `UC-<module>-<số thứ tự>` hoặc `UC-X.Y` (phân cấp)
- Sử dụng quy ước đặt tên nhất quán trên toàn bộ dự án
- Đối với các nhóm UC có liên quan, sử dụng X.Y (ví dụ: UC-3.1, UC-3.2 thuộc nhóm "Đăng ký khóa học")
- Thêm số 0 cho độ dài từ 2-3 chữ số: `UC-LEARN-01`, `UC-MENTOR-003`

**Ví dụ tốt**:
- `UC-LEARN-01` (Module Đăng ký/Học tập, UC số 1)
- `UC-MENTOR-03` (Module Cố vấn, UC số 3)
- `UC-3.2` (phân cấp, sub-UC thứ 2 của nhóm số 3)

**Ví dụ chưa tốt**:
- `UC1` (không có quy ước rõ ràng)
- `UseCase_CourseEnrollment` (gắn tên chung vào ID — khó bảo trì khi tên UC thay đổi)

---

## 2. Tên Use Case (Use Case Name)

**Mục đích**: Nhãn ngắn gọn mô tả mục tiêu của UC.

**Quy tắc RẤT QUAN TRỌNG**:
- PHẢI theo cấu trúc **"Động từ hành động + Tân ngữ"** (Action verb + Object)
- Từ 3-7 chữ, không quá dài
- KHÔNG bắt đầu bằng tên của tác nhân
- KHÔNG sử dụng các động từ chung chung ("quản lý", "xử lý", "tiến hành", "làm")
- Phản ánh mục tiêu của tác nhân, không phải quá trình triển khai kỹ thuật

**Mẫu (Pattern)**: `<Động từ> <Tân ngữ trực tiếp> [<Bổ ngữ>]`

**Ví dụ tốt** (Digital School / BA Zone):
- ✅ "Đăng ký khóa học Digital School"
- ✅ "Đặt lịch hẹn cố vấn 1-kèm-1"
- ✅ "Cấp chứng chỉ hoàn thành khóa học"
- ✅ "Phê duyệt hồ sơ KYC của học viên"
- ✅ "Cấp phát license doanh nghiệp cho nhân viên"

**Ví dụ chưa tốt → cách sửa**:
- ❌ "Sự đăng ký" (Enrollment) → ✅ "Đăng ký khóa học"
- ❌ "Học viên đặt lịch hẹn" (bao gồm tác nhân) → ✅ "Đặt lịch hẹn cố vấn"
- ❌ "Quản lý lộ trình học tập" (động từ chung chung) → tách thành "Tạo mới lộ trình", "Cập nhật lộ trình", "Lưu trữ lộ trình"
- ❌ "Chứng chỉ được cấp" (thể bị động) → ✅ "Cấp chứng chỉ hoàn thành"

---

## 3. Lịch sử Use Case (Use Case History)

**Mục đích**: Theo dõi vết kiểm toán (Người tạo, Ngày tạo, Người cập nhật cuối, Ngày cập nhật cuối).

**Quy tắc**:
- Người tạo (Created By): họ tên đầy đủ + vai trò (VD: "Phúc NT - BA Zone")
- Ngày tạo (Date Created): định dạng YYYY-MM-DD
- Người cập nhật cuối + Ngày cập nhật cuối: cập nhật trong mỗi lần chỉnh sửa
- Nếu chưa biết, hãy dùng ký tự giữ chỗ `<TBD>` (To Be Determined) thay vì để trống.

---

## 4. Tác nhân (Actor)

**Mục đích**: Xác định ai/cái gì tương tác với hệ thống.

**Phân loại tác nhân**:
- **Tác nhân chính (Primary actor)**: Khởi xướng UC, được hưởng lợi từ kết quả
- **Tác nhân phụ (Secondary actor)**: Hệ thống/người hỗ trợ (cổng thanh toán, LMS, dịch vụ lịch)
- **Bên liên quan ẩn (Off-stage stakeholder)**: Có sự quan tâm nhưng không trực tiếp tương tác (cơ quan quản lý, kiểm toán) — thường KHÔNG được liệt kê trong trường Actor

**Quy tắc**:
- Tác nhân chính PHẢI là một vai trò/lớp cụ thể — tuyệt đối không ghi "Người dùng" (User) một cách chung chung.
- Một UC nên có 1 tác nhân chính (hiếm khi có từ 2 trở lên).
- Nếu có tác nhân phụ, hãy gán nhãn rõ ràng.

**Ví dụ tốt** (Digital School / BA Zone):
- ✅ "Chính: Học viên (người đăng ký Digital School Premium, email đã xác minh)"
- ✅ "Chính: Cố vấn (được chứng nhận BA Zone, tài khoản đang hoạt động)"
- ✅ "Chính: Quản lý Nhân sự (Đối tác doanh nghiệp với quyền quản trị license)"
- ✅ "Chính: Quản trị viên BO; Phụ: Dịch vụ AML, Dịch vụ Thông báo"

**Ví dụ chưa tốt**:
- ❌ "Người dùng" (User - quá chung chung)
- ❌ "Sinh viên" (Student - mơ hồ, có giống với Học viên không?)
- ❌ "Hệ thống" (System - bản thân hệ thống là mục tiêu của UC, không phải là tác nhân)

---

## 5. Mô tả (Description)

**Mục đích**: Tóm tắt UC trong 2-3 câu để người đọc có thể nhanh chóng nắm bắt nội dung.

**Quy tắc — phải trả lời được 3 câu hỏi**:
1. **TẠI SAO (WHY)**: Lý do/Yếu tố kích hoạt (trigger) dẫn đến UC này
2. **LÀM GÌ (WHAT)**: Tác nhân làm gì với hệ thống
3. **KẾT QUẢ (OUTCOME)**: Trạng thái cuối cùng (trạng thái hệ thống mới / giá trị nhận được)

**Mẫu (Pattern)**: `[Khi/Để] <lý do/trigger>, <tác nhân> <hành động> nhằm <kết quả>.`

**Ví dụ tốt** (Digital School):
> "Khi một học viên hoàn thành mọi bài học và vượt qua bài kiểm tra cuối khóa học Digital School, học viên đó điều hướng tới mục Chứng chỉ để tải xuống chứng chỉ hoàn thành. UC kết thúc khi một file PDF chứng chỉ cá nhân hóa được tạo ra cùng một mã xác minh duy nhất, được học viên tải về, và được ghi nhận lại trong bảng Certificates."

**Ví dụ chưa tốt**:
> ❌ "UC này nói về chứng chỉ." (quá ngắn, thiếu TẠI SAO và KẾT QUẢ)
> ❌ "Module chứng chỉ có các bước: yêu cầu, tạo, tải xuống…" (đang mô tả một luồng làm việc thay vì viết tóm tắt)

---

## 6. Tiền điều kiện (Preconditions)

**Mục đích**: Liệt kê các điều kiện PHẢI đúng trước khi UC có thể bắt đầu.

**Quy tắc RẤT QUAN TRỌNG**:
- Mọi tiền điều kiện phải có thể **xác minh được** (thường là phép kiểm tra đúng/sai - boolean)
- Đánh số thứ tự: 1, 2, 3…
- Phân biệt với Quy tắc Nghiệp vụ (Business Rules):
  - Tiền điều kiện: được kiểm tra TRƯỚC KHI UC bắt đầu
  - Quy tắc nghiệp vụ: được áp dụng TRONG QUÁ TRÌNH luồng UC chạy
- Phân biệt với Giả định (Assumptions):
  - Tiền điều kiện: BẮT BUỘC ĐỂ UC có thể chạy
  - Giả định: ĐƯỢC TIN là đúng nhưng không xác minh

**Ví dụ tốt** (Digital School):
```
1. Học viên đã đăng nhập vào BA Zone bằng email đã được xác minh
2. Học viên đã hoàn thành 100% các bài học của khóa (tiến độ = 100%)
3. Học viên đã vượt qua bài kiểm tra cuối khóa với điểm số ≥ 70%
4. Dịch vụ tạo chứng chỉ đang khả dụng
```

**Ví dụ chưa tốt**:
- ❌ "Hệ thống đang hoạt động" (quá chung chung, không xác minh được)
- ❌ "Học viên muốn có một chứng chỉ" (đây là động lực, không phải điều kiện)
- ❌ "Học viên phải có phương thức thanh toán hợp lệ" (điều này thuộc về một UC thanh toán, không phải UC chứng chỉ)

---

## 7. Hậu điều kiện (Postconditions)

**Mục đích**: Mô tả trạng thái của hệ thống SAU KHI UC hoàn tất thành công.

**Quy tắc**:
- Xác minh được (có thể kiểm tra thông qua truy vấn DB / phản hồi từ API)
- Bao phủ đủ mọi loại thay đổi:
  - Trạng thái dữ liệu (bản ghi mới, đổi trạng thái)
  - Trạng thái trực quan của người dùng (gửi thông báo, file sẵn sàng để tải xuống)
  - Trạng thái của hệ thống bên ngoài (gọi API thành công, khóa khung giờ trên lịch)
- Đánh số thứ tự

**Quan trọng**: Hậu điều kiện là một **trạng thái** (state), không phải một **hành động** (action).
- ✅ Trạng thái: "Bản ghi chứng chỉ được lưu lại với mã xác minh duy nhất"
- ❌ Hành động: "Hệ thống lưu lại bản ghi chứng chỉ" (đây là một bước trong Luồng cơ bản)

**Ví dụ tốt** (Digital School):
```
1. Bản ghi chứng chỉ được tạo trong bảng Certificates với một mã xác minh duy nhất (định dạng: CERT-BAZONE-YYYY-NNNNN)
2. File chứng chỉ PDF được tạo ra và lưu trữ trên đám mây, có thể truy cập qua một đường dẫn cố định
3. Hồ sơ của học viên hiển thị huy hiệu (badge) chứng chỉ cho khóa học đã hoàn thành
4. Trang xác minh chứng chỉ được mở công khai tại verify.bazone.vn bằng mã duy nhất
5. Thông báo hoàn thành được gửi đến email học viên và trung tâm thông báo trong ứng dụng
```

---

## 8. Mức ưu tiên (Priority)

**Mục đích**: Xác định mức độ ưu tiên triển khai của UC.

**Các hệ thống phân loại phổ biến**:
- **MoSCoW**: Must (Phải có) / Should (Nên có) / Could (Có thể có) / Wonắp (Chưa cần lúc này)
- **3 mức (3-level)**: Cao (High) / Trung bình (Medium) / Thấp (Low)

**Quy tắc**:
- Sử dụng CÙNG MỘT hệ thống ưu tiên đang dùng trong tài liệu SRS / PRD của dự án
- Đưa ra lý do (một câu giải thích tại sao mức ưu tiên lại là X)

**Ví dụ tốt** (Digital School):
- "Cao — Tính năng cốt lõi; gắn liền trực tiếp với tỷ lệ giữ chân và tỷ lệ hoàn thành khóa học"
- "Trung bình — Nâng cao trải nghiệm cho đối tác doanh nghiệp; đã lên kế hoạch cho phase 2"

---

## 9. Tần suất sử dụng (Frequency of Use)

**Mục đích**: Ước tính mức độ thường xuyên thực thi UC → là thông tin đầu vào cho việc lập kế hoạch hiệu suất/dung lượng.

**Quy tắc**:
- Sử dụng CON SỐ CỤ THỂ (không dùng "đôi khi", "thường xuyên")
- Đơn vị thời gian phù hợp: mỗi giây, mỗi giờ, mỗi ngày, mỗi tháng
- Nếu có thời gian cao điểm, hãy ghi chú rõ

**Ví dụ tốt** (Digital School):
- "~500 lượt đăng ký/ngày; đỉnh điểm ~100 lượt/giờ trong các chiến dịch và đợt ra mắt khóa học mới"
- "~15 yêu cầu hẹn/ngày cho mỗi cố vấn; toàn hệ thống ~300/ngày trải đều cho 20 cố vấn hoạt động; đỉnh điểm vào tối Chủ Nhật"

**Ví dụ chưa tốt**:
- ❌ "Thường xuyên"
- ❌ "Hằng ngày" (không rõ số lượng)

---

## 10. Luồng cơ bản (Normal Course of Events)

**Mục đích**: Mô tả "happy path" — luồng chạy thành công từ lúc kích hoạt (trigger) đến lúc đạt mục tiêu.

**Quy tắc RẤT QUAN TRỌNG** (đây là trường dễ mắc lỗi nhất):

### 10.1. Định dạng
- Dạng danh sách đánh số (1, 2, 3…)
- Mỗi bước: chỉ có MỘT hành động duy nhất
- Bắt đầu với một chủ ngữ rõ ràng (Tác nhân / Hệ thống)
- Thể chủ động + thì hiện tại
- Ngắn gọn, 1-2 câu cho mỗi bước

### 10.2. Luân phiên Tác nhân / Hệ thống
Mẫu điển hình: Tác nhân → Hệ thống → Tác nhân → Hệ thống…
- Bước lẻ: thao tác của tác nhân (đầu vào)
- Bước chẵn: hệ thống phản hồi

### 10.3. KHÔNG ĐƯỢC lồng ghép:
- ❌ Các câu lệnh If/else → chuyển sang Luồng thay thế (Alternative Course)
- ❌ Vòng lặp → ghi rõ "Các bước từ X-Y lặp lại cho đến khi Z"
- ❌ Ngoại lệ → chuyển sang Ngoại lệ (Exceptions)
- ❌ Logic xử lý ngầm (internal logic) → đó là thiết kế (design), không phải UC

### 10.4. Điểm bắt đầu và kết thúc
- Bước 1: Yếu tố kích hoạt (sự kiện khiến UC khởi chạy)
- Bước cuối cùng: Mục tiêu được hoàn thành (đạt được hậu điều kiện)

**Ví dụ tốt** (Digital School — đặt lịch hẹn cố vấn):
```
1. Học viên điều hướng tới mục "Cố vấn của tôi" và chọn hồ sơ của một cố vấn.
2. Hệ thống hiển thị hồ sơ cố vấn: tiểu sử, chuyên môn, đánh giá trung bình, và các khung giờ còn trống trong 14 ngày tới.
3. Học viên chọn một ngày và một khung giờ ưng ý.
4. Học viên nhập chủ đề hoặc câu hỏi cho buổi hẹn (tối đa 500 ký tự) và click "Gửi yêu cầu".
5. Hệ thống xác thực xem học viên có còn ít nhất 1 suất hẹn trong gói đăng ký hiện tại hay không.
6. Hệ thống tạo một yêu cầu buổi hẹn với trạng thái='Chờ_Cố_Vấn_Duyệt' (Pending_Mentor_Review) và gửi thông báo tới cố vấn.
7. Hệ thống hiển thị màn hình xác nhận: "Yêu cầu đã được gửi! Cố vấn của bạn sẽ phản hồi trong vòng 24 giờ."
8. Hệ thống gọi UC-NOTI-03 để gửi một email xác nhận tới học viên.
```

**Ví dụ chưa tốt → cách sửa**:
- ❌ "1. Nếu học viên có gói đăng ký Premium, họ có thể chọn bất kỳ cố vấn nào; nếu không, họ chỉ có thể chọn ở hạng miễn phí…" → Chuyển việc phân nhánh này xuống Luồng thay thế (Alternative Course)
- ❌ "3. Hệ thống xác thực. Nếu lỗi, hiển thị lỗi. Nếu hợp lệ, tiếp tục." → Xác thực thành công thì tự tiếp tục luồng; Xác thực lỗi (fail) thì thuộc về Ngoại lệ (Exception)
- ❌ "5. Hệ thống gọi POST /api/v1/sessions với body {learner_id, mentor_id, slot_id}" → Quá sâu về kỹ thuật. Hãy nói: "Hệ thống tạo yêu cầu buổi hẹn trong cơ sở dữ liệu."

---

## 11. Luồng thay thế (Alternative Courses)

**Mục đích**: Một con đường KHÁC nhưng vẫn đi tới mục tiêu (vẫn thành công).

**Quy tắc**:
- Định dạng mã (ID): `UC-XX.AC.N` (AC = Alternative Course)
- Mỗi AC luôn bắt đầu bằng: "Tại bước Y của Luồng cơ bản, nếu [điều kiện], thực hiện thay thế: …"
- Cuối AC, ghi chú rõ sẽ tiếp tục quay lại chạy Luồng cơ bản từ bước nào.

**Ví dụ tốt** (Digital School):
```
UC-LEARN-01.AC.1: Đăng ký bằng voucher doanh nghiệp
Tại bước 5 của Luồng cơ bản, nếu học viên chọn "Voucher Doanh nghiệp" làm phương thức thanh toán:
5a. Hệ thống hiển thị một trường nhập mã voucher.
5b. Học viên nhập mã và click "Áp dụng".
5c. Hệ thống xác thực mã voucher (hạn sử dụng, mức độ phù hợp, số lần dùng còn lại).
5d. Hệ thống cập nhật tổng số tiền thanh toán thành 0 VNĐ → tiếp tục từ bước 7 của Luồng cơ bản (không gọi qua cổng thanh toán).
```

---

## 12. Ngoại lệ (Exceptions)

**Mục đích**: Các trường hợp UC BỊ LỖI (không đạt được mục tiêu).

**Quy tắc**:
- Định dạng mã (ID): `UC-XX.EX.N` (EX = Exception)
- Mỗi ngoại lệ cần có đủ 3 phần:
  1. **Điều kiện kích hoạt (Trigger)**: Khi nào thì ngoại lệ xảy ra
  2. **Phản hồi của hệ thống (System response)**: Hệ thống làm gì
  3. **Trạng thái cuối cùng (Final state)**: Kết thúc ở đâu (hủy thao tác? lưu tạm? ghi log?)

**Các trường hợp lỗi phổ biến cần kiểm tra** (đừng bỏ sót):
- Lỗi xác thực (sai định dạng, thiếu trường bắt buộc)
- Vi phạm quy tắc nghiệp vụ (hết hạn mức, khóa học đã kín chỗ)
- Lỗi từ dịch vụ bên ngoài (cổng thanh toán hết thời gian chờ, LMS không khả dụng)
- Các vấn đề về mạng/kết nối
- Từ chối quyền truy cập (Permission denied / authorization failure)
- Xung đột đồng thời (một suất vừa bị học viên khác giành lấy cùng lúc)
- Hết thời gian chờ của phiên (mentor treo máy quá lâu tại màn hình chi tiết)

**Ví dụ tốt** (Digital School):
```
UC-LEARN-01.EX.2: Khóa học đã kín chỗ ở thời điểm giữa lúc tải trang và xác nhận đăng ký
Kích hoạt: Tại bước 7, LMS trả về mã lỗi CAPACITY_EXCEEDED (VƯỢT SỨC CHỨA) bởi một học viên khác đã đăng ký chỗ cuối cùng vào vài mili-giây trước đó.
Phản hồi: Hệ thống hiển thị "Xin lỗi, khóa học này vừa kín chỗ. Bạn hãy tham gia danh sách chờ để được thông báo khi có chỗ trống nhé."
Trạng thái cuối cùng: Tiền thanh toán tự động được hoàn trả trong vòng 1 ngày làm việc. Không có bản ghi đăng ký nào được tạo. Đưa ra đề xuất tham gia danh sách chờ cho học viên.
```

---

## 13. Bao gồm (Includes)

**Mục đích**: Tái sử dụng (reuse) các chức năng chung giữa các UC.

**Quy tắc**:
- Liệt kê các UC con (sub-UC) được UC này gọi đến (ngữ nghĩa «include» của UML)
- UC con đó bắt buộc phải tồn tại (đã được định nghĩa)
- KHÔNG sử dụng Includes chỉ để nhóm các bước nhỏ — chỉ dùng khi logic đó được tái sử dụng ở các UC khác.

**Ví dụ tốt** (Digital School):
```
- UC-PAY-01: Xử lý thanh toán (được gọi tại bước 6 của Luồng cơ bản)
- UC-NOTI-01: Gửi thông báo đăng ký (được gọi tại bước 9)
```

---

## 14. Yêu cầu đặc biệt (Special Requirements)

**Mục đích**: Chứa các yêu cầu phi chức năng (non-functional requirements) cụ thể của UC này.

**Các phân loại cần quan tâm**:
- **Hiệu suất (Performance)**: Thời gian phản hồi, thông lượng, số lượng người dùng đồng thời
- **Bảo mật (Security)**: Xác thực, mã hóa, bảo vệ quyền riêng tư
- **Tính khả dụng (Usability)**: Khả năng tiếp cận, ưu tiên thiết bị di động (mobile-first)
- **Độ tin cậy (Reliability)**: Thời gian duy trì hoạt động (Uptime), chiến lược dự phòng bất đồng bộ
- **Tính tuân thủ (Compliance)**: Các yêu cầu pháp lý (hóa đơn VAT, lưu trữ dữ liệu)

**Quy tắc**: KHÔNG LẶP LẠI các yêu cầu chức năng (functional requirements) — mục này chỉ dành cho các yêu cầu phi chức năng.

**Ví dụ tốt** (Digital School):
```
- Hiệu suất: Trang danh mục khóa học tải ≤ 2s dưới áp lực 5.000 học viên truy cập đồng thời
- Bảo mật: Dữ liệu thẻ thanh toán không bao giờ được lưu trữ trên server BA Zone; mọi việc xử lý thẻ thông qua cổng thanh toán đạt chuẩn PCI-DSS
- Độ tin cậy: Nếu LMS không khả dụng trong quá trình đăng ký, KHÔNG được phép rollback tiền thanh toán — thử lại bất đồng bộ tối đa 30 phút
- Tuân thủ: Xuất hóa đơn VAT cho mọi giao dịch ≥ 200.000 VNĐ (Luật thuế Việt Nam)
```

---

## 15. Giả định (Assumptions)

**Mục đích**: Những thứ được ngầm mặc định đúng trong quá trình phân tích nhưng chưa được kiểm chứng.

**Phân biệt với Tiền điều kiện (Precondition)**:
- Tiền điều kiện: PHẢI LÀ ĐÚNG, hệ thống có thể kiểm tra
- Giả định: ĐƯỢC TIN LÀ ĐÚNG, không bắt buộc phải kiểm tra

**Ví dụ tốt** (Digital School):
```
1. Địa chỉ email của học viên đang hoạt động và đã được xác minh — các email chào mừng sẽ không bị lỗi trả về (bounce)
2. SLA của cổng thanh toán là ≥ 99.5% uptime trong giờ làm việc
3. Các voucher doanh nghiệp đã được nạp (pre-loaded) bởi nhóm vận hành của BA Zone trước khi gửi cho đối tác
4. Việc cấp quyền truy cập của LMS hoàn thành đồng bộ trong < 3s dưới điều kiện tải bình thường
```

---

## 16. Ghi chú và Vấn đề (Notes and Issues)

**Mục đích**: Dùng để chứa các câu hỏi mở, các mục cần xác định thêm (TBD), các hạng mục cần theo dõi.

**Định dạng**:
```
[TBD-N] | Người phụ trách (Owner) | Thời hạn (Due Date) | Giải pháp (Resolution)
```

**Ví dụ tốt** (Digital School):
```
- [TBD-1] Học viên có nên được phép dùng gói khóa học để tặng người dùng khác không? | Phụ trách: Đội Sản phẩm | Deadline: 2026-06-01 | Giải pháp: TBD — hoãn lại cho phase 2
- [TBD-2] Chính sách hoàn tiền ra sao nếu học viên yêu cầu hoàn lại trong vòng 7 ngày? | Phụ trách: Phúc NT - BA Zone | Deadline: 2026-05-25 | Giải pháp: TBD
- [NOTE] Mẫu email chào mừng phải tuân thủ chuẩn thương hiệu (brand guidelines) hiện tại của Digital School — cần phối hợp với đội Marketing
```

---
*Tổng hợp bởi **Phúc NT** · BA Zone · Digital School*  
*Vui lòng ghi nguồn khi chia sẻ hoặc điều chỉnh hướng dẫn này.*
