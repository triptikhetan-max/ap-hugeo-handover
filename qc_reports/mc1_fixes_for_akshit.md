# MC1: DTM Application — Engineering Fix List

**Course:** `s4-r2-mc1-5ff6309d` | **Date:** 2026-03-18 | **Priority:** BUG-2 first (students broken NOW)

---

## DO NOW — 7 Questions With No Correct Answer (10 min)

These 7 questions have all choices set to `isCorrect: false`. Students get penalized for every answer. **Confirmed broken on live.**

| # | Item ID | Quiz | Test ID | Stem (first words) | Mark this choice correct |
|---|---------|------|---------|---------------------|--------------------------|
| 1 | `pcb-item-ea384068-ea55-4274-9c6a-c9fb2fddbd9d` | 2.1 Q11 | `pcb-test-940e671ba34d43a08ec616d8ccb529d0` | "Most of the world's people live in" | **A: "the world's poorest countries"** |
| 2 | `pcb-item-e618c9f1-4de1-4684-af23-1ac234d8fbcb` | 2.1 Q12 | same | "Throughout human history, world population has" | **D: "grown most rapidly over the last 200 years"** |
| 3 | `pcb-item-26999226-0ad6-4396-91d4-5e2e6635b979` | 2.1 Q13 | same | "Which country densest population?" | **D: "Belgium"** |
| 4 | `pcb-item-b893c849-09e7-4650-b116-e295e3691cbc` | 2.4 Q21 | `pcb-test-5caf0a8273604ad4b8acea88b4ffdb06` | "_____ occurs when adding a fixed percentage" | **D: "Exponential growth"** |
| 5 | `pcb-item-fe1dfdee-c6a7-4675-9bd6-fc85e68229a1` | 2.4 Q22 | same | "Life expectancy has increased" | **D: "worldwide"** |
| 6 | `pcb-item-666e9578-d939-4292-bbbc-8641ca1235d5` | 2.5 Q19 | `pcb-test-687825799f6c4fe99e1248151dc4b274` | "Carrying capacity is a function of" | **E** — BUT rewrite it (see FIX-2 below) |
| 7 | `pcb-item-10e8ce26-6442-4b1f-a27d-17d924088e66` | 2.8 Q9 | `pcb-test-931f09412e934756a2f678f8bb0ec0a2` | "India and China...strict pop policy" | **C: "encourages lower fertility through education and access to family planning"** |

All 7 are Barron's source. Correct answers verified against `barrons_2024_all_mcqs.json` (full Barron's answer key with explanations).

Akshit's export files: `2.1.json` indices 10-12, `2.4.json` indices 20-21, `2.5.json` index 18, `2.8.json` index 8.

**Source verification:** These answers come from Barron's own answer key in the extracted data at `/Users/tripti/Downloads/Human Geography/barrons_2024_all_mcqs.json`. Each question has a `correct_answer` and `explanation` field. The Barron's sections are "Human Population: A Global Perspective" and "Population and Sustainability".

---

## FIX-2 — Rewrite "Carrying Capacity" Choice E + Fix Typo (5 min)

**Item:** `pcb-item-666e9578-d939-4292-bbbc-8641ca1235d5` (2.5 Q19)

Two problems:
1. Choice A says **"echnology"** → change to **"technology"**
2. Choice E says **"(A), (B), and (D)"** → if choices get randomized, this breaks

**Action:** Change choice E text from `(A), (B), and (D)` to `technology, natural resources, and limiting factors`. Then mark choice E as correct.

---

## FIX-3 — Check 4 Missing Stimuli (20 min)

These questions reference a map/graph/pyramid but our data shows no stimulus attached. **Some may be false positives** — the NASA map in Q2 renders fine on live despite missing in data.

