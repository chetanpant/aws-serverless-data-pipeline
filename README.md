# Serverless Data Processing Pipeline on AWS

## Overview

This project builds a serverless data processing pipeline on AWS using event-driven architecture.

The system automatically processes uploaded files, extracts metadata, logs processing details, and stores results in a database without requiring any continuously running servers.

This project was completed as part of the Cloud Services and Platforms course at BITS Pilani.

---

## Problem Statement

Traditional data pipelines rely on continuously running servers to monitor and process incoming data.

This leads to:
- unnecessary resource usage
- higher cost
- scalability limitations

This project solves the problem using a serverless, event-driven architecture.

---

## Architecture

The pipeline follows this flow:

User Upload → Amazon S3 → AWS Lambda → CloudWatch Logs → DynamoDB

![Architecture Diagram](architecture/architecture_diagram.png)

---

## Services Used

- Amazon S3 → data ingestion
- AWS Lambda → processing logic
- Amazon DynamoDB → metadata storage
- Amazon CloudWatch → logging and monitoring
- AWS IAM → access control

---

## How the System Works

1. User uploads a CSV file to S3  
2. S3 triggers Lambda automatically (PUT event)  
3. Lambda reads the file and extracts:
   - file name
   - file type
   - file size
   - row count
   - column count  
4. Logs are written to CloudWatch  
5. Metadata is stored in DynamoDB  

This process runs automatically without manual intervention :contentReference[oaicite:3]{index=3}  

---

## Security Design

Security was implemented using:

- IAM user with least privilege access
- separate Lambda execution role
- restricted permissions for each service
- S3 bucket with public access blocked  

User and service permissions were separated to ensure secure design :contentReference[oaicite:4]{index=4}  

---

## Why Serverless Architecture

Event-driven design was used because:

- no need for continuously running servers
- reduces cost
- scales automatically
- processes only when data arrives  

Lambda executes only when triggered by S3 events :contentReference[oaicite:5]{index=5}  

---

## Output Validation

The pipeline was validated using:

### CloudWatch Logs

- logs show file metrics:
  - file name
  - size
  - rows
  - columns

### DynamoDB Table

- metadata stored successfully after upload
- confirms end-to-end execution

Both outputs matched correctly, validating the system :contentReference[oaicite:6]{index=6}  

---

## Key Learnings

- difference between IAM user and execution role
- importance of least-privilege design
- practical understanding of event-driven systems
- integration of multiple AWS services into a working pipeline  

---

## Possible Improvements

- add SNS notifications for processing alerts
- implement error handling for invalid files
- enable S3 versioning for tracking uploads
- extend pipeline for real-time analytics  

---

## Repository Structure
aws-serverless-data-pipeline/

├── README.md
├── docs/
│ └── project_report.pdf


---

## Project Context

This project was developed as part of the Cloud Services and Platforms course.

It demonstrates:

- cloud architecture design
- serverless systems
- AWS service integration
- secure system design
- real-world pipeline implementation
