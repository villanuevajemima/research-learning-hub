#review: APPROVED

# AWS Glue, Athena & Airflow — Serverless Data Analytics Pipeline
### 06 — glue-athena-airflow — Rubric Generator

---

## QUIZ RUBRIC — AWS Glue, Athena & Airflow: Serverless Data Analytics Pipeline

**Score: 90-100% | Label: Excellent**
Indicates: The learner demonstrates comprehensive understanding of the full data pipeline — from Medallion storage and Glue ETL with quality controls to Iceberg operations, Airflow orchestration, IAM governance, and cost management.
Recommended Action: Proceed to advanced topics (streaming with Kinesis, multi-region architectures, or ML on SageMaker).
Topics to Revisit: None — proceed.

---

**Score: 75-89% | Label: Satisfactory**
Indicates: The learner has solid understanding across most pipeline phases but may have gaps in one or two specific areas such as Airflow internals, Iceberg features, or IAM least-privilege design.
Recommended Action: Review incorrect answers and revisit the corresponding day topics before proceeding to advanced material.
Topics to Revisit: Check answer key — each question maps to a specific day (e.g., Q1→Day 11, Q6→Day 15). Revisit the day associated with each incorrect answer.

---

**Score: 60-74% | Label: Developing**
Indicates: The learner understands the foundational concepts (S3 layers, basic ETL) but struggles with applied or analytical questions covering orchestration, security design, and advanced Iceberg features.
Recommended Action: Revisit Days 6–8 (Glue ETL and data quality), Day 11 (Airflow concepts), and Day 15 (IAM least-privilege) before attempting the quiz again.
Topics to Revisit: Day 4 — Apache Iceberg; Day 6 — DynamicFrames vs DataFrames; Day 7 — DQDL; Day 8 — Quarantine Pattern; Day 11 — Airflow Concepts; Day 15 — IAM Roles; Day 16 — Athena Workgroups.

---

**Score: Below 60% | Label: Needs Review**
Indicates: The learner has not yet developed sufficient understanding of the core pipeline components and would benefit from re-studying the full learning path before reassessment.
Recommended Action: Retake the full learning path starting from Day 1, completing all hands-on activities before reattempting the quiz.
Topics to Revisit: Full learning path — all 20 days.

---

## HANDS-ON RUBRIC — AWS Glue, Athena & Airflow: Serverless Data Analytics Pipeline (Course-Level)

| Criteria | 4 — Advanced | 3 — Proficient | 2 — Developing | 1 — Beginning |
|----------|-------------|----------------|----------------|---------------|
| **S3 Medallion Storage & Partitioning** | Buckets use Hive-style partitioning (year=2026/month=06/) with lifecycle policies, encryption, and versioning configured | Buckets created with bronze/silver/gold prefix structure; raw CSVs uploaded to Bronze | Buckets exist but prefix structure is missing layers or inconsistent partitioning | Buckets are misconfigured, missing, or data was not uploaded |
| **Glue Catalog & Crawler Automation** | Crawlers run on a schedule with incremental schema updates; Data Catalog tables have column comments and business descriptions | Crawler populates the Data Catalog with correct schemas and partition metadata | Crawler runs but produces incorrect schemas, missing partitions, or wrong data types | Crawler fails to run or Data Catalog tables are not created |
| **Glue ETL with DQDL & Quarantine** | ETL job includes custom DQDL rules, splits passing/failing records, writes quarantine metadata columns (dq_failed_rules, dq_timestamp), and is parameterized for reuse | ETL job reads Bronze, applies DQDL rules, writes clean Parquet to Silver, and quarantines failures | ETL job runs but DQDL rules are incomplete, quarantine routing is missing, or output format is incorrect | ETL job fails to run or produces no output |
| **Iceberg & Athena SQL Operations** | MERGE, UPDATE, DELETE, and time travel queries all execute correctly; partition pruning is verified through EXPLAIN output | MERGE statement updates Gold table correctly; Athena queries return expected results | MERGE runs but produces incorrect row counts or schema mismatches | MERGE fails or Athena queries return errors |
| **MWAA Orchestration & Error Handling** | DAG includes S3KeySensor with configurable timeout, GlueJobOperator with status polling, AthenaOperator, XCom passing, retries, and SNS/Slack alert callbacks | DAG with S3KeySensor → GlueJobOperator → AthenaOperator executes end-to-end successfully | DAG runs but tasks fail intermittently, error handling is missing, or dependencies are incorrectly ordered | DAG fails to deploy or no tasks complete |
| **IAM Least-Privilege Security** | Separate IAM roles per service with inline policies scoped to specific resource ARNs; IAM Access Analyzer confirms no unintended access | Roles exist for Glue Crawler, Glue ETL, MWAA, Athena, and QuickSight with correct service policies | Roles exist but permissions are overly broad (e.g., s3:* on the full bucket) or missing required actions | No IAM roles configured; services use default execution roles or root credentials |
| **QuickSight Dashboard & Governance Validation** | Dashboard includes interactive filters, multiple chart types (KPI, line, pie), and a Data Dictionary with column comments; governance tests pass | QuickSight dashboard connected to Athena Gold renders correct KPIs; DESCRIBE shows column comments | Dashboard exists but charts show incorrect data or filters are non-functional | No dashboard created or QuickSight connection to Athena fails |

Total possible score: **28 points** (7 criteria × 4 points max each)
Passing score: **21 points** (75% of total)

### Scoring Guide

| Total Score | Label | Recommended Action |
|-------------|-------|-------------------|
| 25-28 | Advanced | Proceed to advanced topics — streaming data pipelines (Kinesis), multi-region architectures, or ML inference on SageMaker |
| 21-24 | Proficient | Learning path complete — proceed to the next learning path or production deployment of the pipeline |
| 15-20 | Developing | Review flagged pipeline phases and redo the associated hands-on activities before resubmitting |
| Below 15 | Beginning | Revisit the full 20-day learning path before attempting hands-on activities again |

---

Rubric generation complete. Review all criteria and scoring ranges against the learning path content. Rubrics are ready to attach to the relevant module and quiz in the final learning path document.

---

*Version: v1.0 | Created: 2026-06-01 | Author: Instructional Designer*
