# Use Case Writer · BA Zone

> A Claude AI skill that helps IT Business Analysts **scope, analyze, and document Use Cases** in English Markdown, following the industry-standard 13-field template (Karl Wiegers / IIBA style) with best practices from Alistair Cockburn's *Writing Effective Use Cases*.
>
> Developed by **Phúc NT** for the **Digital School** program · **BA Zone** — Vietnam's Business Analyst & Product Owner community.

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

### Option 1: Upload to a Claude Project (recommended)

1. Download or clone this repository
2. In [claude.ai](https://claude.ai), go to **Projects → Create new project**
3. Upload the entire `ba-zone-use-case-writer/` folder to the project knowledge base
4. Start chatting — the skill activates automatically on relevant prompts

### Option 2: Use as a prompt template

Paste the contents of `SKILL.md` at the start of a chat and tell Claude:
> "Follow this workflow whenever I ask you to write a use case."

### Option 3: Deploy to /mnt/skills/user/

If your environment supports the skills mount:
1. Copy the folder to `/mnt/skills/user/ba-zone-use-case-writer/`
2. Claude will detect and trigger the skill automatically

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
