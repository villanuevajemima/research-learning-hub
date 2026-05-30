#review: DRAFT

# AWS Serverless Data Analytics Pipeline
### 02 — aws-serverless-data-analytics — Learning Path Architect

---

## Learning Path Skeleton

### Metadata

| Field | Value |
|-------|-------|
| **Learning Path Title** | AWS Serverless Data Analytics Pipeline |
| **Training POC** | jem |
| **Version** | v1.0 |
| **Date Created** | 2026-05-30 |
| **Created By** | Jem |
| **Objective** | Enable a junior data engineer to design, build, and operate a complete serverless data analytics pipeline on AWS using S3, Glue, Athena, QuickSight, and IAM |
| **Target Audience** | Junior data engineers with no prior AWS experience |
| **Knowledge Prerequisites** | Basic SQL, general programming concepts (variables, functions, control flow) |
| **Tools Needed** | AWS account (free tier), web browser, optionally VS Code or PyCharm |
| **Total Duration** | 2 weeks (10 days) — 2 hours per day |

---

### Day-by-Day Structure

#### Day 1: Cloud Foundations & AWS Account Setup
- **Objective:** Understand cloud computing fundamentals and set up a secure AWS account
- **Visual aid:** ✅ Yes — AWS global infrastructure diagram (regions, AZs, edge locations)
- **Hands-on activity:** Create an AWS account, set up billing alerts, create an IAM admin user

#### Day 2: Amazon S3 for Data Lakes
- **Objective:** Learn S3 as the foundational storage layer for a data lake
- **Visual aid:** ✅ Yes — S3 bucket structure, storage classes, and partitioning strategy diagram
- **Hands-on activity:** Create buckets, upload CSV data, configure lifecycle policies

#### Day 3: AWS Glue: Crawlers, Data Catalog & Schema Discovery
- **Objective:** Use Glue crawlers to automatically discover schema and populate the Data Catalog
- **Visual aid:** ✅ Yes — Glue architecture flow (crawler → catalog → consumers)
- **Hands-on activity:** Create a Glue crawler, run it against S3 data, inspect the resulting catalog tables

#### Day 4: AWS Glue: ETL Jobs with Spark & PySpark
- **Objective:** Write and run Glue ETL jobs to transform raw data into query-optimized formats
- **Visual aid:** ✅ Yes — ETL pipeline flow diagram (extract → transform → load to Parquet)
- **Hands-on activity:** Write a PySpark Glue job that reads CSV, applies transformations, and outputs Parquet

#### Day 5: Amazon Athena: Serverless SQL Querying
- **Objective:** Query transformed data in S3 using standard SQL with Athena
- **Visual aid:** ✅ Yes — Athena query execution flow diagram
- **Hands-on activity:** Run SQL queries against Glue-cataloged data, analyze query costs, use partitioning

#### Day 6: Amazon QuickSight: Dashboards & BI
- **Objective:** Build interactive dashboards and natural-language queries with QuickSight
- **Visual aid:** ✅ Yes — BI dashboard mockup with key chart types
- **Hands-on activity:** Connect QuickSight to Athena, build a multi-chart dashboard, share it

#### Day 7: IAM Deep Dive for Analytics Pipelines
- **Objective:** Design least-privilege IAM policies for every service in the pipeline
- **Visual aid:** ✅ Yes — IAM policy structure diagram and cross-service auth flow
- **Hands-on activity:** Write custom IAM policies for Glue, Athena, and QuickSight roles

#### Day 8: Orchestration & Automation
- **Objective:** Automate multi-step pipelines using Glue triggers, EventBridge, and Step Functions
- **Visual aid:** ✅ Yes — Step Functions workflow state machine diagram
- **Hands-on activity:** Build a Step Functions state machine that chains a crawler → Glue job → Athena query

#### Day 9: Data Quality, Monitoring & Alerting
- **Objective:** Monitor pipeline health and enforce data quality checks
- **Visual aid:** ✅ Yes — CloudWatch dashboard with Glue/Athena metrics
- **Hands-on activity:** Set up CloudWatch alarms for Glue job failures, enable Glue Data Quality

#### Day 10: Cost Optimization & Governance
- **Objective:** Manage and reduce costs across the serverless analytics stack
- **Visual aid:** ✅ Yes — Cost breakdown by service diagram
- **Hands-on activity:** Analyze AWS Cost Explorer, set budgets, apply Athena query cost controls

---

*Version: v1.0 | Created: 2026-05-30 | Author: Jem*
