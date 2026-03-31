# MC1 FRQ — Add 3rd FRQ from CollegeBoard Released Exam

**Course:** `s4-r2-mc1-5ff6309d` | **Test:** `s4-r2-mc1-5ff6309d-frq-test`

---

## Current FRQs

| # | Item ID | Source | Topic | Type | Parts | Status |
|---|---------|--------|-------|------|-------|--------|
| 1 | `pcb-item-5f4d2be1-6832-4424-91a2-db037b026c41` | AP Released Exam 2025 Set 1 Q2 | Japan population pyramid | Type 2 (One Stimulus) | 7 (A-G) | GOOD |
| 2 | `qti-item-5fc26f15-51f6-4efb-800d-1fe1a0b70be1` | AP Classroom | Africa population data table | Type 2 (One Stimulus) | 4 (A-D) | Keep as-is |

## What's Missing

AP exam has 3 FRQs. We have 2. Need 1 more.

Both current FRQs are Type 2 (One Stimulus). Ideally the 3rd would be Type 1 (No Stimulus) or Type 3 (Two Stimuli) for variety.

---

## Recommended 3rd FRQ

### Option A (BEST) — 2024 AP Exam, Set 2, Question 3

**Download:** https://apcentral.collegeboard.org/media/pdf/ap24-frq-human-geography-set-2.pdf (Q3 is on pages 5-6)

**Scoring guidelines:** https://apcentral.collegeboard.org/media/pdf/ap24-apc-human-geography-q3-set-2.pdf

**Topic:** Aging populations, DTM stages, pronatalist policies, economic effects of negative growth

**Stimulus:** Data table with 7 countries (Croatia, Estonia, Germany, Greece, Japan, Portugal, Romania) — birth rate, death rate, % population over 65. All have negative RNI.

**Parts (7, A-G):**
- A: Select one country, identify its DTM stage
- B: Define pronatalist policy
- C: Explain one factor affecting birth rates (Stage 3→4)
- D: Describe one economic effect of negative population growth
- E: Describe a policy a government might develop in response
- F: Explain why urban life expectancy may be higher than national
- G: Explain how low birth rates impact % population over 65

**Why this is perfect for MC1:**
- Covers Topics 2.5 (DTM), 2.8 (Women/demographic change), 2.9 (Aging) — our three weakest areas
- Tests all 3 students' gaps: Gus needs DTM knowledge, Branson needs retrieval under pressure, Sydney needs correct application
- Real AP exam question with official scoring guidelines
- 7 parts with proper verb progression (Identify → Define → Explain → Describe → Describe → Explain → Explain)

### Option B (Alternative) — 2023 AP Exam, Set 1, Question 1

**Download:** https://apcentral.collegeboard.org/media/pdf/ap23-frq-human-geography-set-1.pdf

**Topic:** Rate of Natural Increase (RNI), comparison with TFR

**Type:** Type 1 (No Stimulus) — would give us all 3 FRQ types

**Parts:** 7 (A-G)

**Why:** Covers population dynamics (2.4), gives us a Type 1 FRQ which we're missing. But less aligned with our weak topics than Option A.

---

## Action

1. Download the 2024 Set 2 PDF from the link above
2. Extract Q3 (pages 5-6) — it has the data table stimulus + 7 parts
3. Add to test `s4-r2-mc1-5ff6309d-frq-test` as item 3
4. Also save the scoring guidelines PDF — Eric will need it for manual grading

## Note on FRQ 2

FRQ 2 (Africa data table) has only 4 parts / 5 pts. The AP standard is 7 parts / 7 pts. But this is the real AP Classroom version — don't modify it. If we want a full 7-part version, replace it with a different CollegeBoard released FRQ rather than adding generated parts.

## Also — the original question students got wrong

On the live course, the question "Throughout human history, world population has..." marked the correct answer D ("grown most rapidly over the last 200 years") as WRONG and showed A ("grown at a steady rate") as correct. This is BUG-2 item #2 in the main fix file — `pcb-item-e618c9f1-4de1-4684-af23-1ac234d8fbcb` in quiz 2.1. Fix: mark choice D as `isCorrect: true`.
