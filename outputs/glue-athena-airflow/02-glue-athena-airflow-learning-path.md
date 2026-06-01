#review: APPROVED

# AWS Glue, Athena & Airflow — Serverless Data Analytics
### 02 — glue-athena-airflow — Learning Path Architect

---

## Metadata Block

| Field | Value |
|-------|-------|
| **Learning Path Title** | AWS Glue, Athena & Airflow — Serverless Data Analytics Pipeline |
| **Training POC** | Jem |
| **Version** | v1.0 |
| **Date Created** | 2026-06-01 |
| **Created By** | Jem |
| **Objective** | Learners will build, secure, transform, orchestrate, and monitor a governed data lake using AWS serverless technologies — covering S3, Glue, Lake Formation, MWAA/Airflow, Athena, and QuickSight. |
| **Target Audience** | Junior Data Engineers |
| **Knowledge Prerequisites** | SQL foundations (DDL), basic AWS knowledge (IAM, S3), Python fundamentals, command line familiarity |
| **Tools Needed** | AWS account, S3, AWS Glue, Lake Formation, Amazon MWAA, Athena, QuickSight, PySpark |
| **Total Duration** | 20 days / 80 hours |

---

## Learning Path Skeleton

### Week 1 — Storage Foundations & Lake Formation

#### Day 1: S3 Storage & The Medallion Architecture
- **Learning Objective:** Explain the Bronze/Silver/Gold data lake architecture and provision an S3 bucket with the correct folder structure.
- **Concepts:** Medallion Architecture layers, S3 bucket provisioning, folder prefix strategy, raw vs. curated data
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [VISUAL RECOMMENDED]

#### Day 2: AWS Glue Data Catalog & Crawlers
- **Learning Objective:** Configure an AWS Glue Crawler to discover schemas and populate the Glue Data Catalog from S3 data.
- **Concepts:** Glue Data Catalog, Crawlers, classifiers, schema inference, catalog metadata
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [VISUAL RECOMMENDED]

#### Day 3: AWS Lake Formation & Column-Level Security
- **Learning Objective:** Set up Lake Formation to manage database permissions and enforce column-level access controls.
- **Concepts:** Lake Formation permissions model, column-level security, role-based access, data lake governance
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 4: Apache Iceberg — ACID Transactions on the Data Lake
- **Learning Objective:** Describe how Apache Iceberg enables ACID transactions, schema evolution, and time travel on the data lake.
- **Concepts:** Iceberg table format, ACID transactions, schema evolution, snapshot isolation, time travel queries
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [VISUAL RECOMMENDED]

#### Day 5: Hands-on — S3 Environment & Lake Formation Setup
- **Learning Objective:** Provision an S3 Medallion bucket, run a Glue Crawler, and configure Lake Formation column-level security to protect sensitive data.
- **Concepts:** S3 bucket creation, Glue Crawler configuration, Lake Formation role setup, column masking
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [HANDS-ON RECOMMENDED]
- **Visual Flag:** [NO VISUAL NEEDED]

---

### Week 2 — Data Transformation & Quality

#### Day 6: AWS Glue PySpark — DynamicFrames vs DataFrames
- **Learning Objective:** Differentiate between Spark DataFrames and Glue DynamicFrames and write a basic Glue PySpark ETL script.
- **Concepts:** DynamicFrames, DataFrames, Glue PySpark API, schema-on-read, DynamicFrame transformations
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 7: DQDL — Declarative Data Quality Rules
- **Learning Objective:** Write DQDL rules to enforce data quality constraints within a Glue ETL job.
- **Concepts:** DQDL syntax, row-level quality evaluation, quality rule composition, pass/fail thresholds
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 8: Quarantine Pattern & Bad Data Handling
- **Learning Objective:** Implement branching logic in a Glue job to route failed-quality records to a quarantine S3 prefix.
- **Concepts:** Dead Letter pattern, branching ETL logic, EvaluateDataQuality transform, error routing
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [VISUAL RECOMMENDED]

#### Day 9: Performance Tuning — Partitioning, Compression & Grouping
- **Learning Objective:** Optimize Glue ETL performance through partitioning strategies, Parquet compression, and DynamicFrame grouping.
- **Concepts:** Partition pruning, columnar compression, small-file problem, DynamicFrame grouping, DPU sizing
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 10: Hands-on — Glue ETL Job with Data Quality
- **Learning Objective:** Write a Glue PySpark job that applies DQDL rules, quarantines bad records, and writes clean Parquet to the Silver layer.
- **Concepts:** Glue Job authoring, DQDL in practice, Parquet output, quarantine routing, job testing
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [HANDS-ON RECOMMENDED]
- **Visual Flag:** [NO VISUAL NEEDED]

---

### Week 3 — Orchestration with Amazon MWAA

