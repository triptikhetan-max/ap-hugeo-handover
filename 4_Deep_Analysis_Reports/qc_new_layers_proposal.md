# QC Pipeline — New Layers Proposal

**Date:** 2026-03-16
**Current Pipeline:** 4 layers (L1 Structural, L2 Quality, L3 Content Alignment, L4 Course-Level)

---

## Gaps Found During MC1 Review

| Gap | Discovered When | Impact |
|---|---|---|
| No FRQ validation | FRQ 2 has 4 parts instead of 7 — went undetected | Students under-prepared for 7-part FRQs |
| No article depth check | Women & Demographic Change article is only 859 words | Thin content for a topic where Branson scored 0 |
| No student plan verification | No automated check that student plans exist or match spec | Risk of deploying without student context |
| No rubric existence check | Timeback doesn't store FRQ rubrics at all | FRQs deployed without scoring criteria |
| No cross-unit question check | FRQs should test across units, but no validation | FRQs may be too narrow |
| No video URL validation | YouTube URLs not verified as live | Videos may be dead links |

---

## Proposed New Layers

### Layer 5: FRQ Validation (No API needed)

Structural and content checks specific to FRQ (extended-text) questions.

| Check | Severity | What It Catches |
|---|---|---|
| `frq_part_count` | error | FRQ has fewer than 7 parts (A-G). AP standard is exactly 7 parts, 1 pt each |
| `frq_total_points` | error | FRQ total points != 7. All AP FRQs are worth exactly 7 points |
| `frq_type_coverage` | warning | Course missing FRQ Type 1 (no stimulus), Type 2 (one stimulus), or Type 3 (two stimuli) |
| `frq_task_verbs` | warning | FRQ parts missing required task verbs (Define, Describe, Identify, Compare, Explain) |
| `frq_task_verb_progression` | info | Parts should progress: Identify/Define → Describe → Explain → Compare/Evaluate |
| `frq_stimulus_match` | error | FRQ references stimulus but stimulus_id is empty/broken |
| `frq_stimulus_type_match` | warning | FRQ Type 2 should have exactly 1 stimulus, Type 3 should have exactly 2 |
| `frq_count` | warning | Course has fewer than 3 FRQ practice exercises |
| `frq_rubric_exists` | warning | No rubric/scoring criteria found for FRQ (Timeback limitation — flag for manual handling) |
| `frq_title_typo` | warning | Common typos in quiz titles ("Excercise", "Practise", etc.) |

**Implementation notes:**
- Parse parts from stem text using regex: `([A-G])\.` or `parts? ([A-G])` patterns
- Count task verbs: `identify|define|describe|explain|compare|evaluate|discuss`
- FRQ type detection: count stimulus references in test metadata

### Layer 6: Content Depth (No API for basic checks, API for quality)

Checks article/lesson quality and coverage.

| Check | Severity | What It Catches |
|---|---|---|
| `article_word_count` | warning | Article body_text < 800 words (too thin for AP study) |
| `article_word_count_critical` | error | Article body_text < 400 words (critically thin) |
| `article_key_terms` | warning | Article mentions fewer than 10 key terms from CED topic list |
| `article_examples` | info | Article has no country/region examples (AP tests real-world application) |
| `article_missing_for_topic` | error | CED topic in course tree has no corresponding article/stimulus |
| `video_url_format` | warning | Video URL doesn't match expected format (youtu.be or youtube.com) |
| `video_missing_for_topic` | warning | CED topic has no video resource |
| `content_sequence` | warning | Topic section doesn't follow Video → Article → Quiz order |

**API-enhanced checks (optional, uses Claude):**
| Check | What It Checks |
|---|---|
| `article_ced_alignment` | Does article content actually match the CED topic it's tagged for? |
| `article_completeness` | Does article cover all CED learning objectives for its topic? |
| `article_ap_level` | Is the content at AP level (not too simple, not too advanced)? |

### Layer 7: Student Plan QC (No API needed)

Checks that student-facing plans exist and are complete.

| Check | Severity | What It Catches |
|---|---|---|
| `plan_exists` | warning | No student plan file found for this course |
| `plan_has_all_students` | warning | Plan is missing one or more assigned students |
| `plan_has_targets` | warning | Plan doesn't specify target scores for each student |
| `plan_has_structure` | info | Plan doesn't explain course structure to students |
| `plan_ssd_noted` | warning | SSD student assigned but plan doesn't mention accommodation |
| `plan_success_criteria` | info | Plan doesn't define what "success" looks like |

**Implementation notes:**
- This layer requires a plan file to exist at a known path (e.g., `reports/student_plans_{course_id}.md`)
- Parse the markdown for required sections: student names, targets, what they'll do, success criteria
- Cross-reference with spec file for student assignments

---

## Updated Pipeline Architecture

```
Course Data (8 JSONs)
        |
        v
    [LOADER] — Normalize metadata, parse all files
        |
        +--→ [L1: Structural]     — Missing stems, wrong choice counts, duplicates, stimuli
        +--→ [L2: Quality]        — All-of-above, answer bias, stem length, feedback
        +--→ [L3: Alignment]      — Claude API: answerability, correctness, distractors (MCQ)
        +--→ [L4: Course-Level]   — Topic coverage, skill balance, source mix
        +--→ [L5: FRQ Validation] — NEW: Part count, task verbs, type coverage, rubric
        +--→ [L6: Content Depth]  — NEW: Article word count, key terms, video URLs
        +--→ [L7: Student Plan]   — NEW: Plan exists, all students covered, SSD noted
        |
        v
    [REPORT] — JSON + Markdown, now with L5/L6/L7 findings
```

## CLI Updates

```bash
# Run all layers including new ones
python -m qc_pipeline /path/to/course

# Run only new layers
python -m qc_pipeline /path/to/course --layers L5,L6,L7

# Run FRQ validation only
python -m qc_pipeline /path/to/course --layers L5

# Skip API calls but run everything else
python -m qc_pipeline /path/to/course --no-api
```

## Estimated Impact

| Layer | Checks | Would Have Caught (MC1) |
|---|---|---|
| L5 | 10 | FRQ 2 missing parts (4 vs 7), missing FRQ Type 1 + Type 3, quiz title typo, no rubrics |
| L6 | 8 | Women article too thin (859 words), all articles missing explicit key term lists |
| L7 | 6 | No student plan existed before today |

**Total new checks: 24** (bringing pipeline from ~30 checks to ~54)

---

## Build Order

1. `layer5_frq.py` — FRQ validation (highest value, catches real issues)
2. `layer6_content.py` — Content depth checks
3. `layer7_student_plan.py` — Student plan verification
4. Update `__main__.py` to include new layers
5. Update `config.py` with new thresholds (min article words, min FRQ parts, etc.)
6. Update `report.py` to include L5/L6/L7 sections in output

---

*Proposal ready for implementation. All checks are deterministic (no API needed) except the optional L6 content quality checks.*
