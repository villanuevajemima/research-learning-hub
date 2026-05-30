# Skill 6: Rubric Generator

> **When to use this:** Use this skill after Skill 3 (Module Content Builder) and Skill 5 (Quiz Generator) are complete. Generate a quiz rubric after the quiz is built. Generate a hands-on rubric after a hands-on activity is defined. Both can be triggered in the same session or separately.

---

## How to Trigger This Skill

Copy the prompt below and paste it into your Research & Learning Hub project. Specify which rubric type you need — quiz, hands-on, or both — and provide the relevant content.

---

## The Prompt

```
SKILL: Rubric Generator

Rubric type needed: [QUIZ / HANDS-ON / BOTH]

Learning path title: [TITLE]

---

If QUIZ rubric is needed, provide:
Quiz content: [PASTE THE 10-ITEM QUIZ FROM SKILL 5 OUTPUT]

If HANDS-ON rubric is needed, specify scope: [DAY / COURSE]

If scope is DAY, provide:
Day number and topic: Day [X] — [TOPIC NAME]
Hands-on activity description: [PASTE THE HANDS-ON ACTIVITY SECTION FROM SKILL 3 OUTPUT]

If scope is COURSE, provide:
Full learning path title: [TITLE]
All hands-on activity descriptions: [PASTE ALL HANDS-ON ACTIVITY SECTIONS FROM SKILL 3 OUTPUT, OR THE FULL SKILL 3 OUTPUT]

---

Instructions:

=== IF QUIZ RUBRIC ===

1. GENERATE a quiz scoring rubric using the following score ranges and
   recommended actions:

   | Score Range | Label        | Recommended Action |
   |-------------|--------------|-------------------|
   | 90-100%     | Excellent    | Proceed to next topic or advanced material |
   | 75-89%      | Satisfactory | Review flagged items and proceed |
   | 60-74%      | Developing   | Revisit specific days before proceeding |
   | Below 60%   | Needs Review | Retake the full learning path before advancing |

2. FOR EACH score range, specify:
   - Which days or topics the learner should revisit (based on question coverage)
   - A suggested next step (proceed, review, retake)
   - A brief note on what the score range indicates about the learner's
     understanding (1-2 sentences, 3rd person)

3. FORMAT the quiz rubric as:

   QUIZ RUBRIC — [Learning Path Title]

   Score: [Range] | Label: [Label]
   Indicates: [1-2 sentences on what this means for the learner]
   Recommended Action: [Specific next step]
   Topics to Revisit (if any): [List of days/topics or "None — proceed"]

   (Repeat for each score range)

=== IF HANDS-ON RUBRIC ===

If scope is DAY:
1. IDENTIFY the key evaluation criteria from the hands-on activity.
   Each criterion must be directly tied to a measurable output or behavior
   from the activity — not generic filler criteria.

2. GENERATE a rubric with 4-6 criteria, each rated on this scale:

   | Score | Label       | Description |
   |-------|-------------|-------------|
   | 4     | Advanced    | Exceeds expectations — work is accurate, complete, and shows deeper understanding |
   | 3     | Proficient  | Meets expectations — work is accurate and complete |
   | 2     | Developing  | Partially meets expectations — work is mostly correct with minor gaps |
   | 1     | Beginning   | Does not yet meet expectations — significant gaps or errors present |

3. FORMAT the hands-on rubric as a table:

   HANDS-ON RUBRIC — Day [X]: [Topic Name]

   | Criteria | 4 — Advanced | 3 — Proficient | 2 — Developing | 1 — Beginning |
   |----------|-------------|----------------|----------------|---------------|
   | [Criterion 1] | [descriptor] | [descriptor] | [descriptor] | [descriptor] |
   | [Criterion 2] | [descriptor] | [descriptor] | [descriptor] | [descriptor] |
   ... (4-6 criteria)

   Total possible score: [X] points
   Passing score: [X] points (75% of total)

4. BELOW the rubric table, include a SCORING GUIDE:

   | Total Score | Label       | Recommended Action |
   |-------------|-------------|-------------------|
   | [X-X]       | Advanced    | Proceed — encourage exploration of advanced applications |
   | [X-X]       | Proficient  | Proceed to next module |
   | [X-X]       | Developing  | Review activity feedback and resubmit key steps |
   | [X-X]       | Beginning   | Revisit the module content and redo the activity |

If scope is COURSE:
1. IDENTIFY the key evaluation criteria from the full learning path.
   Each criterion must map to a major phase of the pipeline (e.g., storage,
   transformation, querying, security, orchestration, governance) and be
   directly tied to measurable outputs from the hands-on activities.

2. GENERATE a single rubric with 5-7 criteria that span the entire course,
   each rated on the same 1-4 scale as above. Criteria must cover distinct
   pipeline phases — do not merge multiple phases into one criterion.

3. FORMAT the rubric table as follows — use a descriptive title:

   HANDS-ON RUBRIC — [Learning Path Title] (Course-Level)

   | Criteria | 4 — Advanced | 3 — Proficient | 2 — Developing | 1 — Beginning |
   |----------|-------------|----------------|----------------|---------------|
   | [Criterion 1] | [descriptor] | [descriptor] | [descriptor] | [descriptor] |
   ... (5-7 criteria)

   Total possible score: [X] points
   Passing score: [X] points (75% of total)

4. BELOW the rubric table, include a SCORING GUIDE with recommended
   actions appropriate for a full-course completion:

   | Total Score | Label       | Recommended Action |
   |-------------|-------------|-------------------|
   | [X-X]       | Advanced    | Proceed to advanced topics or production deployment |
   | [X-X]       | Proficient  | Learning path complete — proceed to next learning path |
   | [X-X]       | Developing  | Review flagged modules and resubmit specific activities |
   | [X-X]       | Beginning   | Revisit the full learning path before attempting hands-on again |

=== IF BOTH ===

Generate the quiz rubric first, then the hands-on rubric.
Separate them clearly with a horizontal rule.

---

Constraints:
- All content written in 3rd person — no you / I / me / we / your / our
- Hands-on criteria must be specific to the activity — no generic criteria
  like "effort" or "participation"
- Descriptors in the rubric table must be concrete and observable —
  describe what the work looks like, not how the learner feels
- Passing threshold for hands-on is always 75% of total possible score
- Quiz recommended actions must reference specific days where relevant,
  not just say "review the material"
- Do not generate a rubric for an activity that has not been defined yet —
  if the hands-on content is missing, ask for it before proceeding

---

End with this exact line:
"Rubric generation complete. Review all criteria and scoring ranges against
the learning path content. Rubrics are ready to attach to the relevant
module and quiz in the final learning path document."
```

