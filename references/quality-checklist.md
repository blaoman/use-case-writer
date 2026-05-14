# Quality Checklist — 20 Points to Validate a Use Case

Run this checklist BEFORE handing over a UC. Each item has: definition, how to check, pass/fail examples.

> Compiled by **Phúc NT** · BA Zone · Digital School

## How to use

1. After writing the UC, walk through items C1-C20
2. Mark Status: ✅ Pass / ❌ Fail / ⚠️ Needs review
3. If Fail → fix it or flag it to the user
4. Output a summary table at the end

```
| Item | Status | Note |
| C1   | ✅     | UC Name "Enroll in Digital School course" follows the format |
| C2   | ⚠️     | UC could be split further — confirm with PO |
| ...  | ...    | ... |
```

---

## GROUP A: Scope & Identification (C1-C5)

### C1. UC Name follows "verb + object", active voice
**Definition**: UC Name starts with an active verb + an object noun, with no actor name embedded.

**How to check**: Parse the UC Name → identify the leading verb → verify it's an action verb.

**Pass**: "Enroll in Digital School course", "Approve mentor session request", "Issue completion certificate"
**Fail**: "Enrollment" (no verb), "Learner books session" (actor included), "Manage courses" (vague verb)

---

### C2. UC is at user-goal level (passes the coffee-break test)
**Definition**: After completing the UC, the actor can stop and take a break — the goal is achieved.

**How to check**: Read the Postconditions → ask yourself "Is this a business-meaningful result?"
- If the result is just a sub-step (e.g. "OTP is verified") → UC is too small
- If the result spans multiple sessions → UC is too large

**Pass**:
- "Enroll in Digital School course" → postcondition: enrollment active, learner has course access
- "Book mentor session" → postcondition: session request submitted, mentor notified

**Fail**:
- "Verify OTP" (too small — just a sub-step of another UC) → should be an Includes
- "Manage entire learner lifecycle" (too large — spans many sessions) → split into many UCs

---

### C3. UC ID is unique and follows naming convention
**Definition**: ID is unique in the project and matches the standard format.

**How to check**:
- Check the master UC list — is the ID unique?
- Does the format match `UC-<module>-<seq>`?

**Pass**: "UC-LEARN-01" (unique, correct format), "UC-MENTOR-03"
**Fail**: "UC1" (no module), "UseCase_CourseEnroll" (name embedded)

---

### C4. Exactly 1 primary actor + clear business goal
**Definition**: One UC has 1 primary actor (the initiator) and 1 specific goal.

**How to check**:
- Actor field → is there "Primary: [X]"?
- Description → does it state the goal clearly?
- If you see 2 primary actors → flag for splitting

**Pass**: Primary: Learner. Goal: enroll in a Digital School course and gain immediate access to materials.
**Fail**: Primary: Learner + HR Manager (2 actors). → Split: "Learner self-enrolls" and "HR Manager assigns course to employee" as 2 UCs.

---

### C5. System boundary is clear
**Definition**: The UC describes interaction with one specific system, not multiple systems mixed together.

**How to check**: Read the Normal Course → do the "System..." steps consistently refer to one system?

**Pass**: All steps refer to "BA Zone Platform". LMS and Payment Gateway are secondary actors.
**Fail**: Mixing BA Zone web platform + mobile app + third-party LMS API as if they were one system. → Split by system boundary or clarify primary system.

---

## GROUP B: Actor & Context (C6-C8)

### C6. Actor is a specific role/class
**How to check**: Is the actor a specific role/class rather than "User"?

**Pass**: "Learner (Digital School Premium subscriber)", "Mentor (BA Zone certified, active account)"
**Fail**: "User", "Person", "Actor 1"

---

### C7. Description answers WHY + WHAT + OUTCOME
**How to check**: Read the Description → check that all 3 elements are present.

**Pass**:
"When a learner completes all lessons and passes the final assessment [WHY], the learner navigates to the Certificate section to request a completion certificate [WHAT]. The UC ends when a personalized certificate PDF is generated with a unique verification code and emailed to the learner [OUTCOME]."

**Fail**: "This UC is about issuing certificates." (missing WHY and OUTCOME)

---

### C8. Frequency of Use is quantified
**How to check**: Does the Frequency field contain a NUMBER?

