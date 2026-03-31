# MC1: DTM Application — Fix List for Akshit

**Course:** AP HuGeo: DTM Application (`s4-r2-mc1-5ff6309d`)
**Date:** 2026-03-16
**Students:** Branson (AP 2, SSD double-time), Gus (AP 1), Sydney (AP 3)

---

## Summary

| Category | Count | What it means |
|---|---|---|
| **🐛 BUG** | **6 issues** | Broken — students will hit these and it won't work right |
| **📋 TRIVIAL** | **9 issues** | Could be better — not blocking but worth cleaning up |

---

## 🐛 BUG — Actually Broken, Must Fix

### BUG-1. 78 HUMG20 Questions Have Only 4 Choices (A-D)

**What:** The old HUMG20-v1 quiz (`HUMG20-qti104450-v1`) has 78 questions with only 4 answer choices. AP requires 5 (A-E). Students practicing with 4-choice questions are training for the wrong format.

**Action:** Delete the entire quiz `HUMG20-qti104450-v1` and all 78 items.

<details>
<summary>All 78 item IDs to delete (click to expand)</summary>

| # | Item ID | Stem Preview |
|---|---|---|
| 1 | `HUMG20-qti104450-v1-q1244186` | Of the following, which definition best describes the demographic transition mod... |
| 2 | `HUMG20-qti104450-v1-q1244187` | Select the statement which best identifies Stage 2 of the demographic transition... |
| 3 | `HUMG20-qti104450-v1-q1244189` | Why does Stage 5 show natural population decrease? |
| 4 | `HUMG20-qti104450-v1-q1244190` | Which statement demonstrates how birth rates change from Stage 1 to Stage 4... |
| 5 | `HUMG20-qti104450-v1-q1244191` | Choose the best option...Distinguish between Stage 3 birth rate and death rate... |
| 6 | `HUMG20-qti104450-v1-q1244193` | How does industrialization influence demographic change... |
| 7 | `HUMG20-qti104450-v1-q1244194` | Choose the option that best describes what the demographic transition model repr... |
| 8 | `HUMG20-qti104450-v1-q1244197` | What does the demographic transition model show about birth rate changes? |
| 9 | `HUMG20-qti104450-v1-q1244199` | Determine which option best explains how total population changes through the st... |
| 10 | `HUMG20-qti104450-v1-q1244200` | What happens to death rates when countries move into Stage 2 of the DTM? |
| 11-78 | `HUMG20-qti104450-v1-q1244201` through `HUMG20-qti104450-v1-q1244282` | Various DTM/epidemiological transition stems |

</details>

---

### BUG-2. 3 Ghost "Sample item" Placeholders Still in Build

**What:** Three test-mode placeholder entries are live in the course. Students might encounter them as empty/broken quizzes.

**Action:** Delete these:

| # | Test ID | Location | Items |
|---|---|---|---|
| 1 | `pcb-test-c40e6ed62a334945aed54e52309168d9` | CHECK section | 6 items (dupe of CHECK quiz) |
| 2 | Same test ID appears twice | CHECK section | Same 6 items |
| 3 | `pcb-test-8635b64557644c8daf6af866bc327572` | FRQ APPLY section | 1 item |

---

### BUG-3. 7 Questions Reference Maps/Pyramids That Aren't There

**What:** These questions say "look at the map" or "based on the population pyramid" but there's no image attached. Student sees a blank where the stimulus should be.

**Action:** Attach the correct stimulus image, or rewrite the stem to be standalone.

| # | Item ID | Quiz | What's Missing |
|---|---|---|---|
| 1 | `pcb-item-11e0015d-6104-4196-bdd5-f0775c6c50d6` | 2.1 | References "The map" with NASA source — NEEDS map |
| 2 | `pcb-item-f8faa71a-3e7f-4950-8233-d8dbe4668bb8` | 2.9 | References US Census Bureau population pyramid — NEEDS pyramid |
| 3 | `pcb-item-d0ccabc7-8a32-41ab-8666-e38642aadf04` | CHECK | "rectangle-shaped population pyramid" — could work standalone |
| 4 | `pcb-item-89a2f8e9-d813-42b5-b2ac-ced52b268406` | 2.3 | "population pyramid wide at the top" — could work standalone |
| 5 | `pcb-item-1e0400f1-9b99-4177-a026-af41f0f21e75` | 2.3 | "baby boomers...population pyramid" — could work standalone |
| 6 | `pcb-item-4e066b02-5487-4d99-ae0d-fd30030c8345` | 2.5 | Data table is IN the stem text — probably OK |
| 7 | `pcb-item-a18d40d5-fc82-437c-9be0-029c10baa575` | 2.8 | Data table is IN the stem text — probably OK |

**Priority:** #1 and #2 are the real bugs. #3-5 are Barron's items that get deleted via TRIVIAL-1 anyway. #6-7 are fine.

---

### BUG-4. 7 Questions Have the Wrong Marked Answer

**What:** The answer key is wrong — the "correct" answer isn't correct.

| # | Item ID | Quiz | Stem Preview |
|---|---|---|---|
| 1 | `pcb-item-e618c9f1-4de1-4684-af23-1ac234d8fbcb` | 2.1 | Throughout human history, world population has... |
| 2 | `pcb-item-f9ae7622-217e-4640-aad3-1b8c7bd35f91` | 2.1 | All of the following are true about the geographic center... |
| 3 | `pcb-item-b893c849-09e7-4650-b116-e295e3691cbc` | 2.4 | ______________ occurs when a population is adding a fixed percentage... |
| 4 | `pcb-item-fe1dfdee-c6a7-4675-9bd6-fc85e68229a1` | 2.4 | Life expectancy has increased... |
| 5 | `pcb-item-666e9578-d939-4292-bbbc-8641ca1235d5` | 2.5 | Carrying capacity is a function of... |
| 6 | `pcb-item-10e8ce26-6442-4b1f-a27d-17d924088e66` | 2.8 | India and China are the world's two most populous countries... |
| 7 | `HUMG20-qti104450-v1-q1244280` | HUMG20 quiz | Choose the best option...Distinguish between... |

