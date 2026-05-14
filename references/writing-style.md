# Writing Style Guide

Compiled from Alistair Cockburn ("Writing Effective Use Cases") + IIBA BABOK + BA Zone practice in EdTech and enterprise software domains.

> Compiled by **Phúc NT** · BA Zone · Digital School

## Supreme principle: READABILITY FIRST

Cockburn's famous quote: "Write clearly. Readability is the most important thing."

A good UC is one where:
- Non-technical stakeholders can grasp the meaning
- Developers have enough to code from
- QA has enough to write test cases
- A new BA (or future Digital School grad) can update it when things change

---

## Rule 1: Active Voice + Present Tense

### Active voice
Use active sentences where the subject performs the action.

- ✅ "Learner clicks the **Enroll Now** button"
- ❌ "The **Enroll Now** button is clicked by the learner"

- ✅ "System saves the enrollment record to the database"
- ❌ "The enrollment record is saved to the database by the system"

### Present tense
Use simple present tense, avoid future/past.

- ✅ "System displays the course confirmation screen"
- ❌ "System will display the course confirmation screen"
- ❌ "System displayed the course confirmation screen"

---

## Rule 2: Clear subject — Subject + Verb + Object

Every step must start with a **specific subject**: an actor name or "System".

- ✅ "Learner selects a preferred mentor session slot"
- ❌ "Selects a preferred session slot" (no subject)

