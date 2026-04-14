# AWS Integrated GRC Platform

## Governance, Risk, and Compliance Capstone Project

![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![CloudFormation](https://img.shields.io/badge/CloudFormation-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)

---

## 📌 Project Overview

The **AWS Integrated GRC Platform** is a comprehensive Governance, Risk, and Compliance solution built entirely on Amazon Web Services. This capstone project demonstrates how to design, deploy, and manage an enterprise-grade GRC platform using Infrastructure as Code, serverless computing, and native AWS security services.

The platform integrates **13 AWS services** to provide:
- ✅ Continuous compliance monitoring across multiple frameworks
- ✅ Automated risk assessment and scoring
- ✅ Centralized audit logging with immutable trails
- ✅ Real-time compliance dashboards
- ✅ Infrastructure as Code for reproducibility

### Supported Compliance Frameworks

| Framework | Full Name |
|-----------|-----------|
| **ISO 27001:2022** | Information Security Management System |
| **NIST CSF** | Cybersecurity Framework |
| **PCI DSS 3.2.1** | Payment Card Industry Data Security Standard |
| **HIPAA** | Health Insurance Portability and Accountability Act |
| **GDPR** | General Data Protection Regulation |
| **SOC 2** | Service Organization Control |

---

## 🏗️ Architecture Overview
┌─────────────────────────────────────────────────────────────────────────────┐
│ AWS CLOUD - us-east-1 Region │
└─────────────────────────────────────────────────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────────────────┐
│ VPC (10.0.0.0/16) │
├─────────────────────────────────────┬───────────────────────────────────────┤
│ PUBLIC SUBNETS │ PRIVATE SUBNETS │
│ ┌─────────────────────┐ │ ┌─────────────────────────────┐ │
│ │ Application Load │ │ │ Amazon RDS (MySQL) │ │
│ │ Balancer │ │ │ grc-database │ │
│ │ (Port 80/443) │ │ │ (Private - No Internet) │ │
│ └─────────┬───────────┘ │ └──────────────┬──────────────┘ │
│ │ │ │ │
│ ▼ │ ▼ │
│ ┌─────────────────────┐ │ ┌─────────────────────────────┐ │
│ │ ECS Fargate │ │ │ AWS Lambda │ │
│ │ (Container) │◄─────────│ │ grc-compliance-monitor │ │
│ │ Port 8000 │ │ │ (Python 3.11) │ │
│ └─────────────────────┘ │ └──────────────┬──────────────┘ │
│ │ │ │
│ │ ▼ │
│ │ ┌─────────────────────────────┐ │
│ │ │ DynamoDB │ │
│ │ │ grc-compliance-status │ │
│ │ │ (Real-time compliance) │ │
│ │ └─────────────────────────────┘ │
└─────────────────────────────────────┴───────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ AWS NATIVE SERVICES │
├─────────────────┬─────────────────┬─────────────────┬───────────────────────┤
│ AWS Config │ CloudTrail │ CloudWatch │ Amazon S3 │
│ (Compliance │ (Audit Logs) │ (Monitoring) │ (Evidence & Reports) │
│ Monitoring) │ │ │ │
└─────────────────┴─────────────────┴─────────────────┴───────────────────────┘

text

---

## 📊 Live Dashboard

The GRC dashboard provides real-time visibility into compliance status:

- **Dashboard:** [https://dvdhoxwdqhbgq.cloudfront.net](https://dvdhoxwdqhbgq.cloudfront.net)
### Dashboard Features

| Feature | Displayed Value |
|---------|-----------------|
| Average Compliance | 86% |
| Critical Risks | 1 |
| Active Frameworks | 6 |
| Total Risks | 6 |

### Compliance Scores

| Framework | Compliance |
|-----------|------------|
| ISO 27001:2022 | 85% |
| NIST CSF | 78% |
| PCI DSS | 92% |
| HIPAA | 88% |
| GDPR | 81% |
| SOC 2 | 90% |

---

## 📁 Project Structure
GRC-CAPSTONE-PROJECT/
├── README.md # Project documentation
├── network-stack.yaml # CloudFormation - VPC, subnets, security groups
├── database-stack.yaml # CloudFormation - RDS, S3, DynamoDB
├── lambda_compliance_monitor.py # Lambda function for compliance monitoring
├── test_cases.py # Comprehensive test suite (22 tests)
├── sample_data.sql # Sample GRC data
├── index.html # Project documentation website
├── presentation-slides.pdf # Capstone presentation slides
├── project-report.pdf # Detailed project report
├── demo-video.mp4 # Screen recording demonstration
└── docs/
├── architecture-diagram.md # Architecture design documentation
├── deployment-guide.md # Step-by-step deployment instructions
└── troubleshooting.md # Common issues and solutions

text

---

## 🚀 AWS Resources Deployed

| Service | Resource Name | Purpose |
|---------|---------------|---------|
| **CloudFormation** | grc-network, grc-database | Infrastructure as Code |
| **VPC** | grc-vpc (10.0.0.0/16) | Isolated network |
| **Subnets** | 2 public, 2 private | Network segmentation |
| **Security Groups** | ALB, ECS, RDS | Traffic control (firewalls) |
| **RDS** | grc-database | MySQL 8.0, GRC data storage |
| **Lambda** | grc-compliance-monitor | Automated compliance checking |
| **DynamoDB** | grc-compliance-status, grc-risk-register, grc-controls | Real-time compliance status |
| **S3** | evidence, reports, config, cloudtrail logs | Evidence and report storage |
| **AWS Config** | default recorder | Continuous compliance monitoring |
| **CloudTrail** | grc-trail | API audit logging |
| **CloudWatch** | GRC-Compliance-Dashboard | Monitoring and alerts |
| **SNS** | grc-compliance-alerts | Notification service |
| **ECS** | grc-cluster | Dashboard container hosting |
| **CloudFront** | Distribution | HTTPS content delivery |
| **IAM** | grc-admin user, Lambda roles | Access control |
| **KMS** | grc-db-key, grc-s3-key | Encryption at rest |

---

## 🧪 Test Results

All **22 tests pass**:

```bash
test_compliance_percentage_calculation ... ok
test_compliance_report_generation ... ok
test_non_compliant_rules_detection ... ok
test_risk_level_classification ... ok
test_risk_matrix_values ... ok
test_risk_score_calculation ... ok
test_asset_classification_validation ... ok
test_control_id_format_validation ... ok
test_criticality_level_validation ... ok
test_risk_status_validation ... ok
test_compliance_snapshot_structure ... ok
test_control_record_structure ... ok
test_risk_register_structure ... ok
test_framework_control_count ... ok
test_framework_version_format ... ok
test_audit_log_action_types ... ok
test_audit_log_entity_types ... ok
test_audit_log_entry_structure ... ok
test_compliance_report_content ... ok
test_risk_report_content ... ok
test_compliance_to_risk_workflow ... ok
test_control_to_audit_workflow ... ok

----------------------------------------------------------------------
Ran 22 tests in 0.012s

OK
📋 Prerequisites
Requirement	Version
AWS Account	Free Tier eligible
AWS CLI	v2.x
Python	3.11+
MySQL Client	8.0+
Git	Latest
🚀 Quick Deployment
1. Clone the Repository
bash
git clone https://github.com/JoyAnunwa/GRC-CAPSTONE-PROJECT.git
cd GRC-CAPSTONE-PROJECT
2. Configure AWS CLI
bash
aws configure
# Enter: Access Key ID, Secret Access Key, region: us-east-1, output: json
3. Deploy Network Stack
bash
aws cloudformation create-stack --stack-name grc-network --template-body file://network-stack.yaml --parameters ParameterKey=EnvironmentName,ParameterValue=grc --region us-east-1
4. Deploy Database Stack
bash
aws cloudformation create-stack --stack-name grc-database --template-body file://database-stack.yaml --parameters ParameterKey=EnvironmentName,ParameterValue=grc ParameterKey=DBUsername,ParameterValue=grcadmin ParameterKey=DBPassword,ParameterValue=YourPassword123! --capabilities CAPABILITY_IAM --region us-east-1
5. Load Sample Data
bash
mysql -h $(aws cloudformation describe-stacks --stack-name grc-database --query "Stacks[0].Outputs[?OutputKey=='DatabaseEndpoint'].OutputValue" --output text) -u grcadmin -p grcdb < sample_data.sql
6. Deploy Lambda Function
bash
zip lambda_compliance_monitor.zip lambda_compliance_monitor.py
aws lambda create-function --function-name grc-compliance-monitor --runtime python3.11 --role arn:aws:iam::$(aws sts get-caller-identity --query Account --output text):role/grc-lambda-role --handler lambda_compliance_monitor.lambda_handler --zip-file fileb://lambda_compliance_monitor.zip --timeout 60 --memory-size 256 --region us-east-1
7. Run Tests
bash
python3 test_cases.py
📈 Sample Data
The database contains the following sample GRC data:

Table	Record Count	Description
frameworks	5	ISO 27001, NIST, PCI DSS, HIPAA, GDPR, SOC 2
controls	16	Security controls with implementation status
risks	8	Identified risks with probability × impact scores
assets	6	Company assets with criticality levels
compliance_summary	16	Historical compliance percentages
audit_logs	8	Record of all changes
🔧 Troubleshooting
Common Issues and Solutions
Issue	Solution
RDS connection timeout	Ensure RDS is publicly accessible or use bastion host
CloudFormation stack rollback	Check backup retention period (Free Tier: set to 1 day)
Lambda permission errors	Attach proper IAM policies (AWSLambdaBasicExecutionRole, DynamoDB access)
S3 bucket policy errors	Add bucket policy allowing Config and CloudTrail to write
For detailed troubleshooting, see docs/troubleshooting.md

📚 Documentation
Document	Description
Project Report	Detailed project documentation
Presentation Slides	Capstone presentation
Deployment Guide	Step-by-step instructions
Architecture Design	System architecture documentation
Troubleshooting Guide	Common issues and solutions

## 🎥 Live Demonstration

Watch the complete platform demonstration:

**Video:** [Demo Video](./demo-video.mp4)

**Dashboard:** https://dvdhoxwdqhbgq.cloudfront.net

**Project Website:** https://joyanunwa-aws-grc-project.netlify.app

🏆 Key Achievements
✅ 13 AWS services integrated into a working GRC platform

✅ 6 compliance frameworks supported

✅ 22/22 comprehensive tests passing

✅ Complete Infrastructure as Code using CloudFormation

✅ Automated compliance monitoring with Lambda

✅ Live dashboard accessible via CloudFront

✅ Audit logging with CloudTrail

✅ 500+ CLI commands executed and documented

📧 Contact
Author: Joy Anunwa
Course: GRC208 - Governance, Risk, and Compliance Capstone
Date: April 2026

📄 License
This project is for educational purposes as part of the GRC208 capstone requirement.

🙏 Acknowledgments
AWS Academy for the learning environment

Course instructors for guidance and support

Open source community for tools and libraries


