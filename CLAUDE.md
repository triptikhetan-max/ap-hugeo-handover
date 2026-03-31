# AP Mini-Course QC Project — Session Context

## Project Overview

Quality control and optimization of **AP Human Geography mini-courses** built on the Timeback/PowerPath platform (app.alphalearn.school). The primary course under review is **MC1: DTM Application** (`s4-r2-mc1-5ff6309d`).

The project has two main codebases:
1. **Course Puller** (`course_puller/pull.py`) — Extracts course content from the Timeback API into structured JSON
2. **QC Pipeline** (`qc_pipeline/`) — 6-layer quality validation system that checks structure, content quality, learning flow, and FRQ readiness

## Course: MC1 DTM Application

- **Course ID:** `s4-r2-mc1-5ff6309d`
- **Title:** AP HuGeo: DTM Application
- **Live URL:** `https://app.alphalearn.school/course/s4-r2-mc1-5ff6309d`
- **Students:** Branson (AP 2, SSD double-time), Gus (AP 2), Sydney (AP 3)
- **Content:** 8 quizzes, 6 articles, 6 Heimler videos, 119 questions (117 MCQ + 2 FRQ), 55 stimuli

### Course Structure (What Students See)
1. Topic 2.1: Population Distribution (Video → Article → Quiz 14 items)
2. Topic 2.3: Population Composition (Video → Article → Quiz 17 items)
3. Topic 2.4: Population Dynamics (Video → Article → Quiz 26 items)
4. Topic 2.5: The DTM (Video → Article → Quiz 21 items)
5. Topic 2.8: Women & Demographic Change (Video → Article → Quiz 10 items)
6. Topic 2.9: Aging Populations (Video → Article → Quiz 10 items)
7. Mini MCQ Practice Quiz (Mixed topics, 18 items, all AP Classroom)
8. FRQ APPLY (2 FRQs: Japan pyramid 7pts + Africa data table 5pts)

### Student Profiles (from `course_puller/output/s4-r2-mc1-5ff6309d/students.json`)
- **Gus** (AP 2, target 3, Layer 1): DTM accuracy 38.5%, doesn't KNOW the content. Course teaches from scratch.
- **Branson** (AP 2, target 3, SSD, Layer 2): 32-point recognition-retrieval gap (88% topic → 56% unit). Knows content but can't retrieve under pressure.
- **Sydney** (AP 3, target 4, Layer 2): Misapplied DTM to South Africa. Knows vocabulary, applies it wrong. Needs application practice.

## Critical Bug List (for Akshit)

Full details in `qc_pipeline/reports/mc1_fixes_for_akshit.md`. Summary:

### 4 BUGs (Must Fix, ~35 min total)
1. **BUG-1:** 4 questions reference stimuli not attached (map/graph/pyramid missing). Items: `pcb-item-11e0015d` (2.1), `pcb-item-89a2f8e9` (2.3), `pcb-item-1e0400f1` (2.3), `pcb-item-01818f1f` (2.4). **CAVEAT:** The NASA map in 2.1 renders fine on live despite `stimulus_id: None` in pulled data — our puller may not capture platform-level stimulus attachments. Some of these 4 may be false positives. Two of the 2.3 items are conceptual questions that may not actually need a stimulus image.
2. **BUG-2:** 7 questions have NO correct answer marked (all `isCorrect: false`). Akshit un-marked wrong answers but didn't set correct ones. **CONFIRMED on live** — "Throughout human history, world population has..." marks correct answer D as WRONG. All 7 are Barron's source. Exact fix details with file, index, and correct choice in `mc1_fixes_for_akshit.md`.
3. **BUG-3:** FRQ quiz titled "Practice Excercise" (typo). Students see "FRQ Practice" in breadcrumb — typo only in internal metadata.
4. **BUG-5:** "Carrying capacity" question has typo "echnology" AND choice E says "(A), (B), and (D)" which breaks if choices are randomized. Fix: rewrite choice E to "technology, natural resources, and limiting factors".

### 2 NOTEs (Already deleted, confirm cleanup)
- PP100 Mastery Practice (78 ced_llm items) — `tobedeleted`, blank page on live
- CHECK section + ghost Sample items — `tobedeleted`, invisible to students

### 7 TRIVIALs (Not blocking)
- 28 duplicate stems, answer position bias, debatable answers, thin topics 2.8/2.9, missing feedback on 116 questions, "all/none of the above" in 2 questions

### Bonus Finding
- Question `pcb-item-666e9578` has typo "echnology" instead of "technology" in choice A

## Key Technical Discovery: `tobedeleted` Filtering

The PowerPath API returns ALL resources including deleted ones. The `componentResource.status` field in `01_syllabus.json` has values `active` or `tobedeleted`.

**Fix applied in `pull.py` lines 299-318:**
```python
# Extract resources (skip tobedeleted)
for cr in comp.get("componentResources", []):
    cr_status = cr.get("status", "active")
    if cr_status == "tobedeleted":
        continue
    # ... process resource

# Recurse into sub-components (skip tobedeleted)
for sub in comp.get("subComponents", []):
    if sub.get("status") == "tobedeleted":
        continue
```

