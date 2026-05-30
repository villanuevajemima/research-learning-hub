#review: DRAFT

# AWS Serverless Data Analytics Pipeline
### 03 — aws-serverless-data-analytics — Module Content Builder

---

## Module Content

#### Day 1: Cloud Foundations & AWS Account Setup

- **Learning Objective:** Understand cloud computing fundamentals and set up a secure AWS account.
- **Core Idea:** Cloud computing delivers on-demand compute, storage, and networking resources over the internet on a pay-as-you-go basis. AWS organizes its infrastructure into **Regions** (geographic areas) and **Availability Zones** (isolated data centers within a Region), enabling fault tolerance and low-latency access. A well-structured AWS account with proper identity management and billing controls is the starting point for any cloud data project.
- **Why It Matters:** Without a foundational understanding of Regions and AZs, learners cannot make informed decisions about where to store data or run workloads. A misconfigured account can lead to security breaches or unexpected cost overruns before any actual data work begins. Establishing billing alerts and an IAM admin user from day one prevents these issues while building secure habits.
- **How It Works:** Learners sign up for an AWS account and navigate the Management Console. They create an IAM user with administrative permissions and configure billing alerts through AWS Budgets. Finally, they explore the console to identify the Region selector, service navigation, and the IAM dashboard.
- **Supplemental Reading:**
  - 📄 [AWS Official — Overview of Amazon Web Services](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/introduction.html)
  - 📄 [AWS Official — Regions and Availability Zones](https://aws.amazon.com/about-aws/global-infrastructure/regions-az/)
  - 📝 [DataCamp — How to Set Up and Configure AWS](https://www.datacamp.com/tutorial/how-to-set-up-and-configure-aws)
- **Hands-on Activity:** AWS Account Setup — Sign up for an AWS Free Tier account, create an IAM admin user with MFA enabled, set up a monthly budget alert of $5, and log the steps taken.
- **Visual Aid:** ✅ Yes — AWS global infrastructure diagram showing Regions, Availability Zones, and edge locations. [VISUAL PENDING — Skill 4]

---

#### Day 2: Amazon S3 for Data Lakes

- **Learning Objective:** Learn S3 as the foundational storage layer for a data lake.
- **Core Idea:** Amazon S3 is a highly durable object storage service where data is stored in **buckets** (containers) and organized using **prefixes** that function like folder paths. S3 offers multiple **storage classes** that trade retrieval speed for cost, such as S3 Standard for frequent access and S3 Glacier for archival data. **Partitioning** — organising data into a hierarchical folder structure by columns like date or region — improves query performance by allowing engines to skip irrelevant files.
- **Why It Matters:** S3 is the most common storage layer for AWS data lakes because of its 99.999999999% durability and seamless integration with analytics services. Choosing the right storage class and partitioning strategy directly affects both query speed and monthly storage costs. Understanding S3 fundamentals is prerequisite knowledge for every subsequent module in this pipeline.
- **How It Works:** Learners create an S3 bucket with a unique name and upload CSV data files into it. They organise files using a date-based prefix structure (e.g., `data/year=2026/month=05/`). They configure a lifecycle policy that transitions older data to S3 Glacier after 90 days.
- **Supplemental Reading:**
  - 📄 [AWS Official — Amazon S3 Documentation](https://docs.aws.amazon.com/s3/)
  - 📝 [AWS Blog — Best practices for organizing your S3 data lake](https://aws.amazon.com/blogs/big-data/best-practices-for-organizing-your-data-lake-on-amazon-s3/)
  - 📝 [Medium — Data Analysis Made Easy: S3, AWS Glue, Athena and QuickSight](https://medium.com/@ifeanyiobiana/data-analysis-made-easy-s3-aws-glue-athena-and-quicksight-22125e36b3ae)
- **Hands-on Activity:** S3 Bucket Setup — Create an S3 bucket, organise sample CSV data into a `raw/year=2026/month=05/day=01/` prefix structure, upload files, and verify the object hierarchy in the console.
- **Visual Aid:** ✅ Yes — S3 bucket structure diagram showing buckets, prefixes, objects, and a partitioned folder hierarchy. [VISUAL PENDING — Skill 4]

---

#### Day 3: AWS Glue: Crawlers, Data Catalog & Schema Discovery

- **Learning Objective:** Use Glue crawlers to automatically discover schema and populate the Data Catalog.
- **Core Idea:** The **AWS Glue Data Catalog** is a central metadata repository that stores table definitions, schema information, and partition metadata for data stored in AWS. **Glue Crawlers** automatically scan data sources (such as S3 buckets), infer the schema (column names, data types, partitioning), and populate the Data Catalog with table definitions. **Classifiers** allow custom schema inference logic for non-standard data formats.
- **Why It Matters:** Manually defining table schemas for every dataset does not scale as the number of sources grows. The crawler automates this discovery process, eliminating manual work and reducing human error. Once metadata is in the Data Catalog, any compatible query engine — Athena, Redshift Spectrum, or EMR — can immediately read the data without additional configuration.
- **How It Works:** Learners navigate to the AWS Glue console and create a new crawler targeting the S3 bucket from Day 2. They assign an IAM role that grants the crawler read access to S3 and write access to the Data Catalog. After running the crawler, they inspect the generated table definitions and verify that column names, data types, and partition columns are correct.
- **Supplemental Reading:**
  - 📄 [AWS Official — AWS Glue Data Catalog Documentation](https://docs.aws.amazon.com/glue/latest/dg/catalog-and-crawler.html)
  - 📝 [DataCamp — Getting Started with AWS Glue](https://www.datacamp.com/tutorial/aws-glue)
  - 📝 [AWS Blog — Develop and test AWS Glue jobs locally using a Docker container](https://aws.amazon.com/blogs/big-data/develop-and-test-aws-glue-version-3-0-jobs-locally-using-a-docker-container/)
- **Hands-on Activity:** First Glue Crawler — Create a Glue crawler targeting the S3 bucket from Day 2, run it, inspect the generated table in the Data Catalog, and write a simple SQL `SELECT *` query in Athena to confirm the schema is correct.
- **Visual Aid:** ✅ Yes — Glue architecture flow diagram: S3 → Crawler → Data Catalog → Athena / Glue Jobs / Redshift Spectrum.

  > This flowchart traces the data discovery process: a Glue crawler scans CSV files in S3, optionally applies a classifier for custom formats, and populates the Glue Data Catalog with table definitions. Once catalogued, the metadata is immediately available to Athena, Glue Jobs, and Redshift Spectrum.

  ```mermaid
  graph LR
      S3[("S3 Data Source<br/>CSV Files")]
      CRAWLER["Glue Crawler<br/>Auto-Discovers Schema"]
      CLASSIFIER["Classifier<br/>Custom Format Logic"]
      CATALOG[("Glue Data Catalog<br/>Tables & Schema")]
      ATHENA["Amazon Athena<br/>SQL Queries"]
      GLUEJOB["AWS Glue Jobs<br/>ETL Transformations"]
      REDSHIFT["Redshift Spectrum<br/>External Queries"]

      S3 --> CRAWLER
      CRAWLER --> CLASSIFIER
      CLASSIFIER --> CATALOG
      CATALOG --> ATHENA
      CATALOG --> GLUEJOB
      CATALOG --> REDSHIFT
  ```

---

#### Day 4: AWS Glue: ETL Jobs with Spark & PySpark

- **Learning Objective:** Write and run Glue ETL jobs to transform raw data into query-optimized formats.
- **Core Idea:** **AWS Glue Jobs** are serverless Apache Spark-based workloads that perform **ETL** — extracting data from a source, transforming it (filtering, aggregating, joining, cleaning), and loading it into a target destination. Jobs can be written in PySpark or Scala and are executed on managed worker nodes called **DPUs** (Data Processing Units). Glue can auto-generate ETL code from the Data Catalog or accept custom scripts.
- **Why It Matters:** Raw data in its original format (CSV, JSON, logs) is rarely ready for analysis. Glue Jobs handle the heavy transformation work without requiring users to provision or manage Spark clusters. Understanding how to write and optimise Glue Jobs enables learners to build production-grade data pipelines that convert messy source data into clean, query-optimised formats like Parquet.
- **How It Works:** Learners create a new Glue Job using the Script Editor, writing a PySpark script that reads CSV data from S3, applies transformations such as casting data types and filtering null rows, and writes the output as Parquet back to S3. They configure the job with an appropriate worker type and DPU count, then run it and monitor progress via CloudWatch logs.
- **Supplemental Reading:**
  - 📄 [AWS Official — AWS Glue Jobs Documentation](https://docs.aws.amazon.com/glue/latest/dg/author-job.html)
  - 📄 [AWS Prescriptive Guidance — Best practices for serverless ETL with AWS Glue](https://docs.aws.amazon.com/prescriptive-guidance/latest/serverless-etl-aws-glue/best-practices.html)
  - 📝 [DataCamp — Getting Started with AWS Glue](https://www.datacamp.com/tutorial/aws-glue)
- **Hands-on Activity:** CSV to Parquet Transformation — Write a PySpark Glue Job that reads CSV files from S3, casts date columns to proper timestamp types, removes rows with null primary keys, and writes the result as Parquet into a separate S3 output prefix.
- **Visual Aid:** ✅ Yes — ETL pipeline flow diagram: Raw S3 (CSV) → Glue Job (transform) → Processed S3 (Parquet).

  > This flowchart illustrates the three stages of an AWS Glue ETL job: extract (reading CSV from S3 with automatic schema inference), transform (casting columns to correct types, filtering null rows), and load (writing the cleaned data as compressed Parquet back to S3).

  ```mermaid
  graph LR
      INPUT[("Raw S3<br/>CSV Data")]
      EXTRACT["Extract<br/>Read with Schema Inference"]
      TRANSFORM["Transform<br/>Cast Types · Filter · Clean"]
      LOAD["Load<br/>Write as Parquet"]
      OUTPUT[("Processed S3<br/>Parquet Data")]

      INPUT --> EXTRACT
      EXTRACT --> TRANSFORM
      TRANSFORM --> LOAD
      LOAD --> OUTPUT
  ```

---

#### Day 5: Amazon Athena: Serverless SQL Querying

- **Learning Objective:** Query transformed data in S3 using standard SQL with Athena.
- **Core Idea:** **Amazon Athena** is a serverless interactive query service that allows users to analyse data stored in S3 using standard SQL. It reads table metadata from the Glue Data Catalog and executes queries across data that may be partitioned, compressed, or stored in columnar formats. There is no infrastructure to provision — Athena automatically scales and charges only for the amount of data scanned per query.
- **Why It Matters:** Athena eliminates the need to manage a traditional data warehouse cluster while still supporting complex SQL analytics. When combined with partitioned Parquet data, Athena can deliver sub-second query response times at very low cost. This makes it the natural query layer between the Glue ETL pipeline and the BI visualisation layer.
- **How It Works:** Learners open the Athena console, select the Glue Data Catalog as the data source, and write SQL queries against the tables created by the crawler. They use `SELECT`, `WHERE`, `GROUP BY`, and `JOIN` clauses, then compare query costs and runtimes between unpartitioned CSV data and partitioned Parquet data.
- **Supplemental Reading:**
  - 📄 [AWS Official — Amazon Athena Documentation](https://docs.aws.amazon.com/athena/latest/ug/what-is.html)
  - 📝 [DataCamp — Getting Started with AWS Athena](https://www.datacamp.com/tutorial/aws-athena)
  - 📝 [AWS Blog — Top 10 performance tuning tips for Amazon Athena](https://aws.amazon.com/blogs/big-data/top-10-performance-tuning-tips-for-amazon-athena/)
- **Hands-on Activity:** Athena Query Analysis — Write three Athena queries against the Parquet data from Day 4: a row count, a `GROUP BY` aggregation, and a `JOIN` between two tables. Note the data scanned for each query and compare costs between CSV and Parquet data.
- **Visual Aid:** ✅ Yes — Athena query execution flow diagram: S3 (Parquet) → Glue Catalog (schema) → Athena → Results. [VISUAL PENDING — Skill 4]

---

#### Day 6: Amazon QuickSight: Dashboards & BI

- **Learning Objective:** Build interactive dashboards and natural-language queries with QuickSight.
- **Core Idea:** **Amazon QuickSight** is a cloud-native business intelligence service that enables users to create interactive dashboards, perform ad-hoc analysis, and ask natural-language questions about their data using Amazon Q. It includes the **SPICE** (Super-fast, Parallel, In-memory Calculation Engine) that caches data in memory for rapid visual rendering without querying the source database on every interaction.
- **Why It Matters:** Raw query results are difficult to interpret at a glance — visualisations reveal trends, outliers, and patterns that numbers alone cannot convey. QuickSight's integration with Athena and the Glue Data Catalog means that once data is prepared in the pipeline, building dashboards requires minimal additional configuration.
- **How It Works:** Learners sign into QuickSight, create a new dataset connected to Athena and the Glue Data Catalog, and select the Parquet-backed tables from earlier days. They build a visual analysis by dragging fields onto chart types (bar, line, pivot table), apply filters and date range controls, and publish the analysis as a shared dashboard.
- **Supplemental Reading:**
  - 📄 [AWS Official — Amazon QuickSight Documentation](https://docs.aws.amazon.com/quicksight/latest/user/welcome.html)
  - 📝 [Medium — Data Analysis Made Easy: S3, AWS Glue, Athena and QuickSight](https://medium.com/@ifeanyiobiana/data-analysis-made-easy-s3-aws-glue-athena-and-quicksight-22125e36b3ae)
  - 📝 [AWS Blog — Best practices for Amazon QuickSight dashboard performance](https://aws.amazon.com/blogs/business-intelligence/best-practices-for-amazon-quicksight-dashboard-performance/)
- **Hands-on Activity:** QuickSight Dashboard — Connect QuickSight to the Athena data source, create a new analysis with at least three visualisations (e.g., bar chart of records by category, line chart over time, a KPI card), and publish as a shared dashboard with a date-range filter.
- **Visual Aid:** ✅ Yes — BI dashboard mockup showing key chart types: bar chart, line chart, pivot table, and a KPI tile.

  > This architecture diagram illustrates how Amazon QuickSight connects to the analytics pipeline. Athena queries the Glue Data Catalog, results are cached in the SPICE in-memory engine for fast performance, and QuickSight renders interactive dashboards and natural-language query capabilities for business users.

  ```mermaid
  graph TD
      CATALOG[("Glue Data Catalog")]
      ATHENA["Amazon Athena<br/>SQL Query Layer"]
      SPICE["SPICE Engine<br/>In-Memory Cache"]
      QS["Amazon QuickSight<br/>BI Service"]
      Q_NLP["Amazon Q<br/>Natural Language Queries"]
      DASHBOARD["Interactive Dashboard<br/>Charts & Filters"]
      EMBED["Embedded Analytics<br/>In Applications"]
      USERS["Business Users<br/>Viewers"]

      CATALOG --> ATHENA
      ATHENA --> SPICE
      SPICE --> QS
      QS --> DASHBOARD
      QS --> Q_NLP
      QS --> EMBED
      DASHBOARD --> USERS
      Q_NLP --> USERS
  ```

---

#### Day 7: IAM Deep Dive for Analytics Pipelines

- **Learning Objective:** Design least-privilege IAM policies for every service in the pipeline.
- **Core Idea:** **IAM** (Identity and Access Management) is the AWS service that controls who can perform actions on which resources. A **policy** is a JSON document that defines permissions; a **role** is an identity that assumes policies and can be attached to AWS services (such as Glue or Athena) to grant them temporary credentials. The **principle of least privilege** means granting only the exact permissions needed for a task and nothing more.
- **Why It Matters:** Each service in the analytics pipeline — Glue, Athena, QuickSight — needs its own IAM role with carefully scoped permissions. Overly permissive roles create security risks, while under-permissioned roles cause pipeline failures. Understanding how to write precise policies is essential for building production-grade, auditable data pipelines.
- **How It Works:** Learners write a custom IAM policy that grants a Glue role read access to a specific S3 bucket prefix and write access to the Glue Data Catalog. They attach this policy to a new role and test it by running a crawler. They then use IAM Access Analyzer to verify that the policy does not grant unintended access beyond the specified resources.
- **Supplemental Reading:**
  - 📄 [AWS Official — IAM User Guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
  - 📄 [AWS Official — IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
  - 📝 [DataCamp — AWS IAM Guide](https://www.datacamp.com/tutorial/aws-identity-and-access-management-iam-guide)
- **Hands-on Activity:** Least-Privilege IAM Policy — Write a custom IAM policy that allows only `s3:GetObject` on a specific bucket prefix and `glue:*` on the Data Catalog, attach it to a role, and verify the policy with IAM Access Analyzer.
- **Visual Aid:** ✅ Yes — IAM policy structure diagram showing the JSON format (Effect, Action, Resource, Condition) and a cross-service auth flow. [VISUAL PENDING — Skill 4]

---

#### Day 8: Orchestration & Automation

- **Learning Objective:** Automate multi-step pipelines using Glue triggers, EventBridge, and Step Functions.
- **Core Idea:** **Orchestration** ties individual pipeline steps into an automated, dependency-aware workflow. **AWS Step Functions** builds visual state machines that chain services together (e.g., run a crawler, then a Glue job, then an Athena query). **Glue Triggers** and **Amazon EventBridge** provide time-based and event-based scheduling options for triggering pipeline steps automatically.
- **Why It Matters:** Running each pipeline step manually does not scale and introduces human error. Automated orchestration ensures that data is processed consistently on schedule, downstream steps only run when upstream steps succeed, and failures trigger alerts or retries. This transforms a collection of scripts into a reliable production pipeline.
- **How It Works:** Learners design a Step Functions state machine with three states: start a Glue crawler, wait for completion, run a Glue job. They configure error handling with retry logic and a fallback notification. They also set up an EventBridge rule that triggers the state machine whenever new data arrives in the S3 bucket.
- **Supplemental Reading:**
  - 📄 [AWS Official — AWS Step Functions Documentation](https://docs.aws.amazon.com/step-functions/latest/dg/welcome.html)
  - 📄 [AWS Official — Amazon EventBridge Documentation](https://docs.aws.amazon.com/eventbridge/latest/userguide/what-is-amazon-eventbridge.html)
  - 📝 [DataCamp — Mastering AWS Step Functions](https://www.datacamp.com/tutorial/mastering-aws-step-functions-a-comprehensive-guide)
- **Hands-on Activity:** Step Functions Pipeline — Build a Step Functions state machine with three serial steps: run a Glue crawler, wait for completion, run a Glue job. Add a catch block that sends an SNS notification on failure. Test the workflow by triggering it manually.
- **Visual Aid:** ✅ Yes — Step Functions state machine diagram: S3 upload event → EventBridge → Crawler → Glue Job → Athena query.

  > This flowchart represents an automated Step Functions workflow triggered by an S3 upload event via EventBridge. The state machine runs a Glue crawler, checks for success, proceeds to an ETL job only if the crawler succeeded, and sends an SNS alert on failure — turning a manual sequence into an automated, resilient pipeline.

  ```mermaid
  graph TD
      EVENT["S3 Upload Event<br/>New Data Arrives"]
      RULE["EventBridge Rule<br/>Match Pattern"]
      STATE["Step Functions<br/>State Machine"]
      CRAWLER["Run Glue Crawler<br/>Discover Schema"]
      CHOICE{"Crawler<br/>Succeeded?"}
      JOB["Run Glue ETL Job<br/>Transform to Parquet"]
      SUCCESS["Pipeline Complete"]
      FAIL["Pipeline Failed"]
      ALERT["SNS Notification<br/>Email Alert"]

      EVENT --> RULE
      RULE --> STATE
      STATE --> CRAWLER
      CRAWLER --> CHOICE
      CHOICE -->|Yes| JOB
      CHOICE -->|No| FAIL
      JOB --> SUCCESS
      FAIL --> ALERT
  ```

---

#### Day 9: Data Quality, Monitoring & Alerting

- **Learning Objective:** Monitor pipeline health and enforce data quality checks.
- **Core Idea:** **Amazon CloudWatch** collects metrics and logs from AWS services, enabling real-time monitoring of pipeline health. **Glue Data Quality** is a built-in feature that evaluates datasets against predefined rules (e.g., null checks, row count thresholds, data type validation) and halts pipelines on violations. **CloudWatch Alarms** trigger automated actions (such as an email notification) when metrics cross defined thresholds.
- **Why It Matters:** Data pipelines degrade over time — source data formats change, upstream systems fail, and schema drift occurs. Without monitoring and data quality checks, engineers discover issues only when downstream reports break. Proactive alerting and automated quality gates catch problems early, reducing mean time to detection and preventing bad data from reaching dashboards.
- **How It Works:** Learners navigate to CloudWatch and review the built-in Glue job metrics (DPU usage, job duration, success/failure rate). They create a CloudWatch Alarm that sends an email when a Glue job fails. They then enable Glue Data Quality on a crawler, define a rule that the row count must be greater than zero, and observe how the pipeline behaves when the rule is violated.
- **Supplemental Reading:**
  - 📄 [AWS Official — Amazon CloudWatch Documentation](https://docs.aws.amazon.com/cloudwatch/latest/monitoring/WhatIsCloudWatch.html)
  - 📝 [AWS Blog — Monitor AWS Glue jobs with Amazon CloudWatch](https://aws.amazon.com/blogs/big-data/monitor-aws-glue-jobs-with-amazon-cloudwatch/)
  - 📄 [AWS Official — AWS Glue Data Quality Documentation](https://docs.aws.amazon.com/glue/latest/dg/data-quality.html)
- **Hands-on Activity:** CloudWatch Alarm and Data Quality — Create a CloudWatch Alarm that triggers an SNS email when a Glue job fails. Enable Glue Data Quality on a crawler, add a rule that row count > 0, and verify that a dataset violating the rule causes the pipeline to halt.
- **Visual Aid:** ✅ Yes — CloudWatch dashboard mockup showing Glue job success/failure rate, DPU utilisation, and data quality evaluation results.

  > This architecture diagram shows the monitoring and data quality setup for the pipeline. Glue jobs emit metrics to CloudWatch, which triggers alarms that notify operators via SNS when jobs fail. Glue Data Quality evaluates output datasets against rules and automatically halts the pipeline if quality checks are violated.

  ```mermaid
  graph TD
      GLUE_JOB["AWS Glue Job<br/>ETL Execution"]
      CLOUDWATCH["Amazon CloudWatch<br/>Metrics & Logs"]
      METRICS["Job Metrics<br/>DPU · Duration · Status"]
      ALARM["CloudWatch Alarm<br/>Job Failure Detection"]
      SNS["SNS Topic<br/>Email Notification"]
      DQ["Glue Data Quality<br/>Dataset Evaluation"]
      DQ_RULES["Quality Rules<br/>Row Count > 0<br/>No Null Keys"]
      HALT["Pipeline Halted<br/>On Quality Violation"]

      GLUE_JOB --> CLOUDWATCH
      CLOUDWATCH --> METRICS
      METRICS --> ALARM
      ALARM -->|Breach| SNS
      GLUE_JOB --> DQ
      DQ --> DQ_RULES
      DQ_RULES -.->|Violation| HALT
  ```

---

#### Day 10: Cost Optimization & Governance

- **Learning Objective:** Manage and reduce costs across the serverless analytics stack.
- **Core Idea:** **AWS Cost Explorer** visualises and analyses spending across services, while **AWS Budgets** sends alerts when costs approach or exceed defined thresholds. In the analytics pipeline, costs come primarily from Glue DPU hours, Athena data scanned, S3 storage, and QuickSight SPICE capacity. Strategies such as compressing data, using columnar formats, right-sizing Glue workers, and setting Athena query cost limits directly reduce monthly spending.
- **Why It Matters:** Serverless services are cost-efficient at small scale but can generate unexpectedly large bills without governance. A Glue job running on unnecessarily large worker types or an Athena query scanning terabytes of uncompressed data can cost more than the infrastructure it replaces. Understanding the pricing model of each service and applying cost controls ensures the pipeline remains economical as data volume grows.
- **How It Works:** Learners explore Cost Explorer to view current spending per service. They create a monthly budget of $50 with alerts at 80% and 100% thresholds. They apply Athena workgroup-level cost controls to limit query scan sizes. They right-size a Glue job by testing it with G.1X versus G.2X worker types and comparing runtime and cost.
- **Supplemental Reading:**
  - 📄 [AWS Official — AWS Cost Management Documentation](https://docs.aws.amazon.com/cost-management/latest/userguide/what-is-costmanagement.html)
  - 📝 [AWS Blog — Best practices for cost optimization on AWS Glue](https://aws.amazon.com/blogs/big-data/best-practices-for-cost-optimization-on-aws-glue/)
  - 📝 [DataCamp — AWS Security and Cost Management Concepts](https://www.datacamp.com/courses/aws-security-and-cost-management)
- **Hands-on Activity:** Cost Analysis — Create a monthly AWS Budget of $50 with email alerts. Run the same Glue job with G.1X and G.2X worker types, record the runtime and cost for each, and calculate which is more cost-effective for the workload.
- **Visual Aid:** ✅ Yes — Cost breakdown by service diagram showing relative costs of Glue DPU, Athena queries, S3 storage, and QuickSight across different data sizes. [VISUAL PENDING — Skill 4]

---

*Version: v1.0 | Created: 2026-05-30 | Author: Instructional Designer*
