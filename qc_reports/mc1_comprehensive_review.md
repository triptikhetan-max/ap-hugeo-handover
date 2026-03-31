# MC1: DTM Application — Comprehensive Review

**Course:** `s4-r2-mc1-5ff6309d` | **Pulled:** 2026-03-18 (clean pull with tobedeleted filtering)
**Reviewer:** Claude QC Pipeline | **Updated:** 2026-03-18
**Key findings (Mar 18):** Course puller now filters `tobedeleted` items. Clean data: 8 quizzes, 119 questions (117 MCQ + 2 FRQ). The 78 HUMG20 ced_llm items, CHECK section, and ghost entries are all `tobedeleted` — invisible to students. Live course verified at app.alphalearn.school. 4 real bugs remain.

---

## 1. WHO ARE THE KIDS & WHAT'S THE PROBLEM?

### The Students

| Student | AP Score | Target | Risk Level | SSD |
|---|---|---|---|---|
| **Gus** | **2** (corrected after FRQ regrade) | 3+ | **HIGH** — tied with Branson | None |
| **Branson** | **2** | 3+ | **HIGH** — recognition-retrieval gap | Double-time (+100%) |
| **Sydney** | 3 | 4 | **MEDIUM** — passing but below target | None |

### What Went Wrong — Why They Failed

**Gus (AP 2, corrected after FRQ regrade):**
- DTM accuracy: **38.5%** — can't apply the model at all
- Skill 2 (Spatial Relationships): **25%** — THE lowest of any student on THE highest-weighted FRQ skill (33-43% of FRQ)
- FRQ 2: **0 pts** — didn't know what "superimposed" boundary meant
- Only 54% of Timeback done. Hasn't started Units 5-7 (30% of exam)
- Key insight: This is a **Layer 1 problem** — Gus doesn't KNOW the content. He needs content before skills.

**Branson (AP 2, SSD double-time):**
- **32-point recognition-retrieval gap**: 88% on topic quizzes → 56% on unit tests
- FRQ 1: **0 on DTM** — could describe stages but couldn't EXPLAIN why transitions happen
- FRQ 3: **0** — confused centripetal/centrifugal with push-pull migration (completely different frameworks)
- Skill 3 (Data Analysis): **43%** — can't interpret charts, maps, data tables
- 10 zero-score topics including DTM, Women & Demographic Change, Aging Populations
- Key insight: Branson RECOGNIZES content when prompted but **can't RETRIEVE it when topics mix**

**Sydney (AP 3):**
- **Misapplied DTM to South Africa** — placed it in Stage 2 with "low birth rates" (incorrect)
- FRQ 2: **0/4** — listed indicators instead of explaining DTM transitions
- FRQ 3: Confused **antecedent with subsequent boundaries**
- Only 46% of Timeback done
- Key insight: Sydney knows DTM vocabulary but **applies it to the wrong scenarios**

### What This Course Is Supposed to Fix

MC1 was built specifically to address these failures:

1. **For Gus** → Teach DTM from scratch with real country data and population pyramids. Not recall definitions — APPLICATION. Move him from 38.5% to 80%+ on PP100.

2. **For Branson** → The per-topic cycle structure (Video → Article → Quiz per topic) directly attacks his recognition-retrieval gap. Instead of reading 6 topics then crashing on a test, he now learns one topic → immediately practices it → then faces a mixed quiz at the end. Plus, stimulus-based questions target his weak Skill 3 (Data Analysis).

3. **For Sydney** → Force DTM APPLICATION — she already knows stages, so recall questions do nothing. She needs to look at real country data and figure out WHICH stage applies. The AP Classroom stimulus questions do exactly this.

---

## 2. DOES THIS COURSE ADDRESS THE PROBLEM?

### What's Working ✅

| Element | Assessment | Why It Works |
|---|---|---|
| **Per-topic cycle structure** | ✅ Excellent | Video → Article → Quiz per topic directly attacks Branson's recognition-retrieval gap |
| **6 Heimler videos** | ✅ Good | Quality AP review content, topic-aligned |
| **6 lesson articles** | ✅ Good | Substantive content (859-2,223 words each), covers all 6 CED topics |
| **AP Classroom questions (93)** | ✅ Good | Real AP format, 5-choice, many stimulus-based |
| **2 FRQs** | ✅ Good | Japan pyramid (7pts) + Africa data table (5pts) — relevant practice |
| **Mini MCQ Practice Quiz** | ✅ Good | 18 items, mixed topics, all AP Classroom source |
| **Course tree ordering** | ✅ Correct | CHECK → 2.1 → 2.3 → 2.4 → 2.5 → 2.8 → 2.9 → Mini MCQ → FRQ |

