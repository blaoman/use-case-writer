# Template Guide — How to Fill Each Field

Detailed guidance for filling each of the 13 fields, with pass/fail examples in the EdTech & Digital School domain.

Compiled by **Phúc NT** · BA Zone · Digital School

## Table of Contents
1. [Use Case ID](#1-use-case-id)
2. [Use Case Name](#2-use-case-name)
3. [Use Case History](#3-use-case-history)
4. [Actor](#4-actor)
5. [Description](#5-description)
6. [Preconditions](#6-preconditions)
7. [Postconditions](#7-postconditions)
8. [Priority](#8-priority)
9. [Frequency of Use](#9-frequency-of-use)
10. [Normal Course of Events](#10-normal-course-of-events)
11. [Alternative Courses](#11-alternative-courses)
12. [Exceptions](#12-exceptions)
13. [Includes](#13-includes)
14. [Special Requirements](#14-special-requirements)
15. [Assumptions](#15-assumptions)
16. [Notes and Issues](#16-notes-and-issues)

---

## 1. Use Case ID

**Purpose**: Unique identifier so requirements can be traced back to the UC.

**Rules**:
- Format: `UC-<module>-<sequence>` or `UC-X.Y` (hierarchical)
- Use a consistent naming convention across the project
- For related UC groups, use X.Y (e.g. UC-3.1, UC-3.2 belong to the "Enrollment" group)
- Pad the sequence to 2-3 digits: `UC-LEARN-01`, `UC-MENTOR-003`

**Good examples**:
- `UC-LEARN-01` (Enrollment module, UC #1)
- `UC-MENTOR-03` (Mentoring module, UC #3)
- `UC-3.2` (hierarchical, 2nd sub-UC of group 3)

**Bad examples**:
- `UC1` (no scheme)
- `UseCase_CourseEnrollment` (mixes name into ID — hard to maintain when name changes)

---

## 2. Use Case Name

**Purpose**: Short label describing the UC's goal.

**CRITICAL rules**:
- MUST follow **"Action verb + Object"** form
- 3-7 words, not too long
- DO NOT start with the actor name
- DO NOT use vague verbs ("manage", "handle", "process", "do")
- Reflects the actor's goal, not the implementation

**Pattern**: `<Verb> <Direct Object> [<modifier>]`

**Good examples** (Digital School / BA Zone):
- ✅ "Enroll in Digital School course"
- ✅ "Book 1-on-1 mentor session"
- ✅ "Issue course completion certificate"
- ✅ "Approve learner KYC application"
- ✅ "Assign enterprise license to employee"

**Bad examples → how to fix**:
- ❌ "Enrollment" → ✅ "Enroll in course"
- ❌ "Learner books session" (actor included) → ✅ "Book mentor session"
- ❌ "Manage learning path" (vague verb) → split into "Create learning path", "Update learning path", "Archive learning path"
- ❌ "Certificate is issued" (passive voice) → ✅ "Issue completion certificate"

---

## 3. Use Case History

**Purpose**: Audit trail (Created By, Date Created, Last Updated By, Date Last Updated).

**Rules**:
- Created By: full name + role (e.g. "Phúc NT - BA Zone")
- Date Created: YYYY-MM-DD format
- Last Updated By + Date Last Updated: update on every edit
- If unknown, use the placeholder `<TBD>` instead of leaving blank

---

## 4. Actor

**Purpose**: Identify who/what interacts with the system.

**Actor types**:
- **Primary actor**: Initiates the UC, benefits from the outcome
- **Secondary actor**: Supporting system/person (payment gateway, LMS, calendar service)
- **Off-stage stakeholder**: Has interest but doesn't interact directly (regulators, auditors) — usually NOT listed in the Actor field

**Rules**:
- The primary actor MUST be a specific role/class — never write "User" generically
- A UC should have 1 primary actor (rarely 2+)
- If there's a secondary actor, label it clearly

**Good examples** (Digital School / BA Zone):
- ✅ "Primary: Learner (Digital School Premium subscriber, email verified)"
- ✅ "Primary: Mentor (BA Zone certified, active account)"
- ✅ "Primary: HR Manager (Enterprise Partner with license admin rights)"
- ✅ "Primary: BO Admin; Secondary: AML Service, Notification Service"

**Bad examples**:
- ❌ "User" (too generic)
- ❌ "Student" (ambiguous — is it the same as Learner?)
- ❌ "System" (the system is the target of the UC, not an actor)

---

## 5. Description

**Purpose**: Summarize the UC in 2-3 sentences so readers grasp what it's about quickly.

**Rules — must answer 3 questions**:
1. **WHY**: The reason/trigger that leads to this UC
2. **WHAT**: What the actor does with the system
3. **OUTCOME**: The final result (new system state / value for the actor)

**Pattern**: `[When/To] <trigger/reason>, <actor> <action> in order to <outcome>.`

**Good example** (Digital School):
> "When a learner completes all lessons and passes the final assessment of a Digital School course, the learner navigates to the Certificate section to download their completion certificate. The UC ends when a personalized certificate PDF is generated with a unique verification code, downloaded by the learner, and recorded in the Certificates table."

**Bad examples**:
> ❌ "This UC is about certificates." (too short, missing WHY and OUTCOME)
> ❌ "The certificate module has these steps: request, generate, download…" (describes flow, not a description)

---

## 6. Preconditions

**Purpose**: List conditions that MUST be true before the UC can start.

**CRITICAL rules**:
- Every precondition must be **verifiable** (boolean check)
- Number them: 1, 2, 3…
- Distinguish from Business Rules:
  - Precondition: checked BEFORE the UC starts
  - Business Rule: applied DURING the UC's flow
- Distinguish from Assumptions:
  - Precondition: REQUIRED for the UC to run
  - Assumption: BELIEVED to be true but not verified

**Good examples** (Digital School):
```
1. Learner has logged in to BA Zone with a verified email address
2. Learner has completed 100% of the course lessons (progress = 100%)
3. Learner has passed the final assessment with a score ≥ 70%
4. Certificate generation service is available
```

**Bad examples**:
- ❌ "System is operating" (too generic, not verifiable)
- ❌ "Learner wants a certificate" (motivation, not a condition)
- ❌ "Learner must have a valid payment method" (belongs in a payment UC, not a certificate UC)

---

## 7. Postconditions

**Purpose**: Describe the system state AFTER successful UC completion.

**Rules**:
- Verifiable (can be checked via DB query / API response)
- Cover all kinds of changes:
  - Data state (new record, status change)
  - User-facing state (notification sent, file available for download)
  - External system state (API call succeeded, calendar blocked)
- Number them

**Important**: A postcondition is a **state**, not an **action**.
- ✅ State: "Certificate record is saved with a unique verification code"
- ❌ Action: "System saves the certificate record" (this is a step in the Normal Course)

**Good example** (Digital School):
```
1. Certificate record is created in the Certificates table with a unique verification code (format: CERT-BAZONE-YYYY-NNNNN)
2. Certificate PDF is generated and stored in cloud storage, accessible via a permanent URL
3. Learner's profile displays the certificate badge for the completed course
4. Certificate verification page is publicly accessible at verify.bazone.vn using the unique code
5. Achievement notification is sent to the learner's email and in-app notification center
```

---

## 8. Priority

**Purpose**: Define the implementation priority of the UC.

**Common schemes**:
- **MoSCoW**: Must / Should / Could / Won't
- **3-level**: High / Medium / Low

**Rules**:
- Use the SAME scheme as the project's SRS / PRD
- Justify (one sentence explaining why priority X)

**Good examples** (Digital School):
- "High — Core feature; directly tied to learner retention and completion rate metrics"
- "Medium — Enhances enterprise partner experience; planned for phase 2"

---

## 9. Frequency of Use

**Purpose**: Estimate how often the UC will be executed → input for performance/capacity planning.

**Rules**:
- Use SPECIFIC NUMBERS (not "occasionally", "frequently")
- Suitable time units: per second, per hour, per day, per month
- If there are peak times, state them explicitly

**Good examples** (Digital School):
- "~500 enrollments/day; peak ~100/hour during campaign launches and new course releases"
- "~15 session requests/day per mentor; system-wide ~300/day across 20 active mentors; peak Sunday evenings"

**Bad examples**:
- ❌ "Frequent"
- ❌ "Daily" (no volume)

---

## 10. Normal Course of Events

**Purpose**: Describe the happy path — steps from trigger to goal achieved.

**CRITICAL rules** (this is the most error-prone field):

### 10.1. Format
- Numbered list (1, 2, 3…)
- Each step: one single action
- Start with a clear subject (Actor / System)
- Active voice + present tense
- Short steps, 1-2 sentences each

### 10.2. Alternate Actor / System
Typical pattern: Actor → System → Actor → System…
- Odd steps: actor input
- Even steps: system response

### 10.3. DO NOT embed:
- ❌ If/else → move to Alternative Course
- ❌ Loops → use "Steps X-Y repeat until Z"
- ❌ Exceptions → move to Exceptions
- ❌ Internal system logic → that's design, not a UC

### 10.4. Start and end
- Step 1: Trigger (the event that activates the UC)
- Final step: Goal achieved (postcondition met)

**Good example** (Digital School — book a mentor session):
```
1. Learner navigates to the "My Mentors" section and selects a mentor profile.
2. System displays the mentor's profile: bio, expertise, average rating, and available time slots for the next 14 days.
3. Learner selects a preferred date and time slot.
4. Learner enters a topic or question for the session (max 500 characters) and clicks "Send Request".
5. System validates that the learner has at least 1 unused session quota in their current subscription.
6. System creates a session request with status='Pending_Mentor_Review' and sends a notification to the mentor.
7. System displays a confirmation screen: "Request sent! Your mentor will respond within 24 hours."
8. System invokes UC-NOTI-03 to send a confirmation email to the learner.
```

**Bad examples → how to fix**:
- ❌ "1. If the learner has a Premium subscription, they can select any mentor; otherwise they can only select from the free tier…" → Move the branching to an Alternative Course
- ❌ "3. System validates. If invalid, show error. If valid, continue." → Validation-pass continues in flow; validation-fail goes into an Exception
- ❌ "5. System calls POST /api/v1/sessions with body {learner_id, mentor_id, slot_id}" → Too technical. Say: "System creates the session request in the booking system"

---

## 11. Alternative Courses

**Purpose**: A DIFFERENT path that still leads to the goal (still success), just a different route.

**Rules**:
- ID format: `UC-XX.AC.N` (AC = Alternative Course)
- Each AC starts with: "At step Y of the Normal Course, if [condition], execute the alternative: …"
- After the AC, state explicitly which step of the Normal Course to continue from

**Good example** (Digital School):
```
UC-LEARN-01.AC.1: Enroll using an enterprise voucher
At step 5 of the Normal Course, if the learner selects "Enterprise Voucher" as the payment method:
5a. System displays a voucher code input field.
5b. Learner enters the code and clicks "Apply".
5c. System validates the voucher (expiry, applicability, remaining uses).
5d. System updates the total amount to 0 VND → continue from step 7 of the Normal Course (no payment gateway call).
```

---

## 12. Exceptions

**Purpose**: Cases where the UC FAILS (goal is not achieved).

**Rules**:
- ID format: `UC-XX.EX.N` (EX = Exception)
- Each exception needs 3 parts:
  1. **Trigger condition**: When the exception occurs
  2. **System response**: What the system does
  3. **Final state**: The end state (rollback? partial? log?)

**Common failure modes to check** (don't forget):
- Validation errors (wrong format, missing field)
- Business rule violations (quota exceeded, course at capacity)
- External service failures (payment gateway timeout, LMS unavailable)
- Network/connectivity issues
- Permission denied / authorization failure
- Concurrency conflict (slot booked by another learner at the same time)
- Session timeout (mentor idle too long on the detail view)

**Good example** (Digital School):
```
UC-LEARN-01.EX.2: Course reaches full capacity between page load and enrollment
Trigger: At step 7, LMS returns CAPACITY_EXCEEDED because another learner filled the last slot milliseconds earlier.
Response: System displays "Sorry, this course just reached full capacity. Join the waitlist to be notified when a slot opens."
Final state: Payment is refunded automatically within 1 business day. No enrollment record is created. Learner is offered the waitlist option.
```

---

## 13. Includes

**Purpose**: Reuse common functionality across UCs.

**Rules**:
- List sub-UCs "called" by this UC (UML «include» semantics)
- The sub-UC must exist (have its own spec)
- DO NOT use Includes just to group minor steps — only for logic reused in other UCs

**Good example** (Digital School):
```
- UC-PAY-01: Process payment (called at step 6 of the Normal Course)
- UC-NOTI-01: Send enrollment notification (called at step 9)
```

---

## 14. Special Requirements

**Purpose**: Non-functional requirements specific to this UC.

**Categories to cover**:
- **Performance**: Response time, throughput, concurrent users
- **Security**: Authentication, encryption, data privacy
- **Usability**: Accessibility, mobile-first requirements
- **Reliability**: Uptime, async fallback strategy
- **Compliance**: Regulatory requirements (VAT invoicing, data retention)

**Rule**: DO NOT duplicate functional requirements — only list non-functional.

**Good example** (Digital School):
```
- Performance: Course catalog page loads ≤ 2s under 5,000 concurrent learners
- Security: Payment card data never stored on BA Zone servers; all card processing via PCI-DSS certified gateway
- Reliability: If LMS is unavailable during enrollment, payment must not be rolled back — retry asynchronously up to 30 min
- Compliance: Issue VAT invoice for all transactions ≥ 200,000 VND (Vietnamese tax law)
```

---

## 15. Assumptions

**Purpose**: Things assumed during analysis that haven't been verified.

**Difference vs Precondition**:
- Precondition: MUST BE TRUE, system can verify
- Assumption: BELIEVED TO BE TRUE, not required to verify

**Good example** (Digital School):
```
1. Learner's email address is verified and active — welcome emails will not bounce
2. Payment Gateway SLA is ≥ 99.5% uptime during business hours
3. Enterprise vouchers are pre-loaded by BA Zone's ops team before distribution to partners
4. LMS access provisioning completes synchronously in < 3s under normal load
```

---

## 16. Notes and Issues

**Purpose**: Open questions, TBDs, follow-up items.

**Format**:
```
[TBD-N] | Owner | Due Date | Resolution
```

**Good example** (Digital School):
```
- [TBD-1] Should learners be able to gift a course enrollment to another BA Zone user? | Owner: Product Team | Due: 2026-06-01 | Resolution: TBD — deferred to phase 2
- [TBD-2] What is the refund policy if a learner requests a refund within 7 days? | Owner: Phúc NT - BA Zone | Due: 2026-05-25 | Resolution: TBD
- [NOTE] Welcome email template must align with current Digital School brand guidelines — coordinate with Marketing team
```

---
*Compiled by **Phúc NT** · BA Zone · Digital School*  
*Please credit the source when sharing or adapting this guide.*
