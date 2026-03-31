# MC1 FRQ Structure Review

**Date:** 2026-03-16
**Course:** s4-r2-mc1-5ff6309d (AP HuGeo: DTM Application)
**FRQ Quiz:** `s4-r2-mc1-5ff6309d-frq-test` ("Practice Excercise" — TYPO)

---

## Summary

| Check | Status | Detail |
|---|---|---|
| FRQ count | WARNING | 2 FRQs (AP exam has 3) |
| Quiz title | ERROR | "Practice Excercise" — typo, should be "Practice Exercise" |
| FRQ 1 structure | PASS | 7 parts A-G, matches AP Type 2 (One Stimulus) |
| FRQ 2 structure | WARNING | Only 4 parts A-D (5 pts). AP standard is 7 parts (7 pts) |
| FRQ 1 stimulus | PASS | Image-only (Japan population pyramid). Image URL resolves. |
| FRQ 2 stimulus | PASS | Data table (Africa population stats). Text in body_text. |
| Task verbs | PASS | Both use Identify, Describe, Explain |
| FRQ Type coverage | WARNING | Both are Type 2 (One Stimulus). Missing Type 1 (No Stimulus) and Type 3 (Two Stimuli) |
| Rubric/scoring | WARNING | No rubric data in JSON — Timeback doesn't store rubrics with questions |
| Topic alignment | PASS | FRQ 1: CED 2.3 (Pop Composition), FRQ 2: CED 2.5 (DTM) — both match MC1 scope |

---

## FRQ 1: Japan Population Pyramid (7 pts)

**ID:** `pcb-item-5f4d2be1-6832-4424-91a2-db037b026c41`
**Source:** AP Released Exam 2025 - Set 1, Question 2
**Type:** FRQ Type 2 (One Stimulus)
**CED:** Unit 2, Topic 2.3 (Population Composition), Skill 3 (Data Analysis)

### Stimulus
- **Type:** Image only (no body_text)
- **Image:** Japan population pyramid
- **URL:** `https://pass-rate-dashboard-data.s3.amazonaws.com/cropped_images/f45cb346-1cf4-49e9-902c-087c2c102c47/0.png`
- **Status:** Needs manual verification that image loads correctly in Timeback

### Parts (7 parts, 7 points)

| Part | Task Verb | Prompt | Points |
|---|---|---|---|
| A | Identify | Identify the recent trend in fertility shown in the population pyramid | 1 |
| B | Describe | Describe the ratio of males to females in the Japanese population age 80+ | 1 |
| C | Describe | Describe one process that drives urbanization | 1 |
| D | Describe | Describe one factor that may lead to a decrease in total population within a more developed country | 1 |
| E | Explain | Explain how a country's population pyramid can be used to predict the future needs of the population | 1 |
| F | Explain | Explain why the population pyramid provides limited information about immigration to cities in Japan | 1 |
| G | Explain | Explain the degree to which a country's population growth rate may be affected by a pronatalist policy (must indicate degree: low/moderate/high + explanation) | 1 |

### Assessment
- Structure: CORRECT AP format (7 parts, progressive task verbs: Identify → Describe → Explain)
- Part G requires degree judgment — good higher-order thinking
- Part C ("urbanization") seems tangential to population pyramids — but this is straight from AP Released Exam, so it's valid
- Covers multiple CED topics within Unit 2 (composition, urbanization, aging, pronatalist policies)

---

## FRQ 2: African Population Statistics (5 pts)

**ID:** `qti-item-5fc26f15-51f6-4efb-800d-1fe1a0b70be1`
**Source:** Not explicitly stated (metadata says CED/LLM tagged)
**Type:** FRQ Type 2 (One Stimulus)
**CED:** Unit 2, Topic 2.5 (The Demographic Transition Model), Skill 3

### Stimulus
- **Type:** Data table (text in body_text)
- **Content:** Population statistics for Egypt, Ethiopia, Nigeria, South Africa (2018)
- **Columns:** Population, Birth Rate, Death Rate, TFR, Infant Mortality Rate, % Urban