**Pass**: "~500 enrollments/day platform-wide; peak ~100/hour during promotional campaigns"
**Fail**: "Frequent", "Often during course launches" (no volume)

⚠️ Acceptable: "TBD — awaiting analytics data from ops team" + logged in Notes as [TBD-N]

---

## GROUP C: Pre/Post Conditions (C9-C11)

### C9. Preconditions are verifiable
**How to check**: Can each precondition be verified by a query / boolean test?

**Pass**: "Learner has completed 100% of course lessons (progress = 100%)" (DB query), "Payment Gateway is available" (health check)
**Fail**: "Learner is motivated to learn" (motivation — not verifiable), "System is ready" (too vague)

---

### C10. Postconditions cover the success state + all changes
**How to check**: Do the postconditions describe all changes after the UC runs?
- Data changes (which records, which fields)
- External state (notification sent, calendar blocked, file generated)
- User-visible state (new screen, badge unlocked)

**Pass**:
```
1. Enrollment record created with status='Active'
2. Learner granted access to all published lessons
3. Payment transaction saved with status='Completed'
4. Welcome email + in-app notification sent within 60s
5. Course enrollment count incremented by 1
```

**Fail**: Only "Enrollment succeeded" → missing all state detail.

---

### C11. Preconditions are not confused with Assumptions
**How to check**: Distinguish:
- Precondition: MUST BE TRUE, system can check
- Assumption: BELIEVED to be true, not verified

**Common Digital School mistake**: Putting "Learner has basic computer literacy" in Precondition → WRONG, this is an Assumption. The system cannot check it.

---

## GROUP D: Normal Course (C12-C15)

### C12. Numbered list, one action per step
**How to check**: Does each step:
- Start with a number (1., 2., 3...)
- Contain only one main action
- Avoid "and" connecting two different-kind actions

**Pass**: "3. Learner enters the session topic, preferred date, and time slot." (same kind — input fields)
**Fail**: "3. Learner enters the topic and clicks Send and waits for confirmation." (3 actions in one step)

---

### C13. Alternates Actor / System with clear subjects
**How to check**: Read the steps — is there an alternating Actor/System pattern?

**Pass**:
```
1. Learner clicks Enroll Now              ← Actor
2. System displays the Order Summary      ← System
3. Learner selects a payment method       ← Actor
4. Learner clicks Proceed to Payment      ← Actor
5. System invokes the Payment Gateway     ← System
```
(OK to have 2 consecutive Actor steps when both are input — still clear)

**Fail**: Only "Learner does X, then Y, then Z" with no system response anywhere.

---

### C14. NO embedded if/else/loop in the Normal Course
**How to check**: Search the Normal Course for "if", "in case", "otherwise" → flag.

**Pass**:
```
5. System validates the learner's remaining session quota.
6. System creates the session request with status='Pending_Mentor_Review'.
```

**Fail**:
```
5. If the learner has a Premium subscription, system shows all mentors; if Free, system shows only free-tier mentors; if quota is 0, system blocks the action.
```
→ Split into: Normal Course (default Premium flow) + AC (Free tier) + Exception (quota exhausted).

---

### C15. Flow runs from trigger to postcondition
**How to check**:
- Does step 1 match the trigger in the Description?
- Does the final step achieve the postcondition?
- Are there any "dangling" steps?

**Pass**: Step 1 "Learner clicks Enroll Now" (trigger) → step 9 "System sends welcome notification" (postcondition achieved).
**Fail**: Final step is "System saves enrollment" but postcondition says "Welcome notification is sent" → flow is incomplete.

---

## GROUP E: Alternative & Exception (C16-C18)

### C16. Each AC specifies "at step N" + condition
**How to check**: Does each Alternative Course have:
- ID format `UC-XX.AC.N`
- Opening sentence: "At step Y of the Normal Course, if [condition]..."
- Sub-steps numbered 5a, 5b...
- Closing sentence: "continue from step Z of the Normal Course"

**Pass**:
```
UC-LEARN-01.AC.1: Enroll using enterprise voucher
At step 5 of the Normal Course, if the learner selects Enterprise Voucher:
5a. System displays a voucher code field.
5b. Learner enters the code and clicks Apply.
5c. System validates the voucher → continue from step 7 of the Normal Course.
```

**Fail**:
```
AC1: If learner has a voucher, they can use it instead of paying.
```
(Too vague, no step reference, no sub-steps, no rejoining instruction)