Before fix: 12 quizzes, 202 questions (including 78 dead ced_llm items). After fix: 8 quizzes, 119 questions (matching live course).

## Course Puller

### Location
`course_puller/pull.py` (~872 lines)

### What It Does
- Authenticates to Timeback API via OAuth2 (Cognito)
- Fetches full course syllabus, quizzes, questions, stimuli, videos
- Outputs 8 JSON files + summary

### API Details
- Base: `https://api.alpha-1edtech.ai`
- QTI API: `https://qti.alpha-1edtech.ai/api`
- Auth: OAuth2 client-credentials flow
- Key endpoints: `/powerpath/syllabus/{course_id}`, `/assessment-tests/{test_id}`, `/assessment-items/{item_id}`, `/stimuli/{stim_id}`

### Output Files (in `course_puller/output/s4-r2-mc1-5ff6309d/`)
| File | Content | Size |
|------|---------|------|
| `01_syllabus.json` | Raw API course tree with `componentResource.status` fields | 44 KB |
| `02_course_tree.json` | Simplified hierarchy with resource summaries | 7 KB |
| `03_quizzes.json` | All quizzes/tests with item lists | 14 KB |
| `04_assessment_banks.json` | Bank containers (empty for MC1) | — |
| `05_all_questions.json` | 119 questions with full content | 265 KB |
| `06_all_stimuli.json` | 55 stimuli with HTML/text | 356 KB |
| `07_all_videos.json` | 6 video references | 4 KB |
| `08_summary.json` | Statistics and errors | 0.4 KB |
| `students.json` | Student profiles | 1 KB |

### Run Command
```bash
python3 -m course_puller \
  --client-id 3haed1usvs2t29lhbtmk7dbho1 \
  --client-secret jamgvsdbus38c6iej5g7habom75toekcpvdsv79bogmph2ctf3u \
  --course-id s4-r2-mc1-5ff6309d
```

## QC Pipeline

### Location
`qc_pipeline/` (Python package)

### Architecture — 6 Layers
| Layer | File | What It Checks | Needs API? |
|-------|------|----------------|------------|
| L1 | `layer1_structural.py` | Missing stems, wrong choice count, no correct answer, duplicate IDs/stems, missing stimulus, ghost entries, empty quizzes | No |
| L2 | `layer2_quality.py` | "All/none of above", short/long stems, duplicate choices, auto-generated sources, answer position bias | No |
| L3 | `layer3_alignment.py` | Learning flow (video+article→quiz alignment), student outcome alignment, FRQ readiness | Yes (Claude Sonnet) |
| L4 | `layer4_course.py` | Topic concentration, skill distribution, stimulus coverage, source mix, difficulty distribution | No |
| L5 | `layer5_frq.py` | FRQ count, part count, task verbs, verb progression, type coverage, rubric existence | No |
| L6 | `layer6_content.py` | Article word counts, video URL validation, article quality, empty stimuli | No |

### Key Files
- `__main__.py` — CLI entry point
- `loader.py` — Loads 8 JSON files, normalizes metadata, builds indexes and TopicGroups
- `models.py` — Finding, QuestionInfo, StimulusInfo, NormalizedMetadata, TopicGroup
- `report.py` — Markdown + JSON report generation
- `config.py` — Thresholds and constants
- `api_client.py` — Claude API wrapper with caching, rate limiting, cost tracking
- `prompts/` — L3 prompt templates (learning_flow.py, student_outcome.py, frq_readiness.py)
- `build_dashboard.py` — Interactive HTML dashboard generator
- `transcripts/` — 12 Heimler video transcripts (used by L3 prompts)

### Run Command
```bash
# Full QC (all layers, no API — skip L3)
python -m qc_pipeline course_puller/output/s4-r2-mc1-5ff6309d/ --layers L1,L2,L4,L5,L6

# Full QC with API (needs ANTHROPIC_API_KEY)
python -m qc_pipeline course_puller/output/s4-r2-mc1-5ff6309d/ --students course_puller/output/s4-r2-mc1-5ff6309d/students.json

# Custom layers
python -m qc_pipeline /path/to/course --layers L1,L2 --no-api
```

### Latest QC Report
`qc_pipeline/reports/qc_s4-r2-mc1-5ff6309d_20260318_004352.md`
- 4 errors (all missing_stimulus — but some are false positives, see BUG-1 caveat above)
- 28 warnings
- 157 info
- L3 skipped (no ANTHROPIC_API_KEY)

## Key Reports (in `qc_pipeline/reports/`)

| File | What |
|------|------|
| `mc1_fixes_for_akshit.md` | **THE FIX LIST** — 4 bugs, 2 notes, 7 trivial with item IDs and action plan |
| `mc1_comprehensive_review.md` | Deep pedagogical analysis — student diagnosis, section walkthrough, what's working/broken |
| `student_plans_mc1.md` | Individual student plans for Eric |
| `mc1_frq_structure_review.md` | FRQ format analysis (needs 3 FRQs, has 2; missing Type 1 and Type 3) |
| `gap_analysis_s4_vs_real_exam.md` | MC1 vs real AP exam comparison |
| `mcq_deep_analysis.md` | Question characteristics analysis |
| `prep_books_content_review.md` | Princeton/Barron's question validation |

