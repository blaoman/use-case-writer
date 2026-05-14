---
name: use-case-writer
description: Generate Use Case specifications in English Markdown following the IT BA standard 13-field template (Karl Wiegers / IIBA). Use whenever a BA needs to scope, analyze, document, refine, or review a Use Case. Triggers include "write a use case", "draft UC", "use case specification", "analyze UC scope", "split feature into use cases", "review my UC", "write normal course / alternative course / exceptions", "define actors", and Vietnamese equivalents like "viết use case", "viết UC", "đặc tả use case", "phân tích use case", "review UC". Also trigger when user pastes a feature/BRD/PRD and asks to turn it into UCs. Skill enforces Cockburn's guidelines (coffee-break test, goal levels) and runs a 20-point quality checklist. Output is English Markdown with 13 fields (Actor, Description, Pre/Postconditions, Priority, Frequency, Normal/Alternative Courses, Exceptions, Includes, Special Req, Assumptions, Notes). DO NOT use for Agile User Stories, PRD/URD/SRS, or UML diagrams.
author: Phúc NT @ BA Zone
source: https://github.com/ba-zone
---

# Use Case Writer — Skill for IT Business Analysts
> by **Phúc NT** · BA Zone · Digital School

This skill helps IT BAs **scope, analyze, and document Use Cases** in English Markdown following the standard 13-field template (Karl Wiegers / IIBA style), with best practices from Alistair Cockburn's "Writing Effective Use Cases" and the IIBA BABOK Guide.

Developed by **Phúc NT** as part of the **Digital School** training program by **BA Zone** — Vietnam's Business Analyst & Product Owner community.

## When to use this skill

Trigger this skill whenever the user needs to:
- Draft a new UC from a feature description, BRD, or PRD
- Refine or review an existing UC (completeness, correctness)
- Split a large feature into multiple smaller UCs (scope identification)
- Write a specific section: Normal Course, Alternative Course, Exceptions
- Validate a UC against the quality checklist

## Output rules (non-negotiable)

1. **Language**: English. Even if the user types in Vietnamese, generate the UC document in English. Use Vietnamese only when chatting with the user about the process.
2. **Format**: Markdown (`.md`). Use the 2-column table layout that mirrors the original template.
3. **Mode**: Sequential — generate section by section, **stop and wait for the user to confirm** before moving on. Never dump a full UC in one shot unless the user explicitly says "give me the full UC at once".

---

## Workflow: 4 Steps

```
Step 1: CLASSIFY INPUT     →  identify which mode the user is in
Step 2: SCOPE THE UC       →  apply 4 scoping rules + coffee-break test
Step 3: WRITE THE UC       →  fill the 13 fields ONE SECTION AT A TIME
Step 4: VALIDATE           →  run the 20-point checklist before handover
```

---

## Step 1: Classify input and pick a mode

Before writing anything, identify which mode the user is in:

| Mode | Signals | Action |
|------|---------|--------|
| **Mode A: Write new from feature** | User pastes a feature description, BRD, PRD, or says "write UC for feature X" | Go to Step 2 (scope) → Step 3 (write sequentially) |
| **Mode B: Split large feature into UC list** | User says "split into UC list", "how many UCs does this feature need", uploads a large PRD | Go deep on Step 2 (apply 3 identification techniques), output the **UC List first**, then ask the user which UC to write in detail |
| **Mode C: Refine / review existing UC** | User pastes an existing UC and asks "review this", "is it complete", "what's missing" | Skip Step 2, go directly to Step 4 (validate checklist) |
| **Mode D: Write a specific section** | User says "write the Normal Course for this UC", "add Exceptions" | Read the UC context, jump to the relevant part of Step 3 |

**Golden rule**: If input is vague (just one line), **ASK before writing** — never make things up. Ask at most 3 questions:
1. Who is the primary actor? (specific role / user class)
2. What is the actor's concrete goal in this UC?
3. Which system / module does this UC belong to?

Communicate with the user in their language (Vietnamese or English), but the UC artifact is always English.

---

## Step 2: Scope the Use Case

