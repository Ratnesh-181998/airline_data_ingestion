# airline_data_ingestion
Airline_Data_Ingestion using AWS service's 

<img width="946" height="702" alt="image" src="https://github.com/user-attachments/assets/d8d7d974-6020-4b63-87d5-037ab1a601af" />

---

````markdown
# ✈️ Airline Data Ingestion Project

## 📌 Project Overview

The **Airline Data Ingestion Project** is an event-driven AWS Data Engineering pipeline that automatically ingests daily flight data from Amazon S3 into an Amazon Redshift Fact Table.

The pipeline uses AWS managed services to automate schema discovery, ETL processing, orchestration, monitoring, and notifications.

---

# 🎯 Objective

Build a scalable and serverless ETL pipeline that:

- Detects newly uploaded flight data files
- Discovers schema automatically
- Performs ETL transformations
- Loads processed data into Amazon Redshift
- Sends success/failure notifications
- Supports daily batch ingestion

---

# 🏗️ Architecture

```text
                 Daily Flight Data
                         │
                         ▼
                  Amazon S3 Bucket
                         │
         S3 Event Notification (Object Created)
                         │
                         ▼
                 Amazon EventBridge
                         │
                  EventBridge Rule
                         │
                         ▼
                AWS Step Functions
               /                  \
              /                    \
             ▼                      ▼
     AWS Glue Crawler      AWS Glue Visual ETL
             │                      │
             │              Clean & Transform
             │                      │
             ▼                      ▼
     Glue Data Catalog      Amazon Redshift
                                  │
                                  ▼
                          Flight Fact Table
                                  │
                                  ▼
                            Amazon SNS
                   (Success/Failure Alert)
```

---

# 🛠️ Tech Stack

- Amazon S3
- S3 Event Notification
- Amazon EventBridge
- EventBridge Rule
- AWS Step Functions
- AWS Glue Crawler
- AWS Glue Visual ETL
- Amazon Redshift
- Amazon SNS

---

# 📂 Project Workflow

## Step 1 – Upload Flight Data

Daily airline data files are uploaded into an Amazon S3 bucket.

Supported formats:

- CSV
- JSON
- Parquet

---

## Step 2 – S3 Event Notification

Whenever a new file is uploaded, Amazon S3 generates an Object Created event.

---

## Step 3 – EventBridge

Amazon EventBridge receives the S3 event.

An EventBridge Rule filters the event and triggers the AWS Step Function.

---

## Step 4 – AWS Step Functions

Step Functions orchestrates the complete workflow.

Workflow:

1. Run Glue Crawler
2. Wait until completion
3. Trigger Glue ETL Job
4. Check job status
5. Send SNS notification

---

## Step 5 – AWS Glue Crawler

The crawler scans the uploaded dataset.

It automatically:

- Detects schema
- Detects new columns
- Updates Glue Data Catalog
- Creates metadata tables

---

## Step 6 – AWS Glue Visual ETL

The Glue Visual ETL job performs:

- Data validation
- Data cleansing
- Remove duplicates
- Handle null values
- Standardize formats
- Business transformations
- Generate derived columns

Finally, the processed data is loaded into Amazon Redshift.

---

## Step 7 – Amazon Redshift

The transformed data is inserted into the Flight Fact Table.

Example fact table columns:

| Column |
|----------|
| Flight_ID |
| Airline |
| Flight_Date |
| Source |
| Destination |
| Departure_Time |
| Arrival_Time |
| Delay |
| Distance |
| Ticket_Price |

---

## Step 8 – Amazon SNS

SNS sends an email notification after pipeline execution.

Possible notifications:

- ETL Job Successful
- ETL Failed
- Glue Job Failed
- Redshift Load Failed

---

# 📁 AWS Services Used

| AWS Service | Purpose |
|-------------|----------|
| Amazon S3 | Store raw flight data |
| S3 Event Notification | Detect new files |
| Amazon EventBridge | Event routing |
| EventBridge Rule | Trigger Step Functions |
| AWS Step Functions | Workflow orchestration |
| AWS Glue Crawler | Metadata discovery |
| AWS Glue Visual ETL | Data transformation |
| Amazon Redshift | Data warehouse |
| Amazon SNS | Email/SMS notifications |

---

# 📊 Data Flow

```
Flight File
      │
      ▼
Amazon S3
      │
      ▼
S3 Event Notification
      │
      ▼
Amazon EventBridge
      │
      ▼
EventBridge Rule
      │
      ▼
AWS Step Functions
      │
      ├─────────────► Glue Crawler
      │
      └─────────────► Glue ETL
                          │
                          ▼
                 Amazon Redshift
                          │
                          ▼
                      Amazon SNS
```

---

# 🚀 Features

- Fully Serverless
- Event-driven Architecture
- Automatic Schema Discovery
- Visual ETL Pipeline
- Automated Redshift Loading
- Metadata Management
- Email Notifications
- Scalable Architecture
- Low Maintenance
- Cloud Native

---

# 📈 Benefits

- No manual intervention
- Automatic schema evolution
- Highly scalable
- Cost-effective
- Reliable workflow orchestration
- Easy monitoring
- Faster analytics
- Secure data ingestion

---

# 📋 Prerequisites

- AWS Account
- IAM Roles
- Amazon S3 Bucket
- AWS Glue
- Amazon Redshift Cluster
- Amazon SNS Topic
- EventBridge Rule
- Step Function State Machine

---

# 📌 Use Cases

- Airline Analytics
- Flight Delay Analysis
- Ticket Price Analytics
- Airport Traffic Analysis
- Flight Performance Dashboard
- Business Intelligence Reporting

---

# 📚 Future Enhancements

- Incremental Data Loading
- CDC (Change Data Capture)
- Data Quality Checks
- Glue Job Bookmark
- CloudWatch Monitoring
- Lambda-based Validation
- CI/CD Pipeline
- Terraform Infrastructure
- Data Lake Integration
- Lake Formation Governance

---

# 🎯 Interview Questions

### AWS

- Why use EventBridge instead of Lambda?
- Why Step Functions?
- Difference between EventBridge and SNS.
- Difference between Glue Crawler and Glue ETL.
- What is Glue Data Catalog?

### Redshift

- What is a Fact Table?
- What are Distribution Keys?
- What are Sort Keys?
- COPY Command vs INSERT?
- How do you optimize Redshift performance?

### ETL

- How do you handle duplicate records?
- How do you process incremental data?
- What is schema evolution?
- How do you retry failed jobs?

### Architecture

- Why S3 first instead of directly loading into Redshift?
- How is the pipeline monitored?
- How do you make it fault tolerant?
- How would you scale the pipeline for TBs of data?

---

# 📌 Conclusion

This project demonstrates a production-ready, event-driven AWS Data Engineering pipeline that automates the ingestion of daily airline data into Amazon Redshift using AWS Glue, Step Functions, EventBridge, and SNS. It showcases modern cloud-native ETL architecture with automatic schema discovery, scalable processing, workflow orchestration, and real-time notifications, making it an excellent portfolio project for AWS Data Engineering roles.
````
