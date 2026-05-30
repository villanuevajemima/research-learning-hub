#review: DRAFT

# AWS Serverless Data Analytics Pipeline
### 04 — aws-serverless-data-analytics — Visual Generator

---

## Visuals

### Day 3: AWS Glue: Crawlers, Data Catalog & Schema Discovery

**Recommended diagram type:** Flowchart
**Reason:** A flowchart best captures the linear, step-by-step process of data flowing from S3 through the crawler into the Data Catalog, and then being consumed by downstream services.

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

> This flowchart traces the data discovery process: a Glue crawler scans CSV files in S3, optionally applies a classifier for custom formats, and populates the Glue Data Catalog with table definitions. Once catalogued, the metadata is immediately available to Athena, Glue Jobs, and Redshift Spectrum.

---

### Day 4: AWS Glue: ETL Jobs with Spark & PySpark

**Recommended diagram type:** Flowchart
**Reason:** A flowchart best represents the sequential ETL stages — extract, transform, load — which is inherently a linear data processing pipeline.

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

> This flowchart illustrates the three stages of an AWS Glue ETL job: extract (reading CSV from S3 with automatic schema inference), transform (casting columns to correct types, filtering null rows), and load (writing the cleaned data as compressed Parquet back to S3).

---

### Day 6: Amazon QuickSight: Dashboards & BI

**Recommended diagram type:** Architecture Diagram
**Reason:** An architecture diagram best shows how QuickSight connects to upstream data sources, caches data in SPICE, and serves visualisations to end users.

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

> This architecture diagram illustrates how Amazon QuickSight connects to the analytics pipeline. Athena queries the Glue Data Catalog, results are cached in the SPICE in-memory engine for fast performance, and QuickSight renders interactive dashboards and natural-language query capabilities for business users.

---

### Day 8: Orchestration & Automation

**Recommended diagram type:** Flowchart
**Reason:** A flowchart best captures the branching logic, sequential steps, and error handling path of a Step Functions state machine.

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

> This flowchart represents an automated Step Functions workflow triggered by an S3 upload event via EventBridge. The state machine runs a Glue crawler, checks for success, proceeds to an ETL job only if the crawler succeeded, and sends an SNS alert on failure — turning a manual sequence into an automated, resilient pipeline.

---

### Day 9: Data Quality, Monitoring & Alerting

**Recommended diagram type:** Architecture Diagram
**Reason:** An architecture diagram best shows how Glue jobs, CloudWatch metrics, alarms, and data quality rules interact as a monitoring ecosystem.

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

> This architecture diagram shows the monitoring and data quality setup for the pipeline. Glue jobs emit metrics to CloudWatch, which triggers alarms that notify operators via SNS when jobs fail. Glue Data Quality evaluates output datasets against rules and automatically halts the pipeline if quality checks are violated.

---

*Version: v1.0 | Created: 2026-05-30 | Author: Instructional Designer*
