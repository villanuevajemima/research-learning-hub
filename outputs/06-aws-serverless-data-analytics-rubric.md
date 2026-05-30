#review: DRAFT

# AWS Serverless Data Analytics Pipeline
### 06 — aws-serverless-data-analytics — Rubric Generator

---

## Rubrics

### Quiz Rubric — AWS Serverless Data Analytics Pipeline

**Score: 90-100% | Label: Excellent**
Indicates: The learner demonstrates thorough understanding of the complete serverless analytics pipeline across all 10 days, from cloud foundations through cost governance.
Recommended Action: Proceed to advanced topics such as streaming analytics (Kinesis), real-time processing (Lambda), or multi-region pipeline architectures.
Topics to Revisit: None — proceed.

**Score: 75-89% | Label: Satisfactory**
Indicates: The learner has a solid grasp of most pipeline components but may have minor gaps in one or two areas, likely around service-specific details or optimisation strategies.
Recommended Action: Review the incorrect answers and revisit the corresponding day's module before proceeding.
Topics to Revisit: Check the answer key — revisit the day associated with each incorrect answer.

**Score: 60-74% | Label: Developing**
Indicates: The learner understands the high-level architecture and core services but struggles with applied or analytical questions involving IAM policy design, cost controls, or data quality rules.
Recommended Action: Revisit Day 5 (Athena), Day 7 (IAM), and Day 10 (Cost Optimization) before reattempting the quiz.
Topics to Revisit: Day 5 — Amazon Athena, Day 7 — IAM Deep Dive, Day 10 — Cost Optimization & Governance.

**Score: Below 60% | Label: Needs Review**
Indicates: The learner has not yet developed sufficient understanding of the core services and their interactions within the pipeline.
Recommended Action: Retake the full learning path starting from Day 1 before reassessment.
Topics to Revisit: Full learning path — all days.

---

### Hands-On Rubric (Course-Level)

**HANDS-ON RUBRIC — AWS Serverless Data Analytics Pipeline (Course-Level)**

| Criteria | 4 — Advanced | 3 — Proficient | 2 — Developing | 1 — Beginning |
|----------|-------------|----------------|----------------|---------------|
| S3 Data Lake & Partitioning | Data is organised with correct Hive-style partitioning across date dimensions; lifecycle policies are configured with transitions and expirations | Buckets are created with proper prefix structure; data is partitioned by date | Buckets exist but partitioning is incomplete, inconsistent, or uses a flat structure | Buckets are misconfigured, missing, or data is stored without any organisational structure |
| Glue Catalog & ETL | Crawlers use custom classifiers for non-standard formats; ETL jobs are written in PySpark with proper transformations and output columnar formats; jobs are monitored via CloudWatch | Crawlers populate the Data Catalog correctly; ETL jobs transform data from CSV to Parquet with basic cleaning | Crawlers or ETL jobs run but produce incorrect schemas or output remains in a row-based format | Crawlers or ETL jobs fail to complete or are not implemented |
| Athena Querying & Performance Optimisation | Queries leverage partition pruning and columnar formats; learner compares scan costs between formats and uses workgroup cost controls | Queries return correct results; learner demonstrates awareness of partition pruning and columnar format benefits | Queries run but do not use optimisation; learner does not compare performance across formats | Querying is not functional or learner cannot construct valid SQL |
| QuickSight Visualisation & BI | Dashboard uses multiple chart types (bar, line, KPI) with interactive filters; SPICE is configured for performance; dashboard is published and shared | Dashboard with at least three visualisations is built and published | Dashboard exists but has fewer than three visualisations or lacks interactivity | No dashboard is created or QuickSight is not connected to the data source |
| IAM Security & Least Privilege | Custom IAM policies with scoped actions and resource ARNs are written for each service; IAM Access Analyzer confirms no unintended access | IAM roles with correctly scoped policies are created for Glue, Athena, and QuickSight | IAM policies exist but are too broad (e.g., `s3:*`) or missing required permissions for some services | No IAM roles are configured or the learner uses long-term credentials |
| Pipeline Orchestration & Automation | Step Functions state machine chains crawler, ETL, and query steps with error handling, retry logic, and EventBridge S3 event triggers | Step Functions state machine correctly chains pipeline steps with basic error handling | State machine exists but is missing error handling, retries, or event triggers | No orchestration is implemented — steps are run manually |
| Monitoring, Data Quality & Cost Governance | CloudWatch alarms, Glue Data Quality rules, budgets, and Athena cost controls are all configured, tested, and verified | Monitoring alarms, data quality checks, and budgets are in place | Some monitoring or governance features are configured but incomplete or not tested | No monitoring, data quality, budgets, or cost controls are implemented |

Total possible score: 28 points
Passing score: 21 points (75% of total)

| Total Score | Label | Recommended Action |
|-------------|-------|-------------------|
| 25-28 | Advanced | Proceed to advanced topics (streaming analytics with Kinesis, real-time processing with Lambda, multi-region architectures) |
| 21-24 | Proficient | Learning path complete — proceed to next learning path |
| 15-20 | Developing | Review the flagged pipeline phases and redo the associated hands-on activities before advancing |
| Below 15 | Beginning | Revisit the full learning path and reattempt all hands-on activities before proceeding |

---

*Version: v1.0 | Created: 2026-05-30 | Author: Instructional Designer*