| # | Item ID | Quiz | References | Action |
|---|---------|------|------------|--------|
| 1 | `pcb-item-11e0015d-6104-4196-bdd5-f0775c6c50d6` | 2.1 Q2 | "The map" (NASA) | **Check live** — may already work |
| 2 | `pcb-item-89a2f8e9-d813-42b5-b2ac-ced52b268406` | 2.3 Q5 | "population pyramid wide at top" | **Conceptual question** — may not need image. Verify on live. |
| 3 | `pcb-item-1e0400f1-9b99-4177-a026-af41f0f21e75` | 2.3 Q16 | "when baby boomers retire, pyramid shape" | **Conceptual question** — may not need image. Verify on live. |
| 4 | `pcb-item-01818f1f-d0fb-42d8-aa75-5328ff2f5042` | 2.4 Q17 | "Based on the graph" (UN/PRB) | **Needs graph attached** — check live first |

**Action:** Open each on live course. If stimulus renders, no fix needed. If blank, either attach the correct image or rewrite the stem to be standalone.

---

## FIX-4 — FRQ Title Typo (1 min)

**Test ID:** `s4-r2-mc1-5ff6309d-frq-test`

Current title: **"Practice Excercise"** → Change to: **"Practice Exercise"**

Students see "FRQ Practice" in breadcrumb so this is internal only, but should still be fixed.

---

## FIX-5 — Mini MCQ Has Zero Unique Questions (NEW — IMPORTANT)

**Test ID:** `pcb-test-3333ee99c44a4d61afd057e34fedb29b`

All 18 items in the Mini MCQ Practice Quiz are exact duplicates of topic quiz questions. Students get zero new practice. The quiz is pointless as-is.

**Current 18 items (all duplicates):**

| Mini Q# | Mini Item ID | Duplicate of | Topic Item ID |
|---------|-------------|-------------|---------------|
| Q1 | `pcb-item-8eeea5be-defa-48e2-a021-faf12fb19e32` | 2.1 Q4 | `pcb-item-e91e6eca-3733-480d-9e33-43069b9e6784` |
| Q2 | `pcb-item-d40ee267-1cdc-430e-a981-61a5c3961374` | 2.1 Q8 | `pcb-item-60ffec71-d5fc-4a9b-93b8-2abafc37db9b` |
| Q3 | `pcb-item-5a5212d1-403e-48c2-9f51-3a4b57c9488e` | 2.1 Q7 | `pcb-item-506ce37c-1f5e-4f21-8ea9-ef15e14bd034` |
| Q4 | `pcb-item-f3c18d75-2a75-40f2-8c72-32ed62614bdb` | 2.3 Q1 | `pcb-item-0727919b-e8d6-4275-ae7e-f0c81b808236` |
| Q5 | `pcb-item-d8297b6d-8711-4d71-a7d3-06d86e8d05a7` | 2.3 Q11 | `pcb-item-f128c590-881c-4db5-9013-9df8c3006fe5` |
| Q6 | `pcb-item-5ee291c1-71ac-4df0-85bf-53a3dcb01fff` | 2.3 Q8 | `pcb-item-5da633de-6d16-4407-aeb6-fa782568a1dc` |
| Q7 | `pcb-item-5c01babd-7210-46b3-837e-e2302c0d901e` | 2.4 Q2 | `pcb-item-60c53c34-6365-49c4-8d43-fc6bb30e8771` |
| Q8 | `pcb-item-904304f8-4ba9-48de-9e1a-f38015829a55` | 2.4 Q8 | `pcb-item-831fc102-6089-4ac1-8cd3-9ea802e5c419` |
| Q9 | `pcb-item-8eeb5cf9-a276-47c4-a967-b517b106da3c` | 2.4 Q15 | `pcb-item-244828d7-9a8d-4bce-8369-d31546b432e6` |
| Q10 | `pcb-item-a00ef0a3-7ec9-4f12-97b1-0d759cba3417` | 2.5 Q3 | `pcb-item-ab1f519f-fe4d-458e-89fb-2648d091c45e` |
| Q11 | `pcb-item-36880557-78c2-42e9-a085-c61af8b91197` | 2.5 Q6 | `pcb-item-5cbc382f-a88c-428c-9085-bed1da230d5c` |
| Q12 | `pcb-item-d12018aa-9fa7-42fa-82db-919ed241fcdd` | 2.5 Q13 | `pcb-item-2ce5a571-4f28-42c9-ac46-5bca59fe84d5` |
| Q13 | `pcb-item-f452e0ce-745a-4653-bd25-ebc83f039a88` | 2.8 Q6 | `pcb-item-a18d40d5-fc82-437c-9be0-029c10baa575` |
| Q14 | `pcb-item-238b1763-845c-47a0-b3df-797324a244de` | 2.8 Q7 | `pcb-item-53e8a0f4-561e-4cd3-9f51-7824680ccac2` |
| Q15 | `pcb-item-893f8af0-2c80-4453-8b39-cd3cf52a8d03` | 2.8 Q1 | `pcb-item-4e066b02-5487-4d99-ae0d-fd30030c8345` |
| Q16 | `pcb-item-e5d22249-c827-4af0-aa24-a8e4c5c97b25` | 2.9 Q9 | `pcb-item-f8faa71a-3e7f-4950-8233-d8dbe4668bb8` |
| Q17 | `pcb-item-e15769f7-df76-4724-a0ea-54a751aa742b` | 2.9 Q3 | `pcb-item-f944a2b6-7ff5-4b17-a004-dda14446f66c` |
| Q18 | `pcb-item-338ee090-d5ad-47e5-a86e-9764218755ad` | 2.9 Q5 | `pcb-item-683906b8-9f3e-4bae-863f-ef15542cb3fb` |

