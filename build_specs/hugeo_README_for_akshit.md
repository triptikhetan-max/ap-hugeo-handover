# AP Human Geography Specs — How to Read This

## File Structure

The AP Human Geography specs are split into **one file per course**, with a parent file for shared info.

| File | What It Is |
|---|---|
| **[ap_human_geography.md](ap_human_geography.md)** | **Parent file.** Student data, CED reference (exam structure, skill weights, unit weights), XP notes, PP100 settings, timeline, governance. Read this first — it's the context for everything. |
| [hugeo_mc1_dtm_application.md](hugeo_mc1_dtm_application.md) | **MC1: DTM Application** spec. Topics 2.1, 2.3, 2.4, 2.5, 2.8, 2.9. For Branson, Gus, Sydney. **THIS ONE HAS BEEN REVIEWED AND UPDATED — see changes below.** |
| [hugeo_mc2_boundary_types.md](hugeo_mc2_boundary_types.md) | **MC2: Boundary Types** spec. Topics 4.4-4.6. For Branson, Gus, Sydney. |
| [hugeo_mc3_centripetal_push_pull.md](hugeo_mc3_centripetal_push_pull.md) | **MC3: Centripetal/Centrifugal vs Push-Pull** spec. Topics 4.10, 2.10-2.11. For Branson, Zayen. |
| [hugeo_b1_mixed_topic_practice_tests.md](hugeo_b1_mixed_topic_practice_tests.md) | **B1: 4 Mini Practice Tests** spec. 30 MCQ each, all 7 units. For Branson, Zayen, Grady, Luca. Deploy AFTER R2. |
| [hugeo_b6_skill2_spatial.md](hugeo_b6_skill2_spatial.md) | **B6: Skill 2 Spatial Reasoning** spec. DEFERRED — do not build yet. |

---

## What Changed in MC1 (and Why)

The first build of MC1 was reviewed. Here's what was wrong and what the new structure is.

### Problems with the original build:

1. **Wrong structure** — It was built as a flat LEARN → CHECK → PP100 → FRQ. All 6 topics were dumped into one LEARN section, then one CHECK, then one PP100. Students had to absorb everything at once before practicing anything.

2. **Wrong question source** — The PP100 used 78 questions from a single HUMG20-v1 quiz (`HUMG20-qti104450-v1`). These are NOT AP Classroom questions. They were 4-choice instead of 5-choice, 90% were Topic 2.5 only, 97% tested Skill 1 only, and only 1 out of 78 had a stimulus. The CHECK used 6 questions from Princeton Review/Barron's.

3. **Wrong difficulty** — 83% of the PP100 questions were Remember/Understand level. These students need APPLICATION with stimuli. Gus scores 38.5% on DTM, Branson scored 0 on the DTM FRQ, Sydney misapplied DTM to South Africa. 78 recall questions on one topic doesn't fix any of their problems.

### New structure — Per-Topic Cycles:

Instead of one flat block, the course now cycles through each topic individually:

```
Topic 2.1: Video → Article → PP100/Quiz
Topic 2.3: Video → Article → PP100/Quiz
Topic 2.4: Video → Article → PP100/Quiz
Topic 2.5: Video → Article → PP100/Quiz
Topic 2.8: Video → Article → PP100/Quiz
Topic 2.9: Video → Article → PP100/Quiz
   ↓
Mini MCQ Practice Quiz (balanced across all 6 topics)
   ↓
FRQ (keep existing 2 FRQs)
```

**Why this is better:** Students learn one topic, then immediately practice it before moving to the next. This fixes Branson's recognition-retrieval gap — he can't coast through 6 topics of reading and then crash on a mixed test.

### New question source:

ALL quiz/practice questions must come from the **AP Classroom course** (`c8265419-470e-450c-8113-bd2b31ae27af` — "AP Classroom Scraping - Session 3"), AP Human Geo section.

- 5-choice (A-E) — proper AP format
- Tagged by topic code
- Maximize stimulus-based questions

**Do NOT use** HUMG20-v1 questions for quizzes. Those are not AP Classroom.

LEARN content (articles + Heimler videos) stays from HUMG20-v1.

### PP100 vs Fixed Quiz:

For each topic's quiz: we want PP100 (SmartScore to 100, 80% accuracy threshold). If the AP Classroom question bank doesn't have enough questions for that topic to run PP100, then use a fixed 20-question quiz instead.

### What to delete from current build:

- All 78 HUMG20-v1 PP100 questions
- All 6 CHECK questions (Princeton/Barron's)
- Ghost "Sample item" entries (status: tobedeleted)

### What to keep:

- All 6 Heimler videos
- All 6 lesson articles
- Both FRQs

### Cleanup:

- Fix "Practice Excercise" typo → "Practice Exercise"
- Verify images/tables render in Timeback student view

---

## Build Order

1. **R2 first** (Priority 1): MC1, MC2, MC3 — build in 3-4 days
2. **B1 after R2** (Priority 3): 4 practice tests — build in 5-7 days, deploy AFTER R2 is complete
3. **B6 deferred**: Don't build until R2 + B1 results are in