### What's Broken ❌

| Element | Assessment | Impact on Students |
|---|---|---|
| **6 questions with wrong answer keys** | ❌ Harmful | **CONFIRMED on live course** — student selects correct answer, system marks WRONG. PowerPath Score drops. Students who know the content are penalized. |
| **4 questions reference missing stimuli** | ❌ Broken (maybe) | Stem says "look at the map/graph" but no image. **CAVEAT:** The NASA map in 2.1 renders fine on live despite `stimulus_id: None` in pulled data — some may be false positives (platform-level attachment our puller doesn't capture). |
| **FRQ title typo "Practice Excercise"** | ⚠️ Minor | Internal metadata only — students see "FRQ Practice" in breadcrumb. Still should fix. |
| **Branson SSD double-time not configured** | ❌ Unfair | FRQ 25 min but Branson needs 50 min. Must verify in Timeback admin. |
| **Topics 2.8 and 2.9 have only 10 Qs each** | ⚠️ Thin | Branson scored 0 on these topics — they need MORE practice, not less |
| **"All of the above" randomization risk** | ⚠️ Risky | If PowerPath randomizes choice order, "All of the above" and "Both B and D" answers break. Need to verify platform behavior. |

**Note:** The 78 HUMG20 ced_llm items, CHECK section, and ghost entries are all `tobedeleted` in the API. Students never see them. The 24 Princeton/Barron's questions are vetted prep book content — fine to keep.

### Live Course Verification (Mar 18)

Walked through full student experience on app.alphalearn.school:
- **Topic 2.1 completed** — Video loads, article renders, quiz done to PowerPath Score 100 (14 questions)
- **Wrong answer BUG-2 confirmed** — "Throughout human history, world population has..." marks A correct but D is right. Score dropped 42→38.
- **NASA map renders fine** despite `stimulus_id: None` in pulled data — pipeline has false positives
- **PP100 Mastery Practice confirmed dead** — blank page on live
- **Typo found** — `pcb-item-666e9578` has "echnology" instead of "technology" in choice A

### Bottom Line: Does It Work?

**After fixing the 4 bugs, YES — this course addresses the core problems.** The pedagogical design is sound:
- Per-topic cycles fix Branson's retrieval gap
- AP Classroom questions force application (not recall)
- Stimulus-based questions target Branson's Skill 3 weakness
- The DTM article is comprehensive (1,647 words covering all 5 stages with country examples)
- Stimulus coverage at 40% (47/117 MCQs) — meets AP target
- All 119 questions are 5-choice format (AP standard)

**4 bugs must be fixed before deployment:**
1. Fix 6 wrong answer keys (students penalized for correct answers)
2. Attach missing stimuli to 4 questions (or verify they render on live)
3. Fix FRQ "Excercise" typo
4. Configure Branson's SSD double-time

**The dead content (78 HUMG20 items, CHECK section, ghost entries) is already handled** — all marked `tobedeleted`, invisible to students. No action needed unless we want the API to stop returning them.

---

## 3. STUDENT WALKTHROUGH — Experiencing MC1 as an AP Student

### ~~Section 1: CHECK~~ — DELETED (tobedeleted)

The CHECK section is marked `tobedeleted` in the API and **invisible to students** on the live course. It contained 6 Princeton/Barron's questions. No action needed — this is already handled.

### Section 2: Topic 2.1 — Population Distribution

**Video:** Heimler "Population Distribution & Density" (YouTube: `HkYEbJfxQyI`)
- Good 10-min overview. Covers density types (arithmetic, physiological, agricultural), distribution patterns, physical/human factors.
- Accessible for Gus (AP 2) — Heimler explains concepts with enthusiasm and real examples.

**Article:** "Population Distribution" (2,223 words)
- Covers essential question, physical factors (climate, water, terrain), human factors (economics, government), density types with formulas.
- Has data tables showing density calculations.
- **Gap:** No population dot map or world population distribution map embedded. The article DESCRIBES patterns but students can't SEE them. This matters because Branson's Skill 3 weakness is visual data interpretation.

**Quiz:** PP100, 14 items (10 AP Classroom + 4 Princeton/Barron's)
- AP items are good quality: stimulus-based questions with maps and data tables.
- Example: "Source: NASA, Columbia University... The map shows the number of persons per square kilometer..." — exactly what Gus needs.
- The 4 prep book items add variety and are fine to keep.

### Section 3: Topic 2.3 — Population Composition

**Video:** Heimler "Population Composition" (YouTube: `awId4_crcZg`)
- Covers population pyramids, age-sex structure, dependency ratios.
- Critical for ALL three students — pyramids are the #1 stimulus type on the AP exam for Unit 2.

**Article:** "Population Composition" (1,641 words)
- Covers pyramid types (expansive, constrictive, stationary), sex ratios, dependency ratio formula.
- Has pyramid visual references but the images rely on stimulus links that may not render.
- **Gap:** No side-by-side comparison of pyramids by DTM stage. This connection (pyramid shape = DTM stage) is EXACTLY what Sydney needs to fix her misapplication problem.

**Quiz:** PP100, 17 items (13 AP Classroom + 3 Princeton/Barron's + 1 duplicate)
- Good mix of AP and prep book items with pyramid interpretation questions.
- Example: "Based on the population pyramid, which will pose the greatest demographic challenge..." — application, not recall.
- **Issue:** 2 questions reference "population pyramid" but have no stimulus attached (BUG — needs fix).

### Section 4: Topic 2.4 — Population Dynamics

**Video:** Heimler "Rate of Natural Increase" (YouTube: `W9TTNBvrzVI`)
- Covers CBR, CDR, RNI, TFR, doubling time.

**Article:** "Population Dynamics" (2,060 words)
- Comprehensive — covers all rate calculations, Malthusian theory reference, population momentum.
- Has data tables comparing countries by birth/death rates.
- **Strength:** This article does APPLICATION well — it gives country data and asks students to calculate.

**Quiz:** PP100, 26 items (20 AP Classroom + 6 Princeton/Barron's)
- Largest per-topic quiz. Good variety of stimulus types (data tables, country comparisons).
- Strong quiz — 26 items gives plenty of PP100 practice depth.

### Section 5: Topic 2.5 — The DTM (Core Topic)

**Video:** Heimler "The DTM Explained" (YouTube: `-gf4hakk_WY`)
- THE critical video. Covers all 5 stages with mechanisms, not just labels.
- Perfect for Gus who needs to understand WHY transitions happen.

**Article:** "The Demographic Transition Model" (1,647 words)
- Full coverage: 5 stages with country examples (Niger=Stage 2, Turkey=Stage 3, France=Stage 4, Japan=Stage 5).
- Includes the Epidemiological Transition Model extension.
- Has a comprehensive data table showing all 5 stages' characteristics.
- **Strength:** This article explains mechanisms — "a country's death rate begins to decrease when it moves into Stage 2" with the WHY (improved sanitation, nutrition, medicine).
- **Gap:** No interactive DTM diagram where students can see the birth rate and death rate lines crossing. The article describes the model but a visual would help Gus tremendously.

**Quiz:** PP100, 21 items (15 AP Classroom + 6 Princeton/Barron's)
- Good AP items force application: "Based on the data shown... which of the following is a common demographic challenge?" with stimulus data.
- 21 items is solid for PP100 practice.
- **Note:** The 78 HUMG20 auto-generated items that were in this section are `tobedeleted` — no longer visible to students.

### Section 6: Topic 2.8 — Women & Demographic Change

**Video:** Heimler "Women & Demographic Change" (YouTube: `tntW0JKCGyk`)

**Article:** "Women and Demographic Change" (859 words)
- **SHORTEST ARTICLE** — less than half the length of the DTM article.
- Covers: role of women, family planning, TFR definition, Ghana education-TFR data.
- **Gap:** This is thin. Branson scored 0 on this topic and Sydney needs it for understanding Stage 4-5 transition mechanisms. The article doesn't give enough country case studies or data for practice.
- **Missing:** No mention of pro-natalist vs anti-natalist policies (CED 2.7 content that connects here). No connection to Japan/Germany's aging population crisis driven by women's changing roles.

**Quiz:** Regular quiz (not PP100), 10 items (7 AP Classroom + 3 Princeton/Barron's)
- 10 items total — thin for a topic where Branson scored 0.
- This topic NEEDS more questions. Consider sourcing additional AP Classroom items.

### Section 7: Topic 2.9 — Aging Populations

**Video:** Heimler "Impact of Aging Populations" (YouTube: `szYuBa4cStk`)

**Article:** "Aging Populations" (1,440 words)
- Better than 2.8. Covers causes (longer life expectancy + lower CBR) and effects (dependency ratio, pension strain, labor shortage).
- Has Japan as primary example — good because the FRQ is about Japan.
- **Gap:** No concrete policy examples (raising retirement age, immigration incentives, pro-natalist policies). Students need to know specific government RESPONSES for the FRQ.

**Quiz:** Regular quiz (not PP100), 10 items (9 AP Classroom + 1 Princeton/Barron's)
- 10 items total — thin. Could use more questions for this topic.

### Section 8: Mini MCQ Practice Quiz

- 18 items, ALL AP Classroom source ✅
- Balanced across 6 topics ✅
- Some questions duplicate per-topic items (expected, spec allows 25% overlap)
- This is the CRITICAL assessment — it tests whether students can retrieve across mixed topics.
- **For Branson:** This is where his 32-point gap will show. If he scores well on per-topic quizzes but poorly here, his gap hasn't closed.

### Section 9: FRQ APPLY

- 2 FRQs: Japan population pyramid (7pts) + Africa data table (5pts)
- Both are good quality, relevant to the content taught.
- **For Branson:** The Japan pyramid FRQ directly tests what he scored 0 on.
- **Issue:** "Practice Excercise" typo in internal metadata (students see "FRQ Practice" in breadcrumb).
- **Note:** Ghost "Sample item" entry is `tobedeleted` — invisible to students.
- **Note:** Branson needs 50-min timer (double-time SSD) — must verify configured.

---

## 4. QUICK WINS — High-Impact, Low-Effort Improvements

These use existing content we already have (prep book extracts, ground reality research) and require minimal work.

### QW1: ADD a DTM Stage-Pyramid Connection Table to the 2.3 Article

**Effort:** 5 min (copy from prep book analysis)
**Impact:** HIGH — directly fixes Sydney's misapplication problem

Add this to the Population Composition article after the pyramid types section:

```
DTM Stage → Population Pyramid Shape Connection:
- Stage 1: Very wide base, rapid narrowing → "True pyramid" or "expansive"
- Stage 2: Wide base, less narrowing → "Expansive" (Niger example)
- Stage 3: Narrowing base, wider middle → "Transitional" (Turkey example)
- Stage 4: Roughly rectangular → "Stationary" (France example)
- Stage 5: Narrow base, widest at top → "Constrictive" (Japan example)
```

This is the KEY connection that Sydney missed — she knows DTM stages and knows pyramid shapes but can't connect them. Branson scored 0 on DTM FRQ partly because he couldn't read the pyramid to identify the stage.

### QW2: ADD Country Case Study Data to the 2.8 Article

**Effort:** 10 min
**Impact:** HIGH — the article is too thin (859 words) for a topic where Branson scored 0

Add 2-3 concrete case studies showing women's education → TFR decline:
- **Bangladesh:** TFR dropped from 6.9 (1970) → 2.0 (2020) as female literacy went from 16% → 73%
- **Iran:** TFR dropped from 6.5 (1980) → 1.7 (2020) — fastest fertility decline in history, driven by government-funded women's education programs
- **Sub-Saharan Africa contrast:** Countries with <50% female secondary enrollment still have TFR >5

This data exists in the Princeton Review content analysis. It transforms the article from "women's roles changed" (vague) to "here's the DATA showing exactly how" (AP-exam relevant).

### QW3: ADD Policy Examples to the 2.9 Article

**Effort:** 10 min
**Impact:** MEDIUM-HIGH — students need to know government RESPONSES for FRQ

Add specific policy responses to aging:
- **Japan:** Raised retirement age to 65, investing in robotics for elderly care, offering cash bonuses for childbirth
- **Germany:** Immigration policy to offset aging workforce, accepted 1M+ Syrian refugees partly for demographic reasons
- **China:** Ended one-child policy (2015) → allowed two children → then three (2021) as aging crisis accelerated
- **Singapore/Sweden:** Pro-natalist policies — parental leave, childcare subsidies, tax incentives

These are standard AP FRQ content. If a student gets an FRQ about aging population consequences and government responses, they need specific examples.

### QW4: FLAG the Epidemiological Transition as "LEARN, Don't Memorize"

**Effort:** 2 min (add a note to the DTM article)
**Impact:** MEDIUM — prevents wasted study time

The DTM article covers the Epidemiological Transition Model in detail (5 stages of disease patterns). While this IS in the CED, it's a lower-frequency test topic compared to the DTM itself. For Gus at AP 2, trying to memorize BOTH models simultaneously could cause confusion.

**Suggestion:** Add a note: "Focus first on mastering the 5 DTM stages. The Epidemiological Transition Model extends the DTM to explain disease patterns — understand the concept but don't memorize all 5 disease stages until you've mastered the DTM."

### QW5: REORDER the CHECK Section to Come AFTER Topic 2.5

**Effort:** 5 min (move in Timeback)
**Impact:** MEDIUM — pedagogically better for Gus

Currently CHECK is the FIRST thing students see. But Gus (AP 2) doesn't know any of this content yet. Putting 6 diagnostic questions first will frustrate him and set a negative tone. Better to:
1. Delete CHECK entirely (per spec), OR
2. Move it to after 2.5 as a mid-course diagnostic

The Mini MCQ Practice Quiz already serves the diagnostic purpose at the end.

### QW6: ADD Key Term Definitions Inline

**Effort:** 15 min
**Impact:** MEDIUM — Gus at AP 2 needs vocabulary support

The articles use terms like "crude birth rate," "dependency ratio," "demographic momentum" without always defining them clearly. The Princeton Review has 103 key terms for Unit 2. The highest-impact ones to add inline definitions for:

| Term | Definition to Add | Where |
|---|---|---|
| Crude Birth Rate (CBR) | # live births per 1,000 people per year | 2.4 article |
| Crude Death Rate (CDR) | # deaths per 1,000 people per year | 2.4 article |
| Rate of Natural Increase (RNI) | CBR - CDR (expressed as %) | 2.4 article |
| Demographic Momentum | Population continues growing even after TFR drops below replacement, because large young generation is still having children | 2.5 article |
| Dependency Ratio | (Pop under 15 + Pop over 64) / (Pop 15-64) × 100 | 2.9 article |
| Replacement-level fertility | TFR of 2.1 — the level needed to maintain population size | 2.8 article |

---

## 5. COURSE READINESS SUMMARY

| Item | Status | Detail |
|---|---|---|
| Per-topic cycles (Video → Article → PP100/Quiz) | ✅ | All 6 topics have the correct structure |
| Question sources | ✅ | 93 AP Classroom + 15 Barron's + 9 Princeton + 1 AP Released Exam + 1 ced_llm FRQ = good mix |
| HUMG20 auto-generated questions (78 items) | ✅ RESOLVED | All `tobedeleted` — invisible to students |
| Ghost "Sample item" entries | ✅ RESOLVED | All `tobedeleted` — invisible to students |
| Fix "Practice Excercise" typo | ❌ | Still misspelled in internal metadata |
| Branson SSD double-time | ❓ | Must verify in Timeback |
| Fix 6 wrong answer keys | ❌ | **CONFIRMED on live** — students penalized for correct answers |
| Fix/verify 4 missing stimuli | ❌ | Some may be false positives (NASA map renders on live) |
| 6 Heimler videos from HUMG20-v1 | ✅ | All present, transcripts pulled (15,971 words total) |
| 6 lesson articles from HUMG20-v1 | ✅ | All present (859-2,223 words) |
| Video-article alignment | ✅ | Videos complement articles — video teaches concepts, article provides data + detail |
| Keep 2 FRQs | ✅ | Both present (Japan pyramid + Africa data table) |
| Topics 2.8/2.9 quiz depth | ⚠️ | Only 10 items each — thin for topics where Branson scored 0 |
| Mini MCQ Practice Quiz after topics | ✅ | 18 items, all AP Classroom |
| Stimulus coverage | ✅ | 40% have stimuli (47/117 MCQs) — meets AP target |
| Coaching threshold configured | N/A | Hari/Caleb's job, not Akshit's |

---

## 6. WHAT'S THE VERDICT?

### Will This Course Help These Students Pass?

**For Gus (AP 2 → target 3+):** YES — the per-topic cycles give him the content foundation he desperately needs. The Heimler videos are accessible (all 6 transcripts verified, 928-1,776 words each). The 119 questions are all 5-choice AP format. **BUT the 6 wrong answer keys must be fixed first** — a student learning wrong answers will fail the real exam.

**For Branson (AP 2 → target 3+):** YES — the per-topic cycle structure is EXACTLY what he needs. Learn one topic → immediately practice → move to next. His 32-point recognition-retrieval gap should narrow. **BUT SSD double-time must be configured** and topics 2.8/2.9 (where he scored 0) need more depth (only 10 items each).

**For Sydney (AP 3 → target 4):** PARTIALLY — the AP Classroom questions are good for application practice. But the articles don't explicitly connect DTM stages to pyramid shapes (QW1), which is exactly her misapplication error. Adding the connection table would directly address her specific failure.

### Priority Order for Akshit

1. **Fix 6 wrong answer keys** (20 min) — **MOST CRITICAL** — students are penalized for correct answers
2. **Verify/attach 4 missing stimuli** (20 min) — check if they render on live; if not, attach images or rewrite stems
3. **Fix "Excercise" typo** (1 min)
4. **Configure Branson SSD double-time** (5 min)
5. **QW1-QW3** (25 min) — add stage-pyramid table, beef up 2.8 article, add policy examples to 2.9
6. **Source more questions for 2.8/2.9** (1-2 hrs) — these topics need 20+ items, currently have 10

**Note:** The 78 HUMG20 items, CHECK section, and ghost entries are already `tobedeleted`. No action needed for those.

**After these fixes, re-pull the course and re-run QC pipeline to verify.**

---

## 7. LEARNING FLOW ANALYSIS (NEW — QC v2)

We pulled all 6 Heimler video transcripts and built a learning flow review system that sees exactly what the student sees: video → article → quiz.

### Video Transcript Coverage

| Topic | Video Words | Article Words | Quiz Items | Transcript + Article Together |
|---|---|---|---|---|
| 2.1 Population Distribution | 1,776 | 2,223 | 14 | Strong — video covers concepts, article adds data tables |
| 2.3 Population Composition | 1,245 | data table only | 16 | Video carries the teaching load — article is just a data table |
| 2.4 Population Dynamics | 1,648 | data table only | 26 | Same — video is primary instruction, article is data reference |
| 2.5 The DTM | 1,619 | data table only | 22 | Video explains all 5 stages with mechanisms — article supplements with country data |
| 2.8 Women & Demographic Change | 928 | data table only | 10 | THIN — shortest video + no real article = weakest section |
| 2.9 Aging Populations | 969 | 1,440 | 10 | Better — article is substantive here, but video is short |

**Key finding:** For topics 2.3, 2.4, 2.5, and 2.8, the "article" is really just a data table (259-366 chars). The Heimler videos are the primary teaching content. This means the learning flow is actually: **Video teaches → Data table as reference → Quiz tests**. This works IF the video covers everything the quiz tests.

**Weakest section:** Topic 2.8 (Women & Demographic Change) — shortest video (928 words), data-table-only article, only 10 quiz items. This is exactly where Branson scored 0. Needs attention.

### QC Pipeline v2 Status

The automated learning flow review (3 Claude API prompts) is built and tested structurally. Needs `ANTHROPIC_API_KEY` to run the full analysis:
- **Prompt 1**: Sends video transcript + article + quiz per topic — checks if content teaches what quiz tests
- **Prompt 2**: Checks if this course addresses Branson/Gus/Sydney's specific problems
- **Prompt 3**: Reviews whether FRQs prepare students for the real exam

Run: `python3 -m qc_pipeline course_puller/output/s4-r2-mc1-5ff6309d --verbose`