**Action:** Replace some or all of these 18 items with NEW AP Classroom questions not already in topic quizzes. The purpose of this quiz is mixed-topic retrieval practice — students should see questions they haven't answered before.

**Where to source 18 replacement questions:**

**Option A — AP Classroom (if available):** 3 new questions per topic from AP Classroom question bank. But AP may be exhausted for some topics (we already use 93 AP items across the course).

**Option B — Barron's pool (ready to use):** We have 23 unused Barron's Unit 2 population questions with full stems, choices, answers, and explanations in `barrons_2024_all_mcqs.json`. See the Replacement Question Pool section below for the full list categorized by topic. Pick 3 per topic:
- **2.1:** B-POOL-4 (Rwanda density) + B-POOL-10 (Java density) + 1 more
- **2.3:** B-POOL-8 (one-child pyramid change) + B-POOL-22 (highest birth rate pyramid) + B-POOL-23 (two age cohorts)
- **2.4:** B-POOL-5 (neo-Malthusians) + B-POOL-20 (Malthus argument) + B-POOL-25 (demographic accounting)
- **2.5:** B-POOL-6 (Bangladesh DTM) + B-POOL-13 (epidemiological transition) + B-POOL-11 (Stage 1 vs Stage 2 growth)
- **2.8:** B-POOL-7 (Europe fertility) + B-POOL-12 (population programs) + B-POOL-30 (best predictor of birth rate)
- **2.9:** B-POOL-1 (assisted living) + B-POOL-14 (retirement homes dependency) + B-POOL-21 (elderly pyramid)

**Option C — Mix:** Use AP Classroom where available, fill gaps with Barron's.

---

## FIX-6 — Delete Duplicate Within 2.5 Quiz

**Quiz:** 2.5 (`pcb-test-687825799f6c4fe99e1248151dc4b274`)

Items `pcb-item-a4774845-ac35-4e41-b97f-acf9f1ff0369` (Q4, index 3) and `pcb-item-982aedb6-ec65-4a4e-b839-1f79626eca2f` (Q12, index 11) are the same question ("Birth Rates and Death Rates for Selected Regions").

**Action:** Delete one. Recommend deleting Q12 (`pcb-item-982aedb6-ec65-4a4e-b839-1f79626eca2f`).

