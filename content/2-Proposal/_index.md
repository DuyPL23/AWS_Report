---
title: "Proposal"
date: 2025-09-16
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

In this section, you need to summarize the content of the workshop you **plan** to conduct.

# Studying English Website  

### 1. Executive Summary  
The Studying English Website is designed for English learners to enhance their vocabulary, grammar, and daily communication skills. The platform leverages **AWS Serverless services** to provide monitoring of learning time, predictive analysis of learners' abilities, and guidance for learning policies from basic to advanced levels, while keeping costs minimal.  

### 2. Problem Statement  
*Current Problem*  
English is an essential language for work and daily life. However, learners currently lack a dedicated environment and space for practice, especially in communication skills.  

*Solution*  

*Benefits and ROI*  
The solution creates a foundational platform for members to develop a larger IoT platform while providing data sources for AI research, training models, or analysis. The platform reduces manual reporting for each learner through a centralized system, simplifies management and maintenance, and improves data reliability. Monthly costs are estimated at $0.66 (per AWS Pricing Calculator), totaling $7.92 for 12 months. All IoT devices are already available, so no additional development costs are required. The payback period is 6–12 months due to significant savings in manual operations.  

### 3. Solution Architecture  

![Studying English Website Architecture]()

![Studying English Website Architecture]()

*AWS Services Used*  
- **AWS S3**: Stores raw data (data lake) and processed data (2 buckets)  
- **AWS Amplify gen 2**: Hosts the web interface  
- **AWS MediaConvert**: Processes media content  
- **AWS Route53**: Manages domain and DNS  
- **AWS Cognito**: User management and authentication  
- **AWS Secrets Manager**: Stores sensitive information  
- **AWS IAM**: Access control and permissions  
- **AWS Lambda**: Backend data processing  
- **AWS WAF**: Web application firewall  

*Component Design*  
- *Technical Deployment*:  
- *Deployment Phases*:  
- *Project Includes*:  
- *Data Processing*: AWS Glue Crawlers index data; ETL jobs transform data for analysis.  
- *Web Interface*: AWS Amplify hosts the Next.js application for dashboard and real-time analytics.  
- *User Management*: Amazon Cognito limits to 5 active accounts.  

### 4. Technical Deployment  
*Deployment Phases*  
The project includes 2 parts — backend setup and web platform development — each undergoing 4 phases:  
1. *Research and Architecture Design*: Study Next.js and AWS Serverless architecture (1 month before the internship).  
2. *Cost Estimation and Feasibility Check*: Use AWS Pricing Calculator to estimate and adjust (Month 1).  
3. *Architecture Optimization*: Fine-tune services (e.g., optimize Lambda with Next.js) to ensure efficiency (Month 2).  
4. *Development, Testing, Deployment*: Implement AWS services and Next.js, test, and launch (Month 2–3).  

*Technical Requirements*  
- *Edge Devices*: N/A (since this is web-based)  
- *Platform*: Practical knowledge of AWS Amplify (Next.js hosting), Lambda (minimized as Next.js handles some logic), AWS Glue (ETL), S3 (2 buckets), IoT Core (gateway and rules if needed), and Cognito (5 users). Use AWS CDK/SDK to program services. Next.js helps reduce Lambda load for fullstack web application.  

### 5. Roadmap & Milestones  
- *Before Internship (Month 0)*: Plan learning features and platform structure  
- *Internship (Month 1–3)*:  
    - Month 1: Learn AWS and upgrade technical knowledge  
    - Month 2: Learn deployment, plan architecture and design  
    - Month 3: Deploy, test, and launch the platform  
- *After Deployment*: Research potential development and new features for the program  

### 6. Budget Estimation  
Costs can be viewed on [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)  
Or download [budget estimation file](../attachments/budget_estimation.pdf).  

*Infrastructure Costs*  
- AWS S3: 0.15 USD/month (6 GB, 2 buckets, 2,100 requests)  
- AWS Amplify gen 2: 0.35 USD/month (256 MB, request 500 ms)  
- AWS MediaConvert: 0.05 USD/month (small video conversion)  
- AWS Route53: 0.50 USD/month (1 domain, 1 million queries)  
- AWS Cognito: 0.00 USD/month (5 users Free tier)  
- AWS Secrets Manager: 0.40 USD/month (10 secrets)  
- AWS IAM: 0 USD/month  
- AWS Lambda: 0.00 USD/month (1,000 requests, 512 MB RAM) 
- AWS WAF: 5.00 USD/month (1 Web ACL) 

*Total*: 6.45 USD/month, ~77.4 USD/year  
- *Hardware*: $265 one-time (if needed for any media devices)  

### 7. Risk Assessment  
*Risk Matrix*  
- Server downtime: High impact, medium probability  
- Budget overrun: Medium impact, high probability  

*Mitigation Strategy*  
- Cost: Use AWS Budget for alerts, optimize services  

*Contingency Plan*  
- Revert to manual data collection if AWS services fail  
- Use CloudFormation to restore configurations related to costs  

### 8. Expected Outcomes  
*Technical Improvements*: Real-time monitoring and analysis replace manual operations. Scalable to 10–15 users.  
*Long-term Value*: 1-year learning data platform for AI research, reusable for future educational projects.  