| Country | Population | BR | DR | TFR | IMR | % Urban |
|---|---|---|---|---|---|---|
| Egypt | 97M | 27 | 6 | 3.4 | 15 | 43 |
| Ethiopia | 107M | 33 | 7 | 4.4 | 40 | 20 |
| Nigeria | 195M | 39 | 12 | 5.5 | 67 | 50 |
| South Africa | 58M | 21 | 9 | 2.4 | 36 | 66 |

### Parts (4 parts, NOT 7)

| Part | Task Verb | Prompt | Points |
|---|---|---|---|
| A | Describe | Describe what information the DTM provides about a country | 1 |
| B | Identify + Describe | Identify ONE country in stage 2 of DTM. Describe ONE reason why | 2 |
| C | Describe | Describe the relationship between birth rate and infant mortality rate as epidemiological transition occurs | 1 |
| D | Explain | Explain what TFR and IMR imply about the roles of women | 1 |

### Issues Found

1. **ONLY 4 PARTS (A-D)** — AP standard is 7 parts (A-G) worth 7 points. This FRQ has only 5 points total.
2. **Not AP-released** — Source appears to be CED/LLM tagged, not from an official AP exam. The metadata schema is different from FRQ 1.
3. **Part B is worth 2 points** (identify + describe) which is non-standard — AP typically awards 1 point per sub-task.
4. **Missing higher-order parts** — No parts asking students to "Compare," "Evaluate," or make cross-topic connections. AP FRQs typically escalate from define → describe → explain → evaluate.

---

## Course-Level FRQ Issues

### 1. Only 2 FRQs (AP exam has 3)
The AP exam has exactly 3 FRQs:
- FRQ 1: No Stimulus (7 pts)
- FRQ 2: One Stimulus (7 pts)
- FRQ 3: Two Stimuli (7 pts)

MC1 only has 2 FRQs and both are Type 2 (One Stimulus). **Missing:** Type 1 (No Stimulus) and Type 3 (Two Stimuli).

### 2. Quiz Title Typo
"Practice Excercise" → Should be "Practice Exercise"

### 3. No Rubric Data
Timeback stores FRQs as `extended-text` type with no structured rubric. The scoring criteria, sample responses, and point allocation are NOT in the JSON. This means:
- Students get NO automated scoring feedback on FRQs
- Teachers/coaches have to manually score using external rubrics
- There's no way to programmatically verify rubric quality

### 4. FRQ 2 is Below AP Standard
Only 4 parts / 5 points instead of 7 parts / 7 points. This under-prepares students for the length and complexity of real AP FRQs.

---

## Recommendations for Akshit

| # | Priority | Action |
|---|---|---|
| F1 | CRITICAL | Fix typo: "Practice Excercise" → "Practice Exercise" |
| F2 | HIGH | Add a 3rd FRQ — ideally Type 1 (No Stimulus, 7 pts) or Type 3 (Two Stimuli, 7 pts) to cover all 3 AP FRQ types |
| F3 | HIGH | Replace or expand FRQ 2 to have 7 parts (A-G) worth 7 points total. Add parts E-G with Explain/Compare/Evaluate task verbs |
| F4 | MEDIUM | Verify FRQ 1 image loads correctly in Timeback (Japan pyramid from S3 bucket) |
| F5 | INFO | Note: Timeback cannot auto-score FRQs — students will need manual coaching review. Flag for Eric. |

---

## Rubric Scoring Test

**Can Timeback score FRQs?** NO — based on the data structure:
- FRQ questions are type `extended-text` with `choices: []` (empty)
- No rubric object in the question metadata
- No scoring criteria, sample responses, or point breakdowns
- The quiz is configured as `assessment_type: "quiz"` with `showResults: true`

Students submit free-text responses. There is no automated scoring. This means:
- FRQs in Timeback are essentially practice prompts, not auto-graded assessments
- Scoring must happen via coach review (Eric's responsibility per governance spec)
- The QC pipeline cannot programmatically verify rubric quality because rubrics don't exist in the data

**Recommendation:** Create a separate rubric document for each FRQ that Eric can use for manual scoring. Include sample responses at each point level (0, 1, 2... up to max).