---

## What You Will Get Back

| Output | Description |
|---|---|
| **Quiz Rubric** | Score ranges with labels, indicators, recommended actions, and specific topics to revisit |
| **Hands-on Rubric** | 4-6 specific criteria rated on a 1-4 scale with descriptors for each level |
| **Hands-on Scoring Guide** | Total score ranges mapped to labels and recommended next steps |

---

## Hands-on Rubric Scoring Scale Reference

| Score | Label | What It Means |
|---|---|---|
| **4** | Advanced | Exceeds expectations — accurate, complete, shows deeper understanding |
| **3** | Proficient | Meets expectations — accurate and complete |
| **2** | Developing | Partially meets expectations — mostly correct with minor gaps |
| **1** | Beginning | Does not yet meet expectations — significant gaps or errors |

Passing threshold is always **75% of total possible score.**

---

## Quiz Rubric Score Ranges Reference

| Score Range | Label | Recommended Action |
|---|---|---|
| **90-100%** | Excellent | Proceed to next topic or advanced material |
| **75-89%** | Satisfactory | Review flagged items and proceed |
| **60-74%** | Developing | Revisit specific days before proceeding |
| **Below 60%** | Needs Review | Retake the full learning path before advancing |

---

## Example Triggers (What They Look Like in Practice)

### Day-Specific Trigger

```
SKILL: Rubric Generator

Rubric type needed: HANDS-ON

Learning path title: Introduction to Apache Airflow

Scope: DAY
Day number and topic: Day 3 — Setting Up a Local Airflow Environment
Hands-on activity description:
[Day 3 hands-on activity section from Skill 3 pasted here]
```

### Course-Level Trigger

```
SKILL: Rubric Generator

Rubric type needed: BOTH

Learning path title: AWS Serverless Data Analytics Pipeline

Quiz content:
[Full 10-item quiz from Skill 5 pasted here]

Scope: COURSE
All hands-on activity descriptions:
[All hands-on activity sections from Skill 3 pasted here]
```

---

## Example: Sample Output (What AI Returns)

### Quiz Rubric