---

## FIX-7 — Topics 2.8 and 2.9 Need More Questions

Both have only 10 items. Target: 16 per quiz.

**AP Classroom may be exhausted** — 2.8 already uses 7 AP items and 2.9 uses 9 AP items. First check if AP Classroom has more for these topics. If not, use these specific Barron's questions below (full data in `barrons_2024_all_mcqs.json`, filter by `source` + `question_number`).

**Add these 6 to 2.8 — Women & Demo Change** (`pcb-test-931f09412e934756a2f678f8bb0ec0a2`):

| # | Barron's Ref | Stem | Answer | Stimulus |
|---|-------------|------|--------|----------|
| 1 | Diagnostic Q5 | "Which population policy for country with growing elderly facilities?" | A (Pronatalist) | YES — need assisted living image |
| 2 | Diagnostic Q25 | "Current fertility rates in Europe exhibit which trend?" | A (near/below replacement) | No |
| 3 | PT1 Q4 | "Given Bangladesh's data, DTM position is most likely..." | C (Stage 3) | YES — CIA Factbook chart |
| 4 | PT1 Q44 | "Most successful population programs focus on..." | C (increasing women's access to education) | No |
| 5 | Diagnostic Q21 | "China's one-child policy led to which demographic challenge?" | E (male-female imbalance) | No |
| 6 | PT1 Q8 | "Main cause of declining fertility in developing regions?" | B (women more educated/active in economy) | No |

**Add these 6 to 2.9 — Aging Populations** (`pcb-test-0390d0cc11ee42f18e88b277e1ffbf12`):

| # | Barron's Ref | Stem | Answer | Stimulus |
|---|-------------|------|--------|----------|
| 1 | Diagnostic Q3 | "Assisted living facility image — which country most probable?" | A (United States) | YES — need assisted living image |
| 2 | Diagnostic Q4 | "Countries with growing elderly facilities — which DTM stage?" | D (Stage 4) | YES — same image |
| 3 | PT1 Q57 | "Growing retirement homes indicates..." | C (problematic dependency ratio) | No |
| 4 | PT2 Q58 | "Which of 4 pyramids has greatest proportion of elderly?" | B (Naples, FL) | YES — 4 population pyramids |
| 5 | PT2 Q42 | "Map of average ages by country — what pattern?" | B (wealthier countries = older) | YES — world map |
| 6 | PT2 Q3 | "Which country experiencing slowest population growth?" | A (Denmark) | YES — population pyramids |

**For stimulus images:** Extract from the Barron's EPUB at `/Users/tripti/Downloads/Human Geography/[Barron_s AP]...2024...epub`. Images are in `OEBPS/images/` inside the EPUB (it's a ZIP file). Match by chapter — these are all in Chapter 2 (Unit 2).

---

## CONFIRM — Dead Content in API

These are all `tobedeleted` in the API and invisible to students. No action needed, just confirming.

| What | Status in API | Live Course |
|------|--------------|-------------|
| PP100 Mastery Practice (78 ced_llm items) | `tobedeleted` | Blank page |
| CHECK section + 2 resources | `tobedeleted` | Not visible |
| Sample item ghost in FRQ APPLY | `tobedeleted` | Not visible |

**Question for Akshit:** Can these be fully purged from the API? Our puller was including them until we added `tobedeleted` filtering.

---

## FIX-8 — FRQ Gaps: Need 3rd FRQ + Expand FRQ 2 to 7 Parts (Tripti will share separately)

**Current state:**
- FRQ 1: `pcb-item-5f4d2be1-6832-4424-91a2-db037b026c41` — Japan pyramid, 7 parts A-G, 7 pts. **GOOD.** Type 2 (One Stimulus). Source: AP Released Exam 2025.
- FRQ 2: `qti-item-5fc26f15-51f6-4efb-800d-1fe1a0b70be1` — Africa data table, only 4 parts A-D, 5 pts. **BELOW STANDARD.** Type 2 (One Stimulus).

