# MC1: DTM Application

**Parent spec:** [ap_human_geography.md](ap_human_geography.md) (student data, CED reference, governance)

| Field | Value |
|---|---|
| **Assign to** | Branson (AP 2), Gus (AP 1), Sydney (AP 3) |
| **CED Topics** | 2.1, 2.3, 2.4, 2.5, 2.8, 2.9 |
| **Structure** | Per-topic cycles (Video → Article → PP100/Quiz) for each topic, then Mini MCQ Practice Quiz, then FRQ |
| **Build location** | `/output/s4-r2-mc1-5ff6309d/` |

---

## Structure — Per-Topic Cycles

This course does NOT use the flat LEARN → CHECK → PP100 → FRQ structure. It uses **per-topic cycles**:

**For EACH topic (2.1, 2.3, 2.4, 2.5, 2.8, 2.9):**

1. **Video** — Heimler video from HUMG20-v1 (already exists in current build)
2. **Article** — Lesson article from HUMG20-v1 (already exists in current build)
3. **PP100** — Sourced from AP Classroom ONLY. We want PP100 (SmartScore to 100, 80% accuracy threshold). If the AP Classroom question bank doesn't have enough questions for that topic to run PP100, then use a fixed 20-question quiz instead. Maximize stimulus-based questions (data tables, pyramids, country scenarios).

**After ALL 6 topics are done:**

4. **Mini MCQ Practice Quiz** — Fixed quiz, balanced across all 6 topics. Try not to repeat questions from the per-topic PP100s/quizzes, but if the question bank is limited, 25% repeat is OK (that's spaced repetition). Maximize stimulus-based questions.
5. **FRQ** — Keep existing 2 FRQs (good quality)

---

## LEARN Content — What to Pull (Per Topic)

Pull articles and videos from HUMG20-v1 main course. Do NOT generate content.

| Topic | Article (from HUMG20-v1) | Video (Heimler from HUMG20-v1) |
|---|---|---|
| 2.1 Population Distribution | Full lesson content | Heimler: Population Distribution & Density |
| 2.3 Population Composition | Population pyramid visuals and lesson content | Heimler: Population Composition |
| 2.4 Population Dynamics | Birth rate, death rate, natural increase | Heimler: Rate of Natural Increase |
| 2.5 The DTM | Full lesson — this is the core lesson | Heimler: The DTM Explained |
| 2.8 Women & Demographic Change | Stage 4-5 mechanisms — why birth rates decline | Heimler: Women & Demographic Change |
| 2.9 Aging Populations | Stage 5 consequences — dependency ratios, policy | Heimler: Impact of Aging Populations |

---

## Question Source — AP Classroom ONLY

**All quiz/practice questions** must come from the AP Classroom course:
- **Source course:** `c8265419-470e-450c-8113-bd2b31ae27af` ("AP Classroom Scraping - Session 3"), AP Human Geo section
- AP Human Geo MCQ tests: MCQ Units 1-4 + MCQ Units 5-7 + Practice MCQ 2020
- All AP Classroom questions are **5-choice (A-E)** — proper AP format
- Questions are tagged by topic code — filter by topic for each per-topic quiz

**Do NOT use:**
- HUMG20-v1 questions for quizzes — those are NOT AP Classroom
- Princeton Review or Barron's questions
- Generated/written questions

---

## What to DELETE from Current Build

- All current HUMG20-v1 PP100 questions (78 items from single HUMG20-v1 quiz)
- Current CHECK quiz (6 Princeton/Barron's items)
- Ghost "Sample item" entries (status: tobedeleted)

## What to KEEP from Current Build

- All 6 Heimler videos (LEARN content from HUMG20-v1)
- All 6 lesson articles (LEARN content from HUMG20-v1)
- Both FRQs (Japan population pyramid 7pts + Africa data table 5pts)

---

## FRQ APPLY — 2 Prompts

- Keep existing 2 FRQs from current build (good quality)
- **Timer:** Standard 25 min / **Branson gets 50 min** (double-time SSD)

---

## Cleanup

- Fix "Practice Excercise" typo → "Practice Exercise"
- Verify images/tables render in Timeback student view
- Configure Branson's SSD double-time before deployment

---

## Coaching Threshold (Hari/Caleb monitor this — not Ilma)

If student accuracy drops below 70% on PP100 or scores below 50% on the FRQ --> Hari/Caleb arrange coaching call with Eric's team.

> **Note for Ilma:** LEARN content (articles + videos) stays from HUMG20-v1. ALL quiz questions must come from AP Classroom course `c8265419-470e-450c-8113-bd2b31ae27af`. Verify that per-topic questions are correctly filtered by topic code. Branson's SSD double-time must be configured before deployment.