This is the **most important and most error-prone** part of UC writing. Read carefully.

### 2.1. Four scoping rules

**Rule 1 - Coffee-break test (Alistair Cockburn)**
After completing the UC, can the actor take a coffee break without feeling the task is unfinished? If NO → the UC is too low-level (sub-function), merge it. If YES → scope is right (user-goal level).

**Rule 2 - Goal Level (Cockburn's 3 levels)**
- **Summary level (cloud)**: UC spans multiple sessions. E.g. "Manage course enrollment lifecycle" → too high, DO NOT write as a single UC.
- **User-goal level (sea level)** ✅: 1 actor, 1 session, achieves 1 business goal. E.g. "Enroll in a Digital School course" → right level for a UC.
- **Sub-function level (fish)**: A small step inside another UC. E.g. "Verify OTP" → too low, treat as Includes inside another UC.

**Rule 3 - One Actor, One Goal, One Session**
Each UC should have EXACTLY: 1 primary actor + 1 business goal + completion in 1 continuous session. If you see 2 different goals → split into 2 UCs.

**Rule 4 - System Boundary**
A UC describes the **interaction** between actor and system, NOT the system's internals. Each step must be one of:
- Actor does something to the system (input)
- System responds to the actor (output)
If a step has neither actor nor UI → it's a design detail, not part of the UC.

### 2.2. Three techniques to identify UCs (for Mode B)

When splitting a large feature into a UC list:

**Technique 1: Goal-driven (top-down)**
List all goals for each actor → each goal = 1 candidate UC.

**Technique 2: Event-driven (external + internal triggers)**
- External events: user actions (click, submit, scheduled time)
- Internal events: system-triggered (cron job, batch process)
Each event produces a system response → candidate UC.

**Technique 3: CRUD-driven (data-centric)**
For each business entity (Learner, Course, Enrollment, Certificate…), check whether the system needs Create / Read / Update / Delete. Each = 1 candidate UC (you can merge R-U-D for the same entity if logic is similar).

### 2.3. Output of Step 2

**Mode A**: One sentence confirming scope, then ASK USER TO CONFIRM before moving to Step 3:
> "Scope confirmed: this UC is at user-goal level. Primary actor: [X]. Goal: [Y]. System boundary: [Z]. Confirm to proceed to Step 3?"

**Mode B**: A UC List table:
```
| UC ID | UC Name (verb + noun)              | Primary Actor    | Goal | Priority |
| UC-01 | Enroll in Digital School course    | Learner          | ...  | High     |
| UC-02 | Book 1-on-1 mentor session         | Learner          | ...  | High     |
| UC-03 | Approve learner KYC application    | BO Approver      | ...  | Medium   |
```
Then ask: "Which UC do you want me to write in detail first?"

---

## Step 3: Write the Use Case — section by section

**CRITICAL**: Generate ONE SECTION GROUP at a time, then **STOP and ask the user to confirm** before continuing. Do not dump the whole UC at once.

Read `references/template-guide.md` for detailed guidance on filling each field.
Read `references/writing-style.md` for writing conventions (active voice, numbering, anti-patterns).

### 3.1. The template (output structure)

```markdown
| **Use Case ID:**        | UC-XX-YY                                   |
| **Use Case Name:**      | [Action verb + noun]                       |
| **Created By:**         |          | **Last Updated By:**   |       |
| **Date Created:**       |          | **Date Last Updated:** |       |

| **Actor:**              | [Primary actor] / [Secondary actors]       |
| **Description:**        | [2-3 sentences: why + what + outcome]      |
| **Preconditions:**      | 1. ... 2. ...                              |
| **Postconditions:**     | 1. ... 2. ...                              |
| **Priority:**           | High / Medium / Low                        |
| **Frequency of Use:**   | [X times / unit time]                      |
| **Normal Course of Events:** | 1. Actor... 2. System... 3. ...       |
| **Alternative Courses:**| UC-XX-YY.AC.1: [name]                      |
| **Exceptions:**         | UC-XX-YY.EX.1: [name]                      |
| **Includes:**           | UC-AA-BB                                   |
| **Special Requirements:**| [Non-functional: perf, security…]         |
| **Assumptions:**        | 1. ...                                     |
| **Notes and Issues:**   | TBD-1: [open question] / Owner / Due       |
```

Copy-ready template lives in `assets/uc-template.md`.

### 3.2. Sequential generation — the 5 section groups

Generate **in this exact order**, pause and ask confirmation after each group:

> **Group 1 — Identification + Actor + Description**
> Output: Use Case ID, Name, History (Created By / Date), Actor, Description.
> Then say: *"Group 1 done. Confirm to proceed to preconditions, postconditions, priority, frequency?"*

> **Group 2 — Conditions + Priority + Frequency**
> Output: Preconditions, Postconditions, Priority, Frequency of Use.
> Then say: *"Group 2 done. Confirm to proceed to the Normal Course?"*

> **Group 3 — Normal Course of Events**
> Output: numbered, step-by-step happy path.
> Then say: *"Normal Course done. Confirm to proceed to Alternative Courses and Exceptions?"*

> **Group 4 — Alternative Courses + Exceptions**
> Output: AC.1, AC.2…, EX.1, EX.2…
> Then say: *"Group 4 done. Confirm to proceed to the final group (Includes, Special Req, Assumptions, Notes)?"*

> **Group 5 — Includes + Special Requirements + Assumptions + Notes and Issues**
> Output: the remaining fields.
> Then say: *"All sections done. Shall I run the 20-point quality validation now?"*

**If the user requests changes** to a previous group, apply them and reconfirm before continuing.

**If the user says "skip ahead"** or "give me everything at once", honor that — but warn briefly that sequential mode catches more issues.

### 3.3. CRITICAL field-filling rules (the most common mistakes)

**Use Case ID**: Format `UC-<module>-<seq>`, e.g. `UC-LEARN-01`. Hierarchical X.Y if you have UC groups.

**Use Case Name**: MUST be "**Verb + Object**" (active voice).
- ✅ "Enroll in Digital School course", "Book mentor session", "Issue course completion certificate"
- ❌ "Enrollment" (no verb), "Learner enrolls" (actor included), "Manage courses" (vague verb)

**Actor**: Distinguish:
- *Primary actor*: initiates the UC, benefits from the outcome
- *Secondary actor*: supporting system/person (payment gateway, OTP service, LMS)
Never write "User" — be specific (Learner, Mentor, BO Admin, HR Manager, Enterprise Partner…).

**Preconditions**: Conditions that **MUST be true** before the UC starts. Distinguish from business rules!
- ✅ "Learner has logged in and has an active Digital School subscription"
- ❌ "Learner is motivated to study" (motivation — not verifiable)

**Postconditions**: System state **AFTER** successful UC completion. Must be verifiable.
- ✅ "Enrollment record saved with status='Active'; learner gains access to all course materials"
- ❌ "Learner feels satisfied" (not verifiable)

**Normal Course of Events** (most important):
- Numbered list, one action per step
- Alternate Actor / System steps (subject must be explicit)
- Each step starts with a clear subject + active verb
- **NO embedded if/else, loops, or exceptions** — those go in Alternative/Exception sections
- Storytelling style: from trigger to goal achieved
- ✅ "1. Learner selects the course on the Digital School catalog.  2. System displays course details and enrollment options.  3. Learner clicks 'Enroll Now'."
- ❌ "1. If learner has voucher, enter code; otherwise proceed to payment…" (branching embedded)

**Alternative Courses**: Different paths that **still lead to success**. E.g. paying with enterprise voucher instead of personal wallet. Format `UC-XX.AC.N` + "At step Y of Normal Course, if [condition], execute the alternative: …"

**Exceptions**: Cases where **the goal fails** (errors, validation fails, timeouts). Format `UC-XX.EX.N`. Each exception needs: trigger condition + system response + final state.

**Includes**: List of sub-UCs "called" by this UC (common functionality). E.g. UC "Enroll in course" includes UC "Process payment".

**Special Requirements**: Non-functional requirements specific to this UC:
- Performance: "Course catalog page loads ≤ 2s for 5,000 concurrent learners"
- Security: "Payment data must be encrypted in transit (TLS 1.3)"
- Usability, Reliability, Compliance…

**Assumptions**: Things assumed during analysis. Different from Preconditions — a precondition is a hard requirement; an assumption is a belief that hasn't been verified.

**Notes and Issues**: List of TBDs with format `[TBD-N] | Owner | Due date | Resolution`.

---

## Step 4: Validate against the 20-point checklist

**ALWAYS run this checklist BEFORE handing over the UC.** If any item fails, fix it or flag it to the user.

Read `references/quality-checklist.md` for the full checklist with examples. The 20 items, grouped:

### Scope & Identification (5 items)
- [ ] **C1**: UC Name follows "verb + object", active voice
- [ ] **C2**: UC is at user-goal level (passes coffee-break test)
- [ ] **C3**: UC ID is unique and follows naming convention
- [ ] **C4**: Exactly 1 primary actor + 1 clear business goal
- [ ] **C5**: System boundary is clear (not mixed with other UCs)

### Actor & Context (3 items)
- [ ] **C6**: Actor is a specific role/class, not "User"
- [ ] **C7**: Description answers WHY (reason) + WHAT (action) + OUTCOME (result)
- [ ] **C8**: Frequency of Use is quantified (not "sometimes")

### Pre/Post Conditions (3 items)
- [ ] **C9**: Preconditions are verifiable (not disguised business rules)
- [ ] **C10**: Postconditions cover the success state and all system changes
- [ ] **C11**: Preconditions are not confused with Assumptions

### Normal Course (4 items)
- [ ] **C12**: Numbered list, one action per step
- [ ] **C13**: Alternates Actor / System with clear subjects
- [ ] **C14**: NO embedded if/else/loop in the Normal Course
- [ ] **C15**: Flow runs from trigger to postcondition (no dangling step)

### Alternative & Exception (3 items)
- [ ] **C16**: Each AC specifies "at step N" + condition
- [ ] **C17**: Each Exception has trigger + system response + final state
- [ ] **C18**: Common failure modes are covered (timeout, invalid input, network, permission denied, concurrency conflict)

### Completeness (2 items)
- [ ] **C19**: Includes (if any) point to existing UCs
- [ ] **C20**: Special Requirements don't duplicate functional requirements

**Validation output**: A `Item | Status | Note` table with ✅ ❌ ⚠️ markers.

---

## Output format details

- Always produce English Markdown
- Use the 2-column table layout that matches the original template
- Save final output as a `.md` file if the user wants a downloadable file; otherwise show inline in chat
- File naming convention: `<UC-ID>_<UC-Name-kebab>.md`, e.g. `UC-LEARN-01_enroll-digital-school-course.md`

---

## References

- `references/template-guide.md` - Detailed guidance for each field (with EdTech & Digital School examples)
- `references/writing-style.md` - Writing conventions (active voice, numbering, anti-patterns)
- `references/quality-checklist.md` - 20-point checklist with pass/fail examples
- `references/examples-edtech.md` - 2 complete EdTech UC examples (Course Enrollment, Mentor Session Approval)
- `assets/uc-template.md` - Copy-ready Markdown template

---

## Anti-patterns (ABSOLUTELY avoid)

1. **UC = UI flow**: Describing every button click and popup → that's a wireframe spec, not a UC
2. **UC = User Story**: A UC describes detailed interactions; a US is a one-liner "As a… I want… So that…"
3. **UC = Business Process**: A BP covers an entire business process (many people, many systems); a UC covers 1 actor + 1 system
4. **Vague verbs in UC Name**: "Manage", "Handle", "Process" — too generic. Use specific action verbs
5. **Mixing concerns**: Cramming enrollment, payment, notification into one giant UC → split using Includes
6. **Forgetting exceptions**: Writing only the happy path with no failure modes → insufficient for dev/QA
7. **Vague preconditions**: "System is ready" → meaningless. Must be verifiable

---
*Skill developed by **Phúc NT** · BA Zone · Digital School*  
*Please keep attribution intact when sharing or forking this repo.*
