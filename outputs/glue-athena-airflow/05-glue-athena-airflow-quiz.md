#review: APPROVED

# AWS Glue, Athena & Airflow — Serverless Data Analytics Pipeline
### 05 — glue-athena-airflow — Quiz Generator

---

## 10-Item Multiple Choice Quiz

---

1. In Apache Airflow, what distinguishes a Sensor from an Operator?

   A. Sensors trigger DAG runs, while Operators define the DAG schedule
   B. Sensors wait for a condition to be met, while Operators execute a defined action
   C. Sensors pass data between tasks, while Operators manage task dependencies
   D. Sensors handle error notifications, while Operators orchestrate retry logic

---

2. An engineer needs to query a Gold Iceberg table as it appeared before a batch of erroneous updates was applied three hours ago. Which Iceberg feature makes this possible without restoring from a backup?

   A. Schema evolution
   B. Hidden partitioning
   C. Snapshot-based time travel
   D. Row-level upsert via MERGE

---

3. Which statement describes the role of the Silver layer in the Medallion data lake architecture?

   A. It stores raw ingested data in its original format with no transformations
   B. It contains business-ready aggregated datasets for dashboard consumption
   C. It stores cleaned and validated data in columnar format partitioned by business keys
   D. It writes data directly to an external relational database for transactional workloads

---

4. A Glue ETL pipeline processes daily order files. The job applies DQDL rules and routes failing records to a quarantine S3 prefix. What is the primary benefit of this quarantine pattern over silently dropping the failing records?

   A. It reduces storage costs by isolating bad data in a cheaper S3 storage class
   B. It preserves failed records for audit, investigation, and reprocessing after root cause correction
   C. It automatically retries failed records three times before permanently deleting them
   D. It sends an alert to the data engineering team each time a record fails validation

---

5. A Glue ETL job reads a CSV source where the `payment_value` column contains numeric values in most rows but includes the string "NULL" in some rows. Which approach handles this schema inconsistency without failing the job?

   A. Using a DynamicFrame so Glue preserves the choice type for manual resolution
   B. Using a Spark DataFrame with a pre-defined schema to filter out mismatched rows
   C. Converting all columns to string type before loading the data
   D. Setting the Spark configuration `spark.sql.schema.forceNullable` to true

---

6. An organization assigns separate IAM roles for Glue Crawlers, Glue ETL jobs, and Athena queries. An engineer discovers the QuickSight role has `s3:DeleteObject` on the entire data lake bucket. Which security principle is being violated?

   A. Separation of duties
   B. Least-privilege access
   C. Defense in depth
   D. Credential rotation

---

7. An analytics team frequently runs ad-hoc queries that scan large datasets. A single query scanning 50 TB of data could cost hundreds of dollars. Which Athena feature should a data administrator configure to prevent this scenario?

   A. A Glue Crawler that partitions data by month
   B. A per-query data scan limit on the team's Athena Workgroup
   C. A Lake Formation data filter limiting row access
   D. An S3 lifecycle policy that transitions old data to Glacier

---

8. How does a Glue Crawler detect partitions when scanning an S3 data source?

   A. It inspects the file header of each Parquet file for partition column names
   B. It infers partition boundaries from the S3 folder structure, such as `year=2026/month=06/`
   C. It executes a Spark SQL `SHOW PARTITIONS` statement against the Data Catalog
   D. It reads a separate partition definition file stored alongside the data in S3

---

9. In an MWAA DAG, a GlueJobOperator starts an AWS Glue job and produces a JobRunId. A downstream AthenaOperator needs this JobRunId to verify the job completed. How should the GlueJobOperator make the JobRunId available to the downstream task?

   A. Write the JobRunId to a temporary file stored on the Airflow worker's local disk
   B. Push the JobRunId to an XCom, which the AthenaOperator pulls in its execution context
   C. Store the JobRunId as an Airflow Variable set during DAG initialization
   D. Pass the JobRunId as a command-line argument to the AthenaOperator's bash command

---

10. A daily Glue ETL job writes new order data to a Silver table, and an Athena MERGE statement updates the Gold revenue summary table. What happens when a MERGE statement finds matching rows between the source and target tables?

   A. Matching rows are deleted from the target and re-inserted from the source
   B. The matching rows in the target table are updated with the source values
   C. An error is raised because duplicate keys are not allowed in Iceberg
   D. The existing rows remain unchanged and the new rows are appended

---

## ANSWER KEY

1. **B** — Sensors wait for a condition (e.g., file arrival, job completion) before allowing downstream tasks to proceed, while Operators execute a defined action like running a Glue job or Athena query.

2. **C** — Iceberg's snapshot-based time travel allows querying a table as of any previous snapshot using `SELECT ... FOR SYSTEM_TIME AS OF`, making it possible to see data before erroneous updates without a backup restore.

3. **C** — The Silver layer stores cleaned, validated data in columnar Parquet format, partitioned by business keys, serving as the intermediate quality-controlled layer between raw Bronze and aggregated Gold.

4. **B** — The quarantine pattern preserves failed records in a dedicated S3 prefix so data stewards can audit quality issues, investigate root causes, and reprocess corrected data through the pipeline.

5. **A** — DynamicFrames handle schema inconsistencies by preserving choice types, giving the engineer explicit control to resolve type conflicts via `ResolveChoice` instead of failing or silently coercing.

6. **B** — Least-privilege access requires each role to have only the permissions needed for its function. A QuickSight role should not have `s3:DeleteObject` on the data lake bucket.

7. **B** — Athena Workgroups can enforce per-query data scan limits that cap the maximum amount of data any single query can scan, preventing runaway queries from incurring excessive costs.

8. **B** — Glue Crawlers detect partitions by interpreting S3 folder structure conventions (e.g., `year=2026/month=06/`) and registering those partitions in the Glue Data Catalog automatically.

9. **B** — XComs (cross-communications) allow Airflow tasks to share small amounts of metadata. The GlueJobOperator pushes the JobRunId to XCom, and the downstream AthenaOperator pulls it within its execution context.

10. **B** — The `WHEN MATCHED THEN UPDATE` clause in Iceberg's MERGE statement updates the matching rows in the target table with values from the source, while unmatched rows are inserted.

---

Quiz complete. Review all questions against the learning path content and validate that each correct answer is accurately reflected in the material. Proceed to Checkpoint 3 for final review of the full learning path.

---

*Version: v1.0 | Created: 2026-06-01 | Author: Instructional Designer*