#### Day 11: Airflow Concepts — DAGs, Operators, Sensors
- **Learning Objective:** Define the core Airflow abstractions — DAGs, Operators, and Sensors — and describe how they compose a pipeline.
- **Concepts:** DAG structure, Operator types (GlueJobOperator, AthenaOperator), Sensors (S3KeySensor), task dependencies
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [VISUAL RECOMMENDED]

#### Day 12: Amazon MWAA Environment Setup & Dependencies
- **Learning Objective:** Configure an Amazon MWAA environment including requirements.txt, plugins, and DAG deployment.
- **Concepts:** MWAA environment creation, Python dependency management, plugins, S3 DAG sync, IAM execution roles
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 13: Advanced DAGs — XComs, Variables, Error Handling
- **Learning Objective:** Implement cross-task data passing with XComs, environment configuration with Variables, and error handling with retries and alerts.
- **Concepts:** XComs (push/pull), Airflow Variables, task retries, timeout configuration, callback alerts (Slack/Email)
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 14: Hands-on — Building an MWAA DAG
- **Learning Objective:** Build a complete Airflow DAG in MWAA that chains an S3 sensor, a Glue job trigger, and an Athena query with error handling.
- **Concepts:** DAG authoring, Sensor setup, GlueJobOperator configuration, AthenaOperator usage, retry logic
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [HANDS-ON RECOMMENDED]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 15: IAM Roles & Least-Privilege Policies for Glue / Athena [GAP]
- **Learning Objective:** Design least-privilege IAM policies that grant each AWS service only the permissions required for its pipeline role.
- **Concepts:** IAM policy composition, trust policies, service-linked roles, policy boundary, Access Analyzer
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

> ⚠️ **Note:** This topic extends beyond the provided sources. The practical exercises draw from standard AWS IAM best practices.

---

### Week 4 — Analytics, Visualization & Capstone

#### Day 16: Athena Workgroups & Cost Management
- **Learning Objective:** Configure Athena Workgroups to enforce data-scan limits and isolate query environments between teams.
- **Concepts:** Workgroups, data usage limits, query cost tracking, output location configuration, workgroup-level IAM
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 17: SQL for Iceberg — MERGE, UPDATE, Time Travel
- **Learning Objective:** Execute Iceberg-specific SQL operations in Athena including MERGE (upsert), row-level UPDATE, and time travel queries.
- **Concepts:** MERGE INTO, row-level UPDATE/DELETE, snapshot history, time travel syntax, Iceberg table optimization
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 18: QuickSight Dashboards & Data Dictionary
- **Learning Objective:** Build an executive dashboard in QuickSight connected to Athena and document the data catalog with a Data Dictionary.
- **Concepts:** QuickSight dataset creation, KPI visuals, dashboard publishing, Glue table comments, Data Dictionary documentation
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [THEORY ONLY]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 19: Capstone — Part 1 (Storage, Catalog & ETL)
- **Learning Objective:** Build the storage foundation and ETL pipeline for a governed e-commerce data lake using S3, Glue Catalog, and Glue ETL with DQDL.
- **Concepts:** Medallion architecture provisioning, Glue Crawler setup, DQDL rules, quarantine routing, Parquet output
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [HANDS-ON RECOMMENDED]
- **Visual Flag:** [NO VISUAL NEEDED]

#### Day 20: Capstone — Part 2 (Orchestration, Dashboard & Final Testing)
- **Learning Objective:** Complete the pipeline by adding MWAA orchestration, an Athena-powered QuickSight dashboard, and end-to-end testing with quality and governance validation.
- **Concepts:** MWAA DAG integration, Athena MERGE queries, QuickSight dashboard, governance testing, pipeline validation
- **Estimated Time:** 4 hours
- **Hands-on Flag:** [HANDS-ON RECOMMENDED]
- **Visual Flag:** [NO VISUAL NEEDED]

---

## Visual Decision Gate

The following days have been flagged as **[VISUAL RECOMMENDED]** (confirmed by owner):

| Day | Topic | Suggested Diagram Type |
|-----|-------|----------------------|
| Day 1 | S3 Storage & Medallion Architecture | Architecture Diagram |
| Day 2 | Glue Data Catalog & Crawlers | Architecture / Flowchart |
| Day 4 | Apache Iceberg — ACID Transactions | Concept Map |
| Day 8 | Quarantine Pattern & Bad Data Handling | Flowchart |
| Day 11 | Airflow Concepts — DAGs, Operators, Sensors | Concept Map |

---

*Version: v1.0 | Created: 2026-06-01 | Author: Technical Curriculum Designer*

---

Learning path skeleton complete. Please review the structure, day breakdown, and visual flags. Confirm, adjust, or add changes before proceeding to Skill 3: Module Content Builder.
