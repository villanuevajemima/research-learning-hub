#review: DRAFT

# AWS Serverless Data Analytics Pipeline
### 05 — aws-serverless-data-analytics — Quiz Generator

---

## Quiz

1. Which AWS service is responsible for automatically discovering schema from data stored in S3 and populating a central metadata repository?

   A. Amazon Athena
   B. AWS Glue Crawler
   C. AWS Glue Job
   D. Amazon QuickSight

2. What is the primary purpose of the SPICE engine in Amazon QuickSight?

   A. To transform data from CSV to Parquet format
   B. To cache data in memory for fast dashboard rendering
   C. To crawl S3 buckets and infer schema
   D. To orchestrate multi-step data pipelines

3. A data engineer needs to limit the amount of data an Athena query can scan to control costs. Which mechanism should be used?

   A. IAM policy with `athena:LimitScanSize`
   B. Athena workgroup-level query cost controls
   C. S3 bucket lifecycle policy
   D. Glue Data Quality rule

4. Which AWS service builds visual state machines that chain multiple pipeline steps with dependency-aware error handling?

   A. Amazon EventBridge
   B. AWS Glue Triggers
   C. AWS Step Functions
   D. Amazon CloudWatch

5. An engineer wants to grant an AWS Glue job read access only to a specific S3 bucket prefix. What is the correct approach?

   A. Create an IAM user with long-term credentials and store them in the Glue job
   B. Attach a broad `s3:*` policy to the Glue service role
   C. Write a custom IAM policy with `s3:GetObject` on the specific bucket prefix and attach it to a Glue service role
   D. Use S3 bucket policies with a condition key for `aws:SourceService`

6. What is a key difference between S3 Standard and S3 Glacier storage classes?

   A. S3 Glacier stores data in a columnar format while S3 Standard stores it as objects
   B. S3 Glacier offers lower storage costs but higher retrieval times compared to S3 Standard
   C. S3 Standard is serverless while S3 Glacier requires provisioning
   D. S3 Glacier automatically transforms data to Parquet while S3 Standard does not

7. What is a Glue Data Quality rule designed to do when a dataset violates its conditions?

   A. Automatically correct the data and rerun the pipeline
   B. Log the violation and continue processing
   C. Halt the pipeline and prevent the violation from reaching downstream consumers
   D. Send the data to a separate S3 bucket for manual review

8. An AWS Region contains multiple isolated data centers. What are these data centers called?

   A. Edge locations
   B. Availability Zones
   C. VPC subnets
   D. Data Catalog partitions

9. Which format is recommended as the output of a Glue ETL job to optimise query performance and reduce Athena costs?

   A. CSV
   B. JSON
   C. Parquet
   D. XML

10. How does Amazon Athena determine which files to scan when a query is executed against partitioned data?

    A. It scans all files in the bucket and filters results after reading
    B. It reads partition metadata from the Glue Data Catalog and scans only the relevant S3 prefixes
    C. It uses a secondary index stored in DynamoDB
    D. It relies on the QuickSight SPICE engine to identify relevant partitions

---

## ANSWER KEY

1. **B** — A Glue Crawler automatically scans S3 data sources, infers schema, and populates the Glue Data Catalog with table definitions.
2. **B** — SPICE (Super-fast, Parallel, In-memory Calculation Engine) caches data in memory in QuickSight, enabling rapid visual rendering without querying the source on every interaction.
3. **B** — Athena workgroup-level cost controls allow engineers to set limits on the amount of data scanned per query, preventing unexpectedly large bills.
4. **C** — AWS Step Functions builds visual state machines that chain services together with built-in error handling, retry logic, and conditional branching.
5. **C** — The principle of least privilege requires writing a custom IAM policy that grants only the specific actions needed on the specific resources, then attaching it to a service role.
6. **B** — S3 Glacier has lower storage costs than S3 Standard but is designed for archival data where retrieval times of minutes to hours are acceptable.
7. **C** — Glue Data Quality evaluates datasets against predefined rules and halts the pipeline when violations occur, preventing bad data from reaching downstream consumers.
8. **B** — Availability Zones are isolated data centers within an AWS Region, providing fault tolerance and low-latency connectivity.
9. **C** — Columnar formats like Parquet dramatically reduce scan volume, speed up queries, and lower Athena costs compared to row-based formats like CSV or JSON.
10. **B** — Athena reads table and partition metadata from the Glue Data Catalog, then uses partition pruning to scan only the S3 prefixes that match the query's filter conditions, reducing data scanned and cost.

---

*Version: v1.0 | Created: 2026-05-30 | Author: Instructional Designer*