- ✅ "System validates the learner's remaining session quota"
- ❌ "Validates the remaining quota" (passive, unclear who's doing it)

---

## Rule 3: One step = one action

Each step in the Normal Course does exactly one thing. If you see "and" connecting different kinds of action → split the step.

- ✅ "3. Learner enters the destination account, preferred slot, and session topic." (same kind — filling a form)
- ❌ "3. Learner fills in the session topic and clicks Confirm." → split into 2 steps:
  - "3. Learner enters the session topic (max 500 characters)."
  - "4. Learner clicks the **Send Request** button."

**Why**: "Clicking Send Request" usually triggers system validation → it needs to be a separate step so an Exception "quota exceeded" can be attached to it.

---

## Rule 4: Avoid vague verbs

Vague verbs = verbs that don't convey a specific action.

| ❌ Vague | ✅ Specific |
|---------|------------|
| Manage | Create / Update / Archive / View |
| Handle | Validate / Process / Reject / Escalate |
| Do | Submit / Approve / Assign / Generate |
| Make | Issue / Build / Render / Compute |
| Get | Retrieve / Fetch / Query / Download |
| Use | Apply / Invoke / Execute / Redeem |
| Take care of | Specific verb |

**Apply this to both the UC Name and the step text.**

---

## Rule 5: Avoid implementation details

A UC describes **WHAT** (the action), not **HOW** (the mechanism). Leave HOW for the design phase.

- ❌ "System calls POST /api/v1/enrollments with header Authorization Bearer {token}, body {course_id, learner_id}…"
- ✅ "System creates the enrollment record in the LMS"

- ❌ "System inserts a row into the tbl_enrollments table with fields: enroll_id, course_id, learner_id, created_at…"
- ✅ "System saves the enrollment to the database"

- ❌ "System renders the <EnrollmentSuccessModal> React component with prop courseTitle='BA Fundamentals'…"
- ✅ "System displays the Enrollment Confirmed screen with the course name and access link"

**Exception**: If the UC is specifically an integration spec, it can be more detailed — but still use business language.

---

## Rule 6: Consistent numbering

### Normal Course
Numbered list starting at 1.

### Alternative Course
Sub-numbering by original step + letter:
- AC at step 5 → step 5a, 5b, 5c
- After the AC, state "continue from step N of the Normal Course"

### Exception ID
Format: `UC-XX.EX.N` (numbered independently, not tied to a step)

### Pre/Postconditions
Numbered list starting at 1.

---

## Rule 7: Naming UI elements

When mentioning a UI element in a step, use bold and the actual on-screen label:

- ✅ "Learner clicks the **Enroll Now** button"
- ✅ "System displays the **Order Summary** screen"
- ✅ "Learner selects **Enterprise Voucher** from the payment method dropdown"

Reason: Easy to trace back to wireframes/mockups during design handoff.

---

## Rule 8: Avoid vague words

| ❌ Vague | ✅ Specific |
|---------|------------|
| In some cases | When condition X occurs |
| May / can | When [condition], system [action] |
| Sometimes | X% of the time / Y times per Z |
| If needed | When [specific trigger] |
| Valid | Meets the criteria: … (list them) |
| Appropriate | Per BA Zone policy [reference] |
| Quickly | Within X seconds |
| User | Learner / Mentor / BO Admin / HR Manager |

---

## Rule 9: Don't embed business rules in steps

A Normal Course step describes **flow**. Business rules (validation rules, limits, business logic) should:
- Reference Special Requirements by rule ID
- Or live in a separate Business Rule document (BR-XX-YY)

- ❌ "5. System validates: session topic must be ≤ 500 chars, learner must have ≥ 1 unused quota, slot must be ≥ 2 hours in the future, mentor must not be on leave…"
- ✅ "5. System validates the session request according to business rule BR-MENTOR-001."
  - (Then list BR-MENTOR-001 in Special Requirements or a separate BR document)

---

## Rule 10: Length guidelines

- **UC Name**: 3-7 words
- **Description**: 2-4 sentences, ~50-100 words
- **Normal Course**: 5-15 steps (usually 7-10 for Digital School UCs)
- **Each step**: 1 sentence, max 2 sentences, < 30 words
- **Alternative Courses**: 1-5 ACs per UC (more → consider splitting the UC)
- **Exceptions**: 3-7 for a typical UC
- **Total UC document**: 2-5 A4 pages

If you exceed the guideline:
- UC too long → split via Includes
- Too many ACs/EXs → review the scope, the UC might be carrying too much

---

## Rule 11: Consistency across the project

Be consistent across the whole document set:
- Actor names (don't switch between "Learner", "Student", "User", "Participant")
- System component names (LMS, Learning Management System, Moodle → pick one)
- Screen/menu names (must match the wireframe or product spec)
- Naming convention for UC IDs

Tip: Maintain a **Glossary** at the front of the document set. For Digital School, agree upfront: is it "Learner" or "Student"? "Mentor" or "Instructor"?

---

## Rule 12: Internationalization

If the Digital School platform has i18n requirements:
- Screen/button names in the UC can use keys instead of hard-coded text
- E.g. replace "clicks the **Enroll Now** button" with "clicks the {btn.enroll_now} button"
- For most BA Zone UC specs, plain English labels are fine

---

## Anti-patterns — the 10 most common mistakes

### 1. UC is a pixel-by-pixel UI spec
❌ "System displays a modal with a blue #1E88E5 header 'Enrollment Confirmed', a checkmark icon, and course thumbnail image on the left..."
→ That's a wireframe annotation. A UC says: "System displays the Enrollment Confirmed screen with the course name and a Go to Course button."

### 2. Mixing actor and system in one step
❌ "3. Learner selects the slot and system validates quota."
→ Split into 2 steps.

### 3. Skipping system response
❌ "1. Learner clicks Enroll Now. 2. Learner enters payment info. 3. Learner confirms."
→ System responses between steps are missing. A UC must show DIALOG actor ↔ system.

### 4. Embedded conditional logic
❌ "5. If the learner has a Premium subscription, system allows mentor selection; otherwise only free-tier mentors are shown."
→ Split into Normal Course (default case) + AC (Premium path) or Exception (unauthorized access).

### 5. Vague trigger
❌ "When the learner wants to get a certificate, they..."
→ Be specific: "When the learner navigates to the **Certificates** tab after completing the course..."

### 6. Postcondition is an action instead of a state
❌ "System sends a certificate to the learner" (action)
→ "A certificate email has been delivered to the learner's registered email address" (state) ← verifiable

### 7. UC with 2 primary actors
❌ Primary: Learner + HR Manager (both initiating the UC)
→ Split into 2 UCs: one for self-enrollment, one for HR-assigned enrollment.

### 8. Vague "System processes"
❌ "5. System processes the enrollment."
→ Be specific: "System creates the enrollment record in the LMS and grants the learner access to all published lessons."

### 9. Repeating the Description in the Normal Course
If the Description already states the full flow, don't copy it into the Normal Course. The Description is a 2-3 sentence summary; the Normal Course is the detailed step-by-step.

### 10. Forgetting failure modes
A UC with only a Normal Course + 1 generic "error" Exception → not enough.
For Digital School UCs, always cover: payment failures, quota exhaustion, external service timeouts, concurrency conflicts (two learners grabbing the last slot), and permission/role mismatches.

---
*Compiled by **Phúc NT** · BA Zone · Digital School*  
*Please credit the source when sharing or adapting this guide.*