**Problems:**
1. AP exam has **3 FRQs** (Type 1: No Stimulus, Type 2: One Stimulus, Type 3: Two Stimuli). MC1 has only 2, both Type 2.
2. FRQ 2 has only 4 parts / 5 pts instead of standard 7 parts / 7 pts.

**Action — Expand FRQ 2 to 7 parts:**

Current FRQ 2 has parts A-D. Add parts E, F, G:

```
E. Explain how the data in the table could be used to predict which country
   is most likely to experience rapid population growth in the next 20 years. (1 pt)

F. Explain ONE way that a government policy in a Stage 2 country could
   accelerate the demographic transition to Stage 3. (1 pt)

G. Compare the likely population challenges facing South Africa versus
   Nigeria based on their demographic indicators in the table. (1 pt)
```

This keeps the existing 4 parts, adds 3 more following AP verb progression (Explain → Explain → Compare), and brings total to 7 parts / 7 pts.

**Action — Add 3rd FRQ (Type 1: No Stimulus, 7 pts):**

Create a new FRQ with NO stimulus (text-only prompt). Suggested topic: DTM application across multiple countries (hits Topics 2.4, 2.5, 2.8, 2.9).

```
Suggested FRQ 3 — Type 1 (No Stimulus):

The demographic transition model (DTM) describes changes in birth rates
and death rates as a country develops economically.

A. Define the demographic transition model. (1 pt)
B. Identify the stage of the DTM where natural increase is highest. (1 pt)
C. Describe ONE factor that causes death rates to decline in Stage 2. (1 pt)
D. Describe ONE factor that causes birth rates to decline in Stage 3. (1 pt)
E. Explain how women's access to education affects a country's position
   in the DTM. (1 pt)
F. Explain why some countries in sub-Saharan Africa have remained in
   Stage 2 of the DTM despite global improvements in healthcare. (1 pt)
G. Explain the degree to which government population policies can
   accelerate a country's transition through the DTM. Provide a
   specific country example. (1 pt)
```

Task verb progression: Define → Identify → Describe → Describe → Explain → Explain → Explain (matches AP format). Covers CED Topics 2.4, 2.5, 2.8. Tests all 3 students' weak areas (Gus: Layer 1 content, Branson: retrieval, Sydney: application).

**Add to test:** `s4-r2-mc1-5ff6309d-frq-test` as item 3.

---

## LOWER PRIORITY

### Answer Position Bias
In some quizzes, correct answer clusters at one position. When adding/editing questions, distribute correct answers evenly across A-E.