---

### C17. Each Exception has trigger + response + final state
**How to check**: Does each exception have all 3 parts?

**Pass**:
```
UC-LEARN-01.EX.2: Course reaches full capacity mid-flow
Trigger: At step 7, LMS returns CAPACITY_EXCEEDED.
Response: System displays "This course just reached full capacity. Join the waitlist."
Final state: Payment refunded within 1 business day. No enrollment created. Waitlist offer shown.
```

**Fail**:
```
EX1: If an error occurs, system shows an error message.
```
(Vague — no trigger, no response detail, no final state)

---

### C18. Common failure modes are covered
**How to check**: Does the UC cover at least the common failure types relevant to Digital School?

| Failure type | Required for Digital School UC? |
|---|---|
| Validation error (invalid input) | ✅ |
| Business rule violation (quota exceeded, course at capacity) | ✅ |
| External service failure (payment gateway, LMS, calendar timeout) | ✅ |
| Authentication/Authorization failure | ✅ if UC has auth |
| Network/connectivity issue | ✅ for mobile flows |
| Concurrency conflict (two learners grabbing last slot) | ✅ for enrollment/booking UCs |
| Session timeout (mentor idle on detail view) | ✅ for UCs with long review flows |

**Tip**: If the UC has only 1-2 Exceptions → suspicious. Enrollment and booking UCs typically need 3-5.

---

## GROUP F: Completeness (C19-C20)

### C19. Includes (if any) point to existing UCs
**How to check**: Does each UC in the Includes field have a valid ID + does that UC actually exist?

**Pass**: "Includes: UC-PAY-01 (Process payment)" → UC-PAY-01 has been written and is in the UC register.
**Fail**: "Includes: Payment UC" → ID not specific, or referenced UC doesn't exist yet.

---

### C20. Special Requirements don't duplicate functional requirements
**How to check**: Is each item in Special Requirements a non-functional requirement?

**Pass** (non-functional):
- "Course catalog loads ≤ 2s under 5,000 concurrent users"
- "Audit log retained for 3 years"
- "Comply with Vietnamese VAT invoicing regulations"

**Fail** (functional — belongs in Normal Course / Business Rule):
- "Validate that the voucher code is 16 characters" → validation logic, belongs in a Normal Course step or BR
- "Learner can only enroll in 10 courses per month" → business rule, not a Special Requirement

---

## Validation Report

After checking all 20 items, output the report in this format:

```markdown
## Validation Result for UC-LEARN-01

| # | Item | Status | Note |
|---|------|--------|------|
| C1 | UC Name format | ✅ | "Enroll in Digital School course" — active verb + object |
| C2 | User-goal level | ✅ | Passes coffee-break test |
| C3 | UC ID unique | ✅ | Follows convention |
| C4 | 1 primary actor | ✅ | Learner |
| C5 | System boundary | ✅ | BA Zone Platform |
| C6 | Specific actor | ✅ | |
| C7 | Description WHY+WHAT+OUTCOME | ✅ | |
| C8 | Frequency quantified | ⚠️ | TBD — awaiting analytics from ops team |
| C9 | Preconditions verifiable | ✅ | 4/4 verifiable |
| C10 | Postconditions cover state | ✅ | 5 postconditions |
| C11 | No Pre/Assumption mix | ✅ | |
| C12 | Numbered, 1 action/step | ✅ | 9 steps |
| C13 | Actor/System alternating | ✅ | |
| C14 | No nested if/else | ✅ | |
| C15 | Flow complete | ✅ | |
| C16 | AC has "at step N" | ✅ | 2 ACs, all properly anchored |
| C17 | Exception has 3 parts | ✅ | 4 exceptions, all complete |
| C18 | Common failure modes covered | ✅ | Payment fail, capacity, LMS unavailable — all covered |
| C19 | Includes valid | ✅ | UC-PAY-01, UC-NOTI-01 |
| C20 | Special Req non-functional | ✅ | |

**Summary**: 19/20 ✅ + 1 ⚠️. UC is ready for stakeholder review.
**Follow-up**: C8 — Frequency of Use awaiting analytics data from the ops team [TBD-3].
```

---
*Compiled by **Phúc NT** · BA Zone · Digital School*  
*Please credit the source when sharing or adapting this checklist.*