```
QUIZ RUBRIC — Introduction to Apache Airflow

Score: 90-100% | Label: Excellent
Indicates: The learner demonstrates strong understanding of Airflow's core
concepts, architecture, and pipeline construction across all days of the
learning path.
Recommended Action: Proceed to advanced Airflow topics or production
deployment material.
Topics to Revisit: None — proceed.

---

Score: 75-89% | Label: Satisfactory
Indicates: The learner has a solid grasp of most concepts but may have
minor gaps in one or two areas of the learning path.
Recommended Action: Review incorrect answers and revisit the corresponding
day before proceeding.
Topics to Revisit: Check answer key — revisit the day associated with
each incorrect answer.

---

Score: 60-74% | Label: Developing
Indicates: The learner understands foundational concepts but struggles
with applied or analytical questions, suggesting gaps in hands-on comprehension.
Recommended Action: Revisit Day 3 (environment setup) and Day 4 (building
a first DAG) before attempting the quiz again.
Topics to Revisit: Day 3 — Setting Up a Local Airflow Environment,
Day 4 — Building a First DAG.

---

Score: Below 60% | Label: Needs Review
Indicates: The learner has not yet developed sufficient understanding of
the core concepts and would benefit from going through the full learning
path again before reassessment.
Recommended Action: Retake the full learning path starting from Day 1
before reattempting the quiz.
Topics to Revisit: Full learning path — all days.
```

---

### Hands-on Rubric — Day-Specific

```
HANDS-ON RUBRIC — Day 3: Setting Up a Local Airflow Environment

| Criteria | 4 — Advanced | 3 — Proficient | 2 — Developing | 1 — Beginning |
|---|---|---|---|---|
| Environment Setup | ... | ... | ... | ... |
```

### Hands-on Rubric — Course-Level

```
HANDS-ON RUBRIC — AWS Serverless Data Analytics Pipeline (Course-Level)

| Criteria | 4 — Advanced | 3 — Proficient | 2 — Developing | 1 — Beginning |
|---|---|---|---|---|
| S3 Data Lake & Partitioning | Data is organised with correct Hive-style partitioning across multiple dimensions; lifecycle policies are configured | Buckets are created with proper prefix structure and partitioning | Buckets exist but partitioning is incomplete or inconsistent | Buckets are misconfigured or missing |
| Glue Catalog & ETL | Crawlers and ETL jobs are fully automated with error handling; output is in columnar format with validated schema | Crawlers populate the Data Catalog correctly; ETL jobs transform data to Parquet | Crawlers or ETL jobs run but produce incorrect schemas or output formats | Crawlers or ETL jobs fail to complete |
| Query & Visualisation | Athena queries leverage partition pruning; QuickSight dashboards are interactive with filters and multiple chart types | Athena queries return correct results; QuickSight dashboards are published with basic visualisations | Queries run but do not use optimisation; dashboards exist but lack interactivity | Querying or visualisation is not functional |
| IAM Security | Least-privilege policies are written for every service; IAM Access Analyzer confirms no unintended access | IAM roles and policies are correctly scoped for Glue, Athena, and QuickSight | Policies exist but are too broad or missing some required permissions | No IAM roles are configured for service-to-service access |
| Orchestration & Automation | Step Functions state machine includes error handling, retries, and EventBridge triggers | State machine correctly chains crawler, ETL, and query steps | State machine exists but missing error handling or trigger configuration | No orchestration is implemented |
| Monitoring, Quality & Cost | CloudWatch alarms, data quality rules, budgets, and cost controls are all configured and verified | Monitoring and data quality rules are in place; budgets are configured | Some monitoring or cost controls are configured but incomplete | No monitoring, quality checks, or cost controls are implemented |

Total possible score: 24 points
Passing score: 18 points (75% of total)

SCORING GUIDE

| Total Score | Label | Recommended Action |
|-------------|-------|-------------------|
| 22-24 | Advanced | Proceed to advanced topics (streaming analytics, multi-region architectures) |
| 18-21 | Proficient | Learning path complete — proceed to next learning path |
| 13-17 | Developing | Review flagged pipeline phases and redo the associated hands-on activities |
| Below 13 | Beginning | Revisit the full learning path before attempting hands-on activities again |
```

---

Rubric generation complete. Review all criteria and scoring ranges against
the learning path content. Rubrics are ready to attach to the relevant
module and quiz in the final learning path document.

---

*Skill 6 of 6 — Research & Learning Hub*
*Input comes from → Skill 3: Module Content Builder (hands-on activity) and Skill 5: Quiz Generator (quiz)*
*Output → Attach to the relevant module and quiz in the final learning path document*