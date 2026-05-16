# Use Case Writer · BA Zone

[English](#english) | [Tiếng Việt](#tiếng-việt)

---

## English

> A Claude AI skill that helps IT Business Analysts **scope, analyze, and document Use Cases** in English Markdown, following the industry-standard 13-field template (Karl Wiegers / IIBA style) with best practices from Alistair Cockburn's *Writing Effective Use Cases*.
>
> Developed by **Phúc NT** for the **BA Zone** — Vietnam's Business Analyst & Product Owner community.

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-orange)](https://claude.ai)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)
[![Author](https://img.shields.io/badge/Author-Ph%C3%BAc%20NT-purple)](#)
[![BA Zone](https://img.shields.io/badge/BA-Zone-orange)](https://bazone.vn)
[![Output](https://img.shields.io/badge/Output-English%20Markdown-green)](#)
[![Template](https://img.shields.io/badge/Template-Karl%20Wiegers%20%2F%20IIBA-blue)](#)

---

## Why this skill?

Writing a high-quality Use Case spec is harder than it looks. BAs commonly struggle with:

- **Wrong scope**: writing UCs that are too big (entire workflows) or too small (sub-functions like "Verify OTP")
- **Vague actors**: using "User" instead of specific roles like Learner, Mentor, or HR Manager
- **Embedded logic**: stuffing if/else and loops into the Normal Course
- **Missing failure modes**: only writing the happy path
- **Confusing Preconditions with Business Rules**

This skill enforces the discipline by:

1. **Scoping first** — applying Cockburn's coffee-break test, goal levels, and system boundary rules before writing anything
2. **Generating sequentially** — section by section, stopping for confirmation so issues are caught early
3. **Validating with a 20-point checklist** — every UC is reviewed before handover

---

## Features

- ✅ **English Markdown output** following the standard 13-field template
- ✅ **Sequential workflow** — 5 section groups, with confirmation gates between them
- ✅ **4 modes**: write new, split feature into UC list, refine existing, or write a specific section
- ✅ **Scoping rules** based on Alistair Cockburn (coffee-break test, goal levels, one-actor-one-goal-one-session, system boundary)
- ✅ **3 identification techniques** for breaking down large features: goal-driven, event-driven, CRUD-driven
- ✅ **20-point quality checklist** auto-run before handover
- ✅ **Bilingual interaction** — chat in Vietnamese or English, produce the UC artifact in English
- ✅ **2 complete EdTech UC examples** included as reference (Course Enrollment, Mentor Session Approval)

---

## Repository structure

```
ba-zone-use-case-writer/
├── SKILL.md                          # Main workflow (loaded into Claude's context)
├── references/                       # Reference docs (loaded on demand)
│   ├── template-guide.md             # How to fill each of the 13 fields, with Digital School examples
│   ├── writing-style.md              # Active voice rules, numbering conventions, 10 anti-patterns
│   ├── quality-checklist.md          # 20-point validation checklist with pass/fail examples
│   └── examples-edtech.md            # 2 full EdTech UC examples (Course Enrollment, Mentor Approval)
├── assets/
│   └── uc-template.md                # Copy-ready Markdown template
├── README.md                         # This file
├── LICENSE                           # MIT
├── CHANGELOG.md                      # Version history
└── .gitignore
```

The skill follows the **progressive disclosure** pattern: only `SKILL.md` is always loaded into Claude's context. The `references/` and `assets/` files are loaded only when needed, keeping context usage efficient.

---

## Installation

### Option 1: Claude Code CLI — User-level skill (recommended)

Install once and the skill is available across **all your projects**.

**Step 1 — Clone the repository**

```bash
# Mac / Linux
git clone https://github.com/ba-zone/ba-zone-use-case-writer.git ~/.claude/skills/ba-zone-use-case-writer

# Windows (PowerShell)
git clone https://github.com/ba-zone/ba-zone-use-case-writer.git "$env:USERPROFILE\.claude\skills\ba-zone-use-case-writer"
```

**Step 2 — Verify the structure**

After cloning, the skills directory should look like this:

```
~/.claude/skills/                          # Mac/Linux
%USERPROFILE%\.claude\skills\             # Windows
└── ba-zone-use-case-writer/
    ├── SKILL.md                          ← main entry point (loaded by Claude Code)
    ├── references/
    │   ├── template-guide.md
    │   ├── writing-style.md
    │   ├── quality-checklist.md
    │   └── examples-edtech.md
    └── assets/
        └── uc-template.md
```

**Step 3 — Use the skill in Claude Code**

Open Claude Code CLI (or VS Code / JetBrains extension) and type:

```
/use-case-writer
```

Or just describe what you need — Claude Code will detect and activate the skill automatically based on trigger phrases.

---

### Option 2: Claude Code CLI — Project-level skill

Install inside a specific project so only that project's Claude Code sessions load it.

```bash
# Mac / Linux — run from your project root
git clone https://github.com/ba-zone/ba-zone-use-case-writer.git .claude/skills/ba-zone-use-case-writer

# Windows (PowerShell) — run from your project root
git clone https://github.com/ba-zone/ba-zone-use-case-writer.git .claude\skills\ba-zone-use-case-writer
```

The `.claude/skills/` directory sits alongside your project's `.claude/settings.json`. Claude Code picks it up automatically on next launch within that project.

---

### Option 3: Upload to a Claude Project (claude.ai web)

For users who work on [claude.ai](https://claude.ai) instead of the CLI:

1. Download or clone this repository
2. In [claude.ai](https://claude.ai), go to **Projects → Create new project**
3. Upload all files (drag-and-drop the entire folder into the project knowledge base)
4. Start chatting — the skill activates automatically on relevant prompts

---

### Option 4: Use as a one-shot prompt template

Paste the contents of `SKILL.md` at the start of any Claude chat and say:
> "Follow this workflow whenever I ask you to write a use case."

---

### Skills directory paths — quick reference

| Platform | User-level (global) | Project-level |
|----------|---------------------|---------------|
| Mac / Linux | `~/.claude/skills/` | `.claude/skills/` (project root) |
| Windows | `%USERPROFILE%\.claude\skills\` | `.claude\skills\` (project root) |

> **Tip (Windows):** Open the skills folder quickly with `explorer "$env:USERPROFILE\.claude\skills"` in PowerShell.

---

## Usage

### Trigger phrases

**English**:
- "Write a use case for [feature]"
- "Draft a UC for [functionality]"
- "Split this feature into a UC list"
- "Review my UC"
- "Write the Normal Course for this UC"

**Vietnamese** (skill responds in Vietnamese, UC artifact in English):
- "Viết use case cho [tính năng]"
- "Viết UC cho chức năng này"
- "Tách feature này thành UC list"
- "Review UC này giúp tôi"
- "Đặc tả use case cho [tính năng]"

### Example interaction

```
User: Viết UC cho tính năng đặt lịch mentor 1-on-1

Claude:
[Step 1] Mode: A (write new from feature description).
[Step 2] Xác nhận scope:
  Primary actor: Learner (Digital School Premium subscriber)
  Goal: Book a 1-on-1 mentor session
  System boundary: BA Zone Platform

Scope confirmed ✅. Confirm để tiến hành Step 3 (sinh UC theo từng nhóm)?

User: yes

Claude:
[Group 1: Identification + Actor + Description]

| Use Case ID: | UC-MENTOR-01 |
| Use Case Name: | Book 1-on-1 mentor session |
| ...

Group 1 done. Confirm to proceed to preconditions, postconditions, priority, frequency?

[... continues section by section ...]
```

### The 4 workflow steps

```
Step 1: CLASSIFY INPUT     →  identify which of the 4 modes the user is in
Step 2: SCOPE THE UC       →  apply 4 scoping rules + coffee-break test
Step 3: WRITE THE UC       →  fill 13 fields, ONE SECTION GROUP AT A TIME
Step 4: VALIDATE           →  run 20-point checklist before handover
```

---

## The 13 fields covered

| Field | Purpose |
|-------|---------|
| Use Case ID | Unique identifier (e.g. UC-LEARN-01) |
| Use Case Name | Action verb + Object |
| History | Created By / Date, Last Updated By / Date |
| Actor | Primary + Secondary actors (specific roles) |
| Description | 2-3 sentences: WHY + WHAT + OUTCOME |
| Preconditions | Verifiable conditions before UC starts |
| Postconditions | System state after successful completion |
| Priority | High / Medium / Low with justification |
| Frequency of Use | Quantified (X times / time unit) |
| Normal Course | Numbered, alternating Actor / System steps |
| Alternative Courses | Different paths to success (AC.1, AC.2…) |
| Exceptions | Failure modes (EX.1, EX.2…) |
| Includes | Sub-UCs called for common functionality |
| Special Requirements | Non-functional requirements |
| Assumptions | Beliefs not yet verified |
| Notes and Issues | TBDs with owner + due date |

---

## The 20-point quality checklist

Every UC is validated before handover:

| Group | Items | What it checks |
|-------|-------|----------------|
| **A. Scope & Identification** | C1-C5 | Name format, goal level, ID uniqueness, single primary actor, system boundary |
| **B. Actor & Context** | C6-C8 | Specific actor role, complete description, quantified frequency |
| **C. Pre/Post Conditions** | C9-C11 | Verifiable preconditions, complete postconditions, no Pre/Assumption mix |
| **D. Normal Course** | C12-C15 | Numbered steps, Actor/System alternation, no embedded logic, complete flow |
| **E. Alternative & Exception** | C16-C18 | AC format, exception structure, common failure modes covered |
| **F. Completeness** | C19-C20 | Valid Includes, non-functional Special Requirements |

See [`references/quality-checklist.md`](references/quality-checklist.md) for full details.

---

## What this skill does NOT do

- ❌ **Agile User Stories** — use `ba-zone-user-story-ac-writer` for that
- ❌ **Full PRD / URD / SRS documents** — UC is one section, not the whole doc
- ❌ **UML Use Case Diagrams** — this skill produces text specs, not diagrams
- ❌ **Wireframes or UI mockups** — UC describes interaction, not visual design
- ❌ **Business Process Models** — BP covers multi-actor multi-system processes; UC is 1 actor + 1 system

---

## Examples included

Two complete, validated EdTech UCs ship with the skill in [`references/examples-edtech.md`](references/examples-edtech.md):

1. **UC-LEARN-01: Enroll in a Digital School course**
   - Learner-facing UC with payment integration and async LMS fallback
   - 9-step Normal Course, 2 Alternative Courses, 4 Exceptions
   - Demonstrates: voucher payment AC, capacity race condition, async retry on LMS failure

2. **UC-MENTOR-03: Approve learner 1-on-1 mentor session request**
   - Mentor-facing admin UC with concurrency, quota enforcement, and calendar integration
   - 10-step Normal Course, 2 Alternative Courses, 4 Exceptions
   - Demonstrates: concurrency conflict, quota exhaustion at approval time, calendar service degraded-mode handling

---

## References & inspiration

- **Alistair Cockburn**, *Writing Effective Use Cases* (Addison-Wesley, 2000)
- **Karl Wiegers & Joy Beatty**, *Software Requirements* (Microsoft Press, 3rd ed.)
- **IIBA**, *BABOK Guide v3* — Use Case and Scenarios technique
- **Ivar Jacobson**, *Object-Oriented Software Engineering* — origin of use case modeling

---

## Contributing

Contributions welcome! If you have:
- Additional UC examples from your domain (insurance, healthcare, e-commerce, EdTech…)
- New anti-patterns you've encountered in the field
- Improvements to the 20-point checklist
- Translations or localization notes

Please open a Pull Request or Issue. When contributing UC examples, ensure they pass the full 20-point checklist first.

---

## License

MIT License — see [LICENSE](LICENSE) for details.

**Attribution requirement**: Any redistribution of this repository, in whole or in part, must credit the original author: **Phúc NT / BA Zone / Digital School**. Removing or obscuring authorship information is not permitted under the terms of this license.

---

## Author

Developed by **Phúc NT** · [BA Zone](https://bazone.vn) · Digital School

This is intellectual property of **BA Zone**. You are free to use and fork this repository under the MIT License, provided you **keep the author attribution** (Phúc NT / BA Zone) in all redistributed copies.

*BA Zone · Digital School — Cộng đồng BA/PO Việt Nam*

---

## Tiếng Việt

> Một Claude AI skill giúp BA IT **xác định scope, phân tích và đặc tả Use Case** bằng Markdown tiếng Anh, theo chuẩn template 13 trường (phong cách Karl Wiegers / IIBA) và các best practice từ cuốn *Writing Effective Use Cases* của Alistair Cockburn.
>
> Phát triển bởi **Phúc NT** cho **BA Zone** — Cộng đồng Business Analyst & Product Owner Việt Nam.

[![Claude Skill](https://img.shields.io/badge/Claude-Skill-orange)](https://claude.ai)
[![License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)
[![Author](https://img.shields.io/badge/Author-Ph%C3%BAc%20NT-purple)](#)
[![BA Zone](https://img.shields.io/badge/BA-Zone-orange)](https://bazone.vn)
[![Output](https://img.shields.io/badge/Output-English%20Markdown-green)](#)
[![Template](https://img.shields.io/badge/Template-Karl%20Wiegers%20%2F%20IIBA-blue)](#)

---

## Tại sao cần skill này?

Viết đặc tả Use Case chất lượng cao khó hơn bạn nghĩ. BA thường vấp phải những lỗi sau:

- **Sai scope**: UC quá lớn (cả workflow) hoặc quá nhỏ (sub-function như "Xác minh OTP")
- **Actor mơ hồ**: dùng "User" thay vì role cụ thể như Học viên, Mentor, hay HR Manager
- **Logic nhúng vào Normal Course**: nhồi if/else và vòng lặp vào các bước
- **Thiếu failure mode**: chỉ viết happy path
- **Nhầm lẫn Precondition với Business Rule**

Skill này giúp bạn tuân thủ nguyên tắc bằng cách:

1. **Scope trước** — áp dụng coffee-break test, goal level và system boundary theo phương pháp Cockburn trước khi viết bất cứ điều gì
2. **Sinh tuần tự** — từng nhóm section, dừng để xác nhận nhằm phát hiện vấn đề sớm
3. **Validate bằng checklist 20 điểm** — mỗi UC đều được review trước khi bàn giao

---

## Tính năng

- ✅ **Output Markdown tiếng Anh** theo chuẩn template 13 trường
- ✅ **Workflow tuần tự** — 5 nhóm section, có cổng xác nhận giữa các nhóm
- ✅ **4 chế độ**: viết mới, tách feature thành UC list, chỉnh sửa UC hiện có, hoặc viết một section cụ thể
- ✅ **Quy tắc scope** theo Alistair Cockburn (coffee-break test, goal level, one-actor-one-goal-one-session, system boundary)
- ✅ **3 kỹ thuật nhận diện** để phân rã feature lớn: goal-driven, event-driven, CRUD-driven
- ✅ **Checklist chất lượng 20 điểm** chạy tự động trước khi bàn giao
- ✅ **Tương tác song ngữ** — chat bằng tiếng Việt hoặc tiếng Anh, artifact UC output bằng tiếng Anh
- ✅ **2 UC EdTech đầy đủ** kèm theo làm tham khảo (Đăng ký khóa học, Phê duyệt buổi Mentor)

---

## Cấu trúc repository

```
ba-zone-use-case-writer/
├── SKILL.md                          # Main workflow (loaded into Claude's context)
├── references/                       # Reference docs (loaded on demand)
│   ├── template-guide.md             # How to fill each of the 13 fields, with Digital School examples
│   ├── writing-style.md              # Active voice rules, numbering conventions, 10 anti-patterns
│   ├── quality-checklist.md          # 20-point validation checklist with pass/fail examples
│   └── examples-edtech.md            # 2 full EdTech UC examples (Course Enrollment, Mentor Approval)
├── assets/
│   └── uc-template.md                # Copy-ready Markdown template
├── README.md                         # This file
├── LICENSE                           # MIT
├── CHANGELOG.md                      # Version history
└── .gitignore
```

Skill tuân theo mô hình **progressive disclosure**: chỉ có `SKILL.md` được load vào context của Claude mọi lúc. Các file trong `references/` và `assets/` chỉ được load khi cần, giúp tiết kiệm context.

---

## Cài đặt

### Option 1: Claude Code CLI — Skill cấp người dùng (khuyên dùng)

Cài một lần, skill khả dụng trên **tất cả project** của bạn.

**Bước 1 — Clone repository**

```bash
# Mac / Linux
git clone https://github.com/ba-zone/ba-zone-use-case-writer.git ~/.claude/skills/ba-zone-use-case-writer

# Windows (PowerShell)
git clone https://github.com/ba-zone/ba-zone-use-case-writer.git "$env:USERPROFILE\.claude\skills\ba-zone-use-case-writer"
```

**Bước 2 — Kiểm tra cấu trúc**

Sau khi clone, thư mục skills phải có dạng sau:

```
~/.claude/skills/                          # Mac/Linux
%USERPROFILE%\.claude\skills\             # Windows
└── ba-zone-use-case-writer/
    ├── SKILL.md                          ← main entry point (loaded by Claude Code)
    ├── references/
    │   ├── template-guide.md
    │   ├── writing-style.md
    │   ├── quality-checklist.md
    │   └── examples-edtech.md
    └── assets/
        └── uc-template.md
```

**Bước 3 — Sử dụng skill trong Claude Code**

Mở Claude Code CLI (hoặc extension VS Code / JetBrains) và gõ:

```
/use-case-writer
```

Hoặc chỉ cần mô tả nhu cầu — Claude Code sẽ tự nhận diện và kích hoạt skill dựa trên trigger phrase.

---

### Option 2: Claude Code CLI — Skill cấp project

Cài vào một project cụ thể để chỉ phiên làm việc Claude Code của project đó mới load skill.

```bash
# Mac / Linux — chạy từ project root
git clone https://github.com/ba-zone/ba-zone-use-case-writer.git .claude/skills/ba-zone-use-case-writer

# Windows (PowerShell) — chạy từ project root
git clone https://github.com/ba-zone/ba-zone-use-case-writer.git .claude\skills\ba-zone-use-case-writer
```

Thư mục `.claude/skills/` nằm cùng cấp với `.claude/settings.json` của project. Claude Code tự nhận diện khi khởi động lại trong project đó.

---

### Option 3: Upload lên Claude Project (claude.ai web)

Dành cho người dùng [claude.ai](https://claude.ai) thay vì dùng CLI:

1. Tải về hoặc clone repository này
2. Trên [claude.ai](https://claude.ai), vào **Projects → Create new project**
3. Upload tất cả file (kéo thả toàn bộ thư mục vào knowledge base của project)
4. Bắt đầu chat — skill tự kích hoạt khi gặp prompt liên quan

---

### Option 4: Dùng như one-shot prompt template

Dán nội dung của `SKILL.md` vào đầu bất kỳ cuộc chat Claude nào và nói:
> "Hãy tuân theo workflow này mỗi khi tôi yêu cầu viết use case."

---

### Đường dẫn thư mục skills — tham khảo nhanh

| Nền tảng | Cấp người dùng (toàn cục) | Cấp project |
|----------|---------------------------|-------------|
| Mac / Linux | `~/.claude/skills/` | `.claude/skills/` (project root) |
| Windows | `%USERPROFILE%\.claude\skills\` | `.claude\skills\` (project root) |

> **Mẹo (Windows):** Mở nhanh thư mục skills bằng `explorer "$env:USERPROFILE\.claude\skills"` trong PowerShell.

---

## Cách sử dụng

### Trigger phrase

**Tiếng Anh**:
- "Write a use case for [feature]"
- "Draft a UC for [functionality]"
- "Split this feature into a UC list"
- "Review my UC"
- "Write the Normal Course for this UC"

**Tiếng Việt** (skill phản hồi bằng tiếng Việt, artifact UC output bằng tiếng Anh):
- "Viết use case cho [tính năng]"
- "Viết UC cho chức năng này"
- "Tách feature này thành UC list"
- "Review UC này giúp tôi"
- "Đặc tả use case cho [tính năng]"

### Ví dụ tương tác

```
User: Viết UC cho tính năng đặt lịch mentor 1-on-1

Claude:
[Step 1] Mode: A (write new from feature description).
[Step 2] Xác nhận scope:
  Primary actor: Learner (Digital School Premium subscriber)
  Goal: Book a 1-on-1 mentor session
  System boundary: BA Zone Platform

Scope confirmed ✅. Confirm để tiến hành Step 3 (sinh UC theo từng nhóm)?

User: yes

Claude:
[Group 1: Identification + Actor + Description]

| Use Case ID: | UC-MENTOR-01 |
| Use Case Name: | Book 1-on-1 mentor session |
| ...

Group 1 done. Confirm to proceed to preconditions, postconditions, priority, frequency?

[... continues section by section ...]
```

### 4 bước workflow

```
Step 1: CLASSIFY INPUT     →  identify which of the 4 modes the user is in
Step 2: SCOPE THE UC       →  apply 4 scoping rules + coffee-break test
Step 3: WRITE THE UC       →  fill 13 fields, ONE SECTION GROUP AT A TIME
Step 4: VALIDATE           →  run 20-point checklist before handover
```

---

## 13 trường bắt buộc

| Trường | Mục đích |
|--------|---------|
| Use Case ID | Mã định danh duy nhất (vd. UC-LEARN-01) |
| Use Case Name | Động từ hành động + Tân ngữ |
| History | Người tạo / Ngày tạo, Người cập nhật cuối / Ngày cập nhật |
| Actor | Primary actor + Secondary actor (role cụ thể) |
| Description | 2-3 câu: TẠI SAO + LÀM GÌ + KẾT QUẢ |
| Preconditions | Điều kiện có thể kiểm chứng trước khi UC bắt đầu |
| Postconditions | Trạng thái hệ thống sau khi hoàn thành thành công |
| Priority | High / Medium / Low kèm lý giải |
| Frequency of Use | Định lượng (X lần / đơn vị thời gian) |
| Normal Course | Các bước đánh số, xen kẽ Actor / System |
| Alternative Courses | Các nhánh dẫn đến thành công (AC.1, AC.2…) |
| Exceptions | Failure mode (EX.1, EX.2…) |
| Includes | Sub-UC được gọi cho chức năng dùng chung |
| Special Requirements | Yêu cầu phi chức năng |
| Assumptions | Giả định chưa được xác minh |
| Notes and Issues | TBD kèm người chịu trách nhiệm + ngày hạn |

---

## Checklist chất lượng 20 điểm

Mỗi UC đều được validate trước khi bàn giao:

| Nhóm | Điểm | Kiểm tra |
|------|------|----------|
| **A. Scope & Identification** | C1-C5 | Định dạng tên, goal level, mã ID duy nhất, single primary actor, system boundary |
| **B. Actor & Context** | C6-C8 | Role Actor cụ thể, Description đầy đủ, Frequency có định lượng |
| **C. Pre/Post Conditions** | C9-C11 | Precondition có thể kiểm chứng, Postcondition đầy đủ, không nhầm Pre với Assumption |
| **D. Normal Course** | C12-C15 | Bước được đánh số, xen kẽ Actor/System, không nhúng logic, luồng đầy đủ |
| **E. Alternative & Exception** | C16-C18 | Định dạng AC, cấu trúc Exception, bao phủ failure mode phổ biến |
| **F. Completeness** | C19-C20 | Includes hợp lệ, Special Requirements phi chức năng |

Xem [`references/quality-checklist.md`](references/quality-checklist.md) để biết chi tiết đầy đủ.

---

## Skill này KHÔNG làm

- ❌ **Agile User Story** — dùng `ba-zone-user-story-ac-writer` cho việc này
- ❌ **PRD / URD / SRS đầy đủ** — UC là một section, không phải toàn bộ tài liệu
- ❌ **UML Use Case Diagram** — skill này sinh đặc tả văn bản, không phải sơ đồ
- ❌ **Wireframe hay UI mockup** — UC mô tả tương tác, không phải thiết kế giao diện
- ❌ **Business Process Model** — BP bao phủ quy trình đa actor đa hệ thống; UC là 1 actor + 1 hệ thống

---

## Ví dụ đi kèm

Hai UC EdTech đầy đủ, đã validated, được đóng gói cùng skill trong [`references/examples-edtech.md`](references/examples-edtech.md):

1. **UC-LEARN-01: Enroll in a Digital School course**
   - UC phía Học viên, tích hợp thanh toán và xử lý LMS bất đồng bộ dự phòng
   - 9 bước Normal Course, 2 Alternative Course, 4 Exception
   - Minh họa: AC thanh toán bằng voucher, race condition về capacity, async retry khi LMS lỗi

2. **UC-MENTOR-03: Approve learner 1-on-1 mentor session request**
   - UC phía Mentor/admin với xử lý đồng thời, kiểm soát quota và tích hợp lịch
   - 10 bước Normal Course, 2 Alternative Course, 4 Exception
   - Minh họa: xung đột concurrency, quota cạn kiệt tại thời điểm phê duyệt, xử lý calendar service degraded

---

## Tài liệu tham khảo

- **Alistair Cockburn**, *Writing Effective Use Cases* (Addison-Wesley, 2000)
- **Karl Wiegers & Joy Beatty**, *Software Requirements* (Microsoft Press, lần xuất bản thứ 3)
- **IIBA**, *BABOK Guide v3* — Kỹ thuật Use Case and Scenarios
- **Ivar Jacobson**, *Object-Oriented Software Engineering* — nguồn gốc của use case modeling

---

## Đóng góp

Chào đón mọi đóng góp! Nếu bạn có:
- Thêm UC mẫu từ domain của bạn (bảo hiểm, y tế, e-commerce, EdTech…)
- Anti-pattern mới bạn gặp phải trong thực tế
- Cải tiến cho checklist 20 điểm
- Bản dịch hoặc ghi chú về localization

Vui lòng mở Pull Request hoặc Issue. Khi đóng góp UC mẫu, hãy đảm bảo chúng vượt qua checklist 20 điểm đầy đủ trước.

---

## Giấy phép

MIT License — xem [LICENSE](LICENSE) để biết chi tiết.

**Yêu cầu ghi công**: Mọi hành vi phân phối lại repository này, toàn bộ hoặc một phần, phải ghi công tác giả gốc: **Phúc NT / BA Zone / Digital School**. Việc xóa hoặc che giấu thông tin tác giả không được phép theo điều khoản của giấy phép này.

---

## Tác giả

Phát triển bởi **Phúc NT** · [BA Zone](https://bazone.vn) · Digital School

Đây là tài sản trí tuệ của **BA Zone**. Bạn được tự do sử dụng và fork repository này theo MIT License, với điều kiện **giữ nguyên thông tin tác giả** (Phúc NT / BA Zone) trong mọi bản phân phối lại.

*BA Zone · Digital School — Cộng đồng BA/PO Việt Nam*