## Live Course Verification Findings

We walked through the full student experience on the live course (app.alphalearn.school):

### Completed
- **Topic 2.1:** Video loads (Heimler YouTube embed), article renders, quiz completed to PowerPath Score 100 (14 questions answered)
- **Wrong answer confirmed LIVE:** Question about "Throughout human history, world population has..." — selected correct answer D, system marked WRONG and showed A as correct. PowerPath Score dropped 42→38.
- **NASA map stimulus:** `pcb-item-11e0015d` shows `stimulus_id: None` in pulled data but the map **renders correctly on live course**. Our pipeline's missing_stimulus detection has false positives — stimuli may be attached at platform level without being captured by our puller.
- **PP100 Mastery Practice:** Confirmed blank/dead on live course (renders empty page)

### Not Yet Completed
- Topics 2.3-2.9 walkthrough
- Mini MCQ Practice Quiz
- FRQ submission and grading check
- Verification of remaining BUG-1 items on live (especially `pcb-item-01818f1f` graph in 2.4)
- Videos on live (verify Heimler YouTube embeds load)

## Question About "All of the Above" Randomization

**OPEN ISSUE:** Questions with "All of the above" or "Both B and D" style choices will BREAK if the platform randomizes choice order. If choice E says "All of the above" but choices A-D get shuffled, the reference becomes meaningless. Need to check:
1. Does PowerPath randomize choice order?
2. If so, are these questions flagged to prevent randomization?
3. If not, these questions need to be rewritten or removed.

Related: The AP exam spec says questions should NOT have "All of the above" / "None of the above" choices.

## Metadata Coverage Issue

Most questions lack proper tagging:
- Unit tags: 7/119 (6%)
- Topic tags: 7/119 (6%)
- Skill tags: 7/119 (6%)
- Source tags: 40/119 (34%)
- Difficulty: 100% tagged

Question sources: 93 AP Classroom + 15 Barron's + 9 Princeton + 1 AP Released Exam + 1 ced_llm FRQ.

## Metadata Schemas (handled by `loader.py`)

The pipeline normalizes multiple schema formats:
- **New (MC2):** "Unit And Topic", "Skill Category And Skill"
- **Old (MC1):** cedUnit, cedTopic, cedSkill, topicName, skillName
- **HUMG20:** unit, topic_code, skill_number, topic_name
- **Minimal AP Classroom:** "course content", "practice and skill", "source", "difficulty"

## Other Root Directory Files

| File | Purpose |
|------|---------|
| `analyze_mc1_course.py` | Course mapper — reads 8 JSONs, outputs `mc1_course_map.json` |
| `analyze_barrons_epub.py` | Barron's prep book content analyzer |
| `analyze_princeton_epub.py` | Princeton prep book content analyzer |
| `mc1_course_map.json` | Full course structure map (384 KB) |
| `mc1_analysis_output.txt` | Course analysis console output (238 KB) |
| `portfolio.html` | Tripti's work portfolio (Aug 2024 - Mar 2026) |
| `dashboard.html` | Harvard HGSE LDIT dashboard (298 KB) |

## Akshit's Exported Data Validation (Mar 18)

Akshit shared `Course 1 - DTM Application` zip with 7 quiz JSON files (116 MCQs, no FRQs). Validated against our API pull:
- **95 questions matched** between datasets
- **0 answer key conflicts** where both have answers marked
- **7 questions have NO correct answer** — all Barron's source. Akshit removed wrong markings but didn't set correct ones
- **1 question removed** from 2.3 (France/India pyramids, `pcb-item-4e0e95b4`)
- **2 questions reformatted** in 2.4 (same content, different HTML)
- **63/116 have feedback** in Akshit's data (vs our pull showing 116 missing)
- Data file location: `akshit_update/Course 1 - DTM Application/final/`

## Pending Work

1. **Continue live course walkthrough** — Topics 2.3-2.9, Mini MCQ, FRQ submission + grading
2. **Re-evaluate BUG-1** — Some "missing stimulus" errors are false positives (stimulus renders on live despite missing in pulled data)
3. **Update fixes file** with all live verification results
4. **Check "all of the above" randomization issue**
5. **Build MC1 review dashboard** (Step 15 in original plan)
6. **Verify remaining BUG-2 wrong answers on live** — Only one confirmed so far
7. **Check FRQ grader** — Submit response and verify grading works

## Learning Framework

Tripti thinks about learning in three layers:
- **Layer 1:** Does the student KNOW the content? (articles, videos teach this)
- **Layer 2:** Can they DO the disciplinary moves? (stimulus questions, data analysis)
- **Layer 3:** Can they perform under exam conditions? (timed tests, FRQs)

Courses should build all three layers in order. QC verifies this flow.