**Note:** 6 of 7 are Barron's/Princeton items (deleted via TRIVIAL-1) or HUMG20 items (deleted via BUG-1). After those deletions, recheck remaining AP Classroom items.

---

### BUG-5. FRQ Title Typo: "Practice Excercise"

**What:** The FRQ quiz is titled "Practice Excercise" — misspelled.

**Action:** Rename test `s4-r2-mc1-5ff6309d-frq-test` to "Practice Exercise".

---

### BUG-6. Branson's SSD Double-Time Not Configured

**What:** Branson has SSD accommodation requiring double-time (+100%). If this isn't set up, his timed components are unfairly short.

**Action:** In Timeback admin:
- FRQ timer: standard 25 min → **Branson gets 50 min**
- PP100 timed sessions: double standard time
- Verify Branson's profile has SSD flag set

---

## 📋 TRIVIAL — Not Broken, Just Not Great

### TRIVIAL-1. 29 Questions From Prep Books Instead of AP Classroom

**What:** Spec says AP Classroom questions only. 29 items are from Princeton Review or Barron's. They're not "wrong" — they're just not official AP material. Could be weaker quality.

**Action:** Delete and replace with AP Classroom items when sourcing new questions. Low urgency.

| Section | Count | Sources |
|---|---|---|
| CHECK quiz | 6 items | Princeton Ch.4, Barron's Ch.2 |
| Topic 2.1 | 4 items | Barron's, Princeton Review |
| Topic 2.3 | 3 items | Barron's |
| Topic 2.4 | 6 items | Barron's, Princeton Review |
| Topic 2.5 | 6 items | Barron's, Princeton Review |
| Topic 2.8 | 3 items | Barron's, Princeton Review |
| Topic 2.9 | 1 item | Princeton Review |

---

### TRIVIAL-2. 28 Duplicate Question Stems

**What:** Same question appears in multiple quizzes. Not broken, but wastes student practice time — they see the same question twice and it inflates their accuracy.

**Action:** For each pair, keep one copy and delete the duplicate. Many of these are HUMG20 copies that get deleted via BUG-1 anyway.

---

### TRIVIAL-3. Answer Position Bias in 3 Quizzes

**What:** In some quizzes, the correct answer is disproportionately in one position (e.g., answer C is correct 40% of the time). Test-savvy students can pick up on the pattern.

**Action:** When rebuilding quizzes, randomize correct answer position evenly across A-E (~20% each).

---

### TRIVIAL-4. 17 Debatable Answer Questions

**What:** Some questions have a "correct" answer that's arguable — another choice could also be defended. Not wrong per se, just not cleanly unambiguous.

**Action:** Review when time allows. Low priority — these mimic real AP exam ambiguity.

---

### TRIVIAL-5. Topics 2.8 and 2.9 Are Thin (10 items each)

**What:** Spec says 20-question quizzes for topics without enough PP100 items. Topics 2.8 and 2.9 only have 10 items each — half the target.

**Action:** Source more AP Classroom questions for these topics.

---

### TRIVIAL-6. Low Stimulus Coverage (24%)

**What:** Only 48/200 MCQs have data tables, maps, or images. AP exam is ~40%+ stimulus-based. Students aren't getting enough practice with stimulus questions.

**Action:** Prioritize stimulus-based questions when sourcing replacements.

---

### TRIVIAL-7. 116 Questions Missing Feedback

**What:** When students get wrong answers, they get no explanation. Not broken, but weakens learning — especially for Gus (AP 1) who needs to understand WHY.

**Action:** Add feedback to per-topic quiz questions over time. Lowest priority.

---

### TRIVIAL-8. 2 Questions Use "All/None of the Above"

**What:** Real AP exam never uses these. Minor format issue.

**Action:** Replace with specific distractors.

---

### TRIVIAL-9. Topic Distribution Imbalanced

**What:** Topic 2.5 (DTM) has 70+ questions while 2.8/2.9 have ~10 each. After BUG-1 deletions this mostly fixes itself, but 2.8/2.9 still need more.

**Action:** Gets fixed naturally by BUG-1 deletion + TRIVIAL-5 sourcing.

---

## Quick Action Plan

| Step | What | Time | Category |
|---|---|---|---|
| 1 | Delete HUMG20 quiz + 78 items | 5 min | BUG-1 |
| 2 | Delete 3 ghost entries | 2 min | BUG-2 |
| 3 | Fix "Excercise" typo | 1 min | BUG-5 |
| 4 | Attach stimuli to 2 questions (#1, #2) | 15 min | BUG-3 |
| 5 | Configure Branson double-time | 5 min | BUG-6 |
| 6 | Delete 29 prep book items | 10 min | TRIVIAL-1 |
| 7 | Source new AP Classroom items for 2.8/2.9 | 1-2 hrs | TRIVIAL-5 |
| 8 | Clean up remaining duplicates | 20 min | TRIVIAL-2 |
| 9 | Add feedback (ongoing) | 2-3 hrs | TRIVIAL-7 |

**Bugs: ~30 min to fix all 6. Trivial: ~3-4 hrs for the full cleanup.**