### Missing Feedback
0/116 MCQs have feedback in topic quizzes (Akshit's export shows 63/116 have it — may need re-upload). When students get wrong answers, they see nothing. Add explanations over time, starting with BUG-2 questions (students need to understand why D not A).

### "All/None of the Above"
Only 1 question uses this pattern (the Carrying Capacity one, already fixed above in FIX-2). AP exam never uses these.

---

## Quick Content Wins (for Tripti/Eric, not Akshit)

### Add to Topic 2.3 Article
Insert after pyramid types section — DTM Stage ↔ Pyramid Shape connection table. Sydney needs this to stop misapplying DTM stages.

### Beef Up Topic 2.8 Article (currently 859 words, thinnest)
Add case studies: Bangladesh TFR drop with female literacy rise, Iran's rapid fertility decline, Sub-Saharan Africa contrast.

### Add to Topic 2.9 Article
Add government response examples: Japan (retirement age, robotics, cash bonuses), Germany (immigration), China (ended one-child), Singapore/Sweden (pro-natalist policies). FRQ questions ask students to name specific policy responses.

---

## Action Plan — Priority Order

| Step | What | Item IDs | Time |
|------|------|----------|------|
| **1** | **Mark correct answers on 7 broken questions** | See DO NOW table above | 10 min |
| **2** | Rewrite Carrying Capacity choice E + fix typo | `pcb-item-666e9578` | 5 min |
| **3** | Check 4 stimulus questions on live | `pcb-item-11e0015d`, `-89a2f8e9`, `-1e0400f1`, `-01818f1f` | 20 min |
| **4** | Fix FRQ title typo | `s4-r2-mc1-5ff6309d-frq-test` | 1 min |
| **5** | Delete duplicate in 2.5 | `pcb-item-982aedb6` | 2 min |
| **6** | Replace Mini MCQ with 18 new AP Classroom questions | `pcb-test-3333ee99c44a4d61afd057e34fedb29b` | 1-2 hrs |
| **7** | Add 6-10 questions each to 2.8 and 2.9 | `pcb-test-931f09412e934756a2f678f8bb0ec0a2`, `pcb-test-0390d0cc11ee42f18e88b277e1ffbf12` | 1-2 hrs |
| **8** | Expand FRQ 2 from 4→7 parts (add E, F, G) | `qti-item-5fc26f15-51f6-4efb-800d-1fe1a0b70be1` | 30 min |
| **9** | Add 3rd FRQ (Type 1, No Stimulus, 7 pts) — see FIX-8 for exact prompt | `s4-r2-mc1-5ff6309d-frq-test` | 30 min |

**Steps 1-5: ~38 min. Do these before students start the course.**
**Steps 6-7: 2-4 hrs. Can be done after students begin (they won't hit Mini MCQ until they finish all 6 topics).**
**Steps 8-9: ~1 hr. FRQ is at the end of the course so students won't reach it immediately.**

---

## Replacement Question Pool — Barron's 2024 (NOT in course yet)

We extracted 319 MCQs from Barron's AP Human Geography Premium 2024 (`/Users/tripti/Downloads/Human Geography/barrons_2024_all_mcqs.json`). 35 are Unit 2. 12 are migration (wrong mini-course). **23 are population questions ready to use.** All have stems, 5 choices, correct answer, and explanation.

**For Topic 2.9 (Aging) — currently 10 items, need 6-10 more:**

| ID | Source | Stem | Answer | Has Stimulus |
|----|--------|------|--------|--------------|
| B-POOL-1 | Diagnostic Q3 | "This is an image of an assisted living facility. Which country is the most probable location?" | A (United States) | YES (image) |
| B-POOL-2 | Diagnostic Q4 | "Countries with growing number of such facilities are most likely in which stage of DTM?" | D (Stage 4) | YES (image) |
| B-POOL-14 | PT1 Q57 | "Growing number of retirement homes is an indication of..." | C (problematic dependency ratio) | No |
| B-POOL-21 | PT2 Q58 | "Which population pyramid has the greatest proportion of elderly residents?" | B (Naples, FL) | YES (4 pyramids) |

**For Topic 2.8 (Women & Demo Change) — currently 10 items, need 6-10 more:**

| ID | Source | Stem | Answer | Has Stimulus |
|----|--------|------|--------|--------------|
| B-POOL-3 | Diagnostic Q5 | "Which population policy might be in place in a country with growing elderly facilities?" | A (Pronatalist) | YES (image) |
| B-POOL-7 | Diagnostic Q25 | "Current fertility rates in Europe exhibit which trend?" | A (near or below replacement) | No |
| B-POOL-9 | PT1 Q4 | "Given Bangladesh's data, its DTM position is most likely..." | C (Stage 3) | YES (chart) |
| B-POOL-12 | PT1 Q44 | "Most successful population programs focus on..." | C (women's access to education) | No |
| B-POOL-16 | PT2 Q10 | "Which describes a country in stage 3 of DTM?" | D (rapid but declining growth) | YES (DTM diagram) |
| B-POOL-17 | PT2 Q42 | "Pattern in map showing average ages by country..." | B (wealthier = older) | YES (map) |

**For Topic 2.1 (Distribution) — currently 14 items, could add:**

| ID | Source | Stem | Answer | Has Stimulus |
|----|--------|------|--------|--------------|
| B-POOL-4 | Diagnostic Q8 | "Rwanda population density high despite equatorial location because..." | A (volcanic activity feeds soil) | No |
| B-POOL-10 | PT1 Q9 | "Java's population density is attributable to..." | A (volcanic activity) | No |

**For Topic 2.4 (Dynamics) — currently 26 items, could add:**

| ID | Source | Stem | Answer | Has Stimulus |
|----|--------|------|--------|--------------|
| B-POOL-5 | Diagnostic Q9 | "Neo-Malthusians describe tension between..." | E (population growth and resource consumption) | No |
| B-POOL-11 | PT1 Q11 | "Malthus and neo-Malthusians describe tension between..." | E (same topic, different wording) | No |
| B-POOL-20 | PT2 Q55 | "Thomas Malthus introduced which argument?" | D (population outstrips food production) | No |

**For Topic 2.3 (Composition) — currently 17 items, could add:**

| ID | Source | Stem | Answer | Has Stimulus |
|----|--------|------|--------|--------------|
| B-POOL-8 | PT1 Q2 | "If strict one-child policy, how would pyramid change in 20 years?" | C (still wide base due to momentum) | YES (pyramid) |
| B-POOL-15 | PT2 Q3 | "Which country experiencing slowest population growth?" | A (Denmark) | YES (pyramids) |
| B-POOL-22 | PT2 Q59 | "Which pyramid depicts community with highest birth rate?" | A (Detroit) | YES (4 pyramids) |
| B-POOL-23 | PT2 Q60 | "Which pyramid depicts community with two distinct age cohorts?" | C (Honolulu) | YES (4 pyramids) |

**For Topic 2.5 (DTM) — currently 22 items, could add:**

| ID | Source | Stem | Answer | Has Stimulus |
|----|--------|------|--------|--------------|
| B-POOL-6 | Diagnostic Q15 | "Given Bangladesh's data, DTM position is most likely..." | C (Stage 3) | No |
| B-POOL-13 | PT1 Q51 | "Which concept explains difference in causes of death low vs high income?" | B (Epidemiological transition) | No |
| B-POOL-8 | Diagnostic Q21 | "China's one-child policy led to which demographic challenge?" | E (male-female imbalance) | No |

**How to use:** Full question data (stems, all 5 choices, correct answer, explanation) is in `barrons_2024_all_mcqs.json`. Filter by `unit: "Unit 2"` and match by `source` + `question_number` fields above. Each question includes a full `explanation` field that can be used as student feedback.

**NOTE:** Some questions reference images/charts from the Barron's book that would need to be recreated or sourced as stimulus images in Timeback. Questions marked "YES" in Has Stimulus need the original image uploaded.

---

## Reference: All Quiz IDs

| Quiz | Test ID | Items |
|------|---------|-------|
| 2.1 Population Distribution | `pcb-test-940e671ba34d43a08ec616d8ccb529d0` | 14 |
| 2.3 Population Composition | `pcb-test-b91ca0faa52b4ddb83b1bfaf95602a02` | 17 |
| 2.4 Population Dynamics | `pcb-test-5caf0a8273604ad4b8acea88b4ffdb06` | 26 |
| 2.5 The DTM | `pcb-test-687825799f6c4fe99e1248151dc4b274` | 22 |
| 2.8 Women & Demo Change | `pcb-test-931f09412e934756a2f678f8bb0ec0a2` | 10 |
| 2.9 Aging Populations | `pcb-test-0390d0cc11ee42f18e88b277e1ffbf12` | 10 |
| Mini MCQ Practice | `pcb-test-3333ee99c44a4d61afd057e34fedb29b` | 18 |
| FRQ APPLY | `s4-r2-mc1-5ff6309d-frq-test` | 2 |
