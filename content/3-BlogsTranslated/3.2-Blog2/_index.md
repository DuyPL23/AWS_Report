---
title: "Blog 2"
<<<<<<< HEAD
date: 2025-09-18
weight: 2
chapter: false
pre: " <b> 3.3. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy it verbatim** for your report, including this warning.
{{% /notice %}}

# Simplifying Source Code Documentation with Amazon Q Developer

By Jehu Gray, Joyce Muya, Adeogo Olajide, Abiola Olanrewaju, and Damola Oluyemo | April 11, 2005

## Introduction

In fast-paced software development, maintaining detailed documentation often takes a back seat to feature development priorities. Amazon Q Developer’s `/doc` agent changes this by automating README creation and updates. This tool significantly reduces documentation time, ensuring feature development is uninterrupted.

## How Amazon Q Developer Generates Documentation Automatically

The `/doc` agent leverages **Generative AI** to analyze the entire codebase and automatically produce detailed documentation. It respects `.gitignore` files, excluding unnecessary files from documentation generation.

## Solution Overview

Example: A cloud infrastructure team working on an **AWS DataSync** project. When the product manager requested detailed documentation, the team used `/doc` to automatically create a README instead of manually writing it.

## Getting Started with `/doc`

Basic steps:  

1. **Install Amazon Q** following the guide  
2. Open an IDE with the Amazon Q extension  
3. Click the Amazon Q icon to open the chat panel  
4. Enter `/doc` to start the documentation workflow  
5. Select the documentation task:
   - Create a new README  
   - Update an existing README

### Example: Creating a New README

- Select “Create a README”  
- Confirm the directory, select “Yes”  
- The agent scans the codebase, summarizes content, and creates the README  
- Preview the file and choose to accept or edit before applying

### Example: Updating an Existing README

- Select “Update an existing README”  
- Describe the changes to apply  
- The agent suggests updates based on recent code changes  
- Confirm the updates by selecting “Yes”

## Advanced Documentation Management

The `/doc` agent supports iterative feedback loops:

- Review content to identify missing sections  
- Provide specific feedback to refine documentation  
- Request additional detailed explanations  
- Build complete documentation over multiple update cycles

### Component-Level Documentation

- **Root-level README**: Project overview  
- **Component-level README**: Module-specific details  
- **Service-level docs**: Microservices  
- **API docs**: Interface and endpoint explanations  

### Handling Documentation Inheritance

- Create base documentation for the parent project  
- Generate documentation for extensions  
- Cross-reference related documents  
- Update specific sections when inheritance patterns change

### Documentation Sync Strategy

- Schedule updates according to sprint cycles  
- Include documentation review in the **code review** process  
- Use `/doc` to generate change summaries  
- Verify that documentation accurately reflects code changes

## Best Practices for Using `/doc`

1. **Optimize repositories**: Generate documentation for the full codebase or selected sections  
2. **Maintain code quality**: Clear comments, meaningful variable/function names, follow coding conventions  
3. **Provide clear instructions for updates**: Use Update an existing README and Make a specific change  
4. **Compose effective change descriptions**: Include sections to edit, content to add/remove, issues to address  
5. **Understand system limitations**: `/doc` cannot access internal platforms or specialized software; manual edits may be required

### Quotas and Limits

- Limited number of feedback iterations per session  
- Files/directories in `.gitignore` are automatically excluded

## Conclusion

Amazon Q Developer’s `/doc` transforms documentation from a tedious task into an automated, efficient process. README files remain accurate and up-to-date without consuming valuable development time. `/doc` can be easily integrated into development workflows.

## Author Profiles

### Jehu Gray
Prototyping Architect at AWS, exploring Infrastructure as Code (IaC) capabilities.

### Abiola Olanrewaju
Solutions Architect at AWS, supporting GovTech, Data Analytics, Security, and Generative AI.

### Adeogo Olajide
Solutions Architect at AWS, assisting GovTech and public sector organizations, specializing in secure, scalable, compliant architecture.

### Joyce Muya
Solutions Architect at AWS, supporting media & entertainment enterprises, focusing on Analytics and AI/ML workloads.

### Damola Oluyemo
Solutions Architect at AWS, helping enterprise customers design cloud solutions and explore IaC and Generative AI.
=======
date: 2025-09-16
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Getting Started with Healthcare Data Lakes: Using Microservices

Data lakes can help hospitals and healthcare facilities turn data into business insights, maintain business continuity, and protect patient privacy. A **data lake** is a centralized, managed, and secure repository to store all your data, both in its raw and processed forms for analysis. Data lakes allow you to break down data silos and combine different types of analytics to gain insights and make better business decisions.

This blog post is part of a larger series on getting started with setting up a healthcare data lake. In my final post of the series, *“Getting Started with Healthcare Data Lakes: Diving into Amazon Cognito”*, I focused on the specifics of using Amazon Cognito and Attribute Based Access Control (ABAC) to authenticate and authorize users in the healthcare data lake solution. In this blog, I detail how the solution evolved at a foundational level, including the design decisions I made and the additional features used. You can access the code samples for the solution in this Git repo for reference.

---

## Architecture Guidance

The main change since the last presentation of the overall architecture is the decomposition of a single service into a set of smaller services to improve maintainability and flexibility. Integrating a large volume of diverse healthcare data often requires specialized connectors for each format; by keeping them encapsulated separately as microservices, we can add, remove, and modify each connector without affecting the others. The microservices are loosely coupled via publish/subscribe messaging centered in what I call the “pub/sub hub.”

This solution represents what I would consider another reasonable sprint iteration from my last post. The scope is still limited to the ingestion and basic parsing of **HL7v2 messages** formatted in **Encoding Rules 7 (ER7)** through a REST interface.

**The solution architecture is now as follows:**

> *Figure 1. Overall architecture; colored boxes represent distinct services.*

---

While the term *microservices* has some inherent ambiguity, certain traits are common:  
- Small, autonomous, loosely coupled  
- Reusable, communicating through well-defined interfaces  
- Specialized to do one thing well  
- Often implemented in an **event-driven architecture**

When determining where to draw boundaries between microservices, consider:  
- **Intrinsic**: technology used, performance, reliability, scalability  
- **Extrinsic**: dependent functionality, rate of change, reusability  
- **Human**: team ownership, managing *cognitive load*

---

## Technology Choices and Communication Scope

| Communication scope                       | Technologies / patterns to consider                                                        |
| ----------------------------------------- | ------------------------------------------------------------------------------------------ |
| Within a single microservice              | Amazon Simple Queue Service (Amazon SQS), AWS Step Functions                               |
| Between microservices in a single service | AWS CloudFormation cross-stack references, Amazon Simple Notification Service (Amazon SNS) |
| Between services                          | Amazon EventBridge, AWS Cloud Map, Amazon API Gateway                                      |

---

## The Pub/Sub Hub

Using a **hub-and-spoke** architecture (or message broker) works well with a small number of tightly related microservices.  
- Each microservice depends only on the *hub*  
- Inter-microservice connections are limited to the contents of the published message  
- Reduces the number of synchronous calls since pub/sub is a one-way asynchronous *push*

Drawback: **coordination and monitoring** are needed to avoid microservices processing the wrong message.

---

## Core Microservice

Provides foundational data and communication layer, including:  
- **Amazon S3** bucket for data  
- **Amazon DynamoDB** for data catalog  
- **AWS Lambda** to write messages into the data lake and catalog  
- **Amazon SNS** topic as the *hub*  
- **Amazon S3** bucket for artifacts such as Lambda code

> Only allow indirect write access to the data lake through a Lambda function → ensures consistency.

---

## Front Door Microservice

- Provides an API Gateway for external REST interaction  
- Authentication & authorization based on **OIDC** via **Amazon Cognito**  
- Self-managed *deduplication* mechanism using DynamoDB instead of SNS FIFO because:  
  1. SNS deduplication TTL is only 5 minutes  
  2. SNS FIFO requires SQS FIFO  
  3. Ability to proactively notify the sender that the message is a duplicate  

---

## Staging ER7 Microservice

- Lambda “trigger” subscribed to the pub/sub hub, filtering messages by attribute  
- Step Functions Express Workflow to convert ER7 → JSON  
- Two Lambdas:  
  1. Fix ER7 formatting (newline, carriage return)  
  2. Parsing logic  
- Result or error is pushed back into the pub/sub hub  

---

## New Features in the Solution

### 1. AWS CloudFormation Cross-Stack References
Example *outputs* in the core microservice:
```yaml
Outputs:
  Bucket:
    Value: !Ref Bucket
    Export:
      Name: !Sub ${AWS::StackName}-Bucket
  ArtifactBucket:
    Value: !Ref ArtifactBucket
    Export:
      Name: !Sub ${AWS::StackName}-ArtifactBucket
  Topic:
    Value: !Ref Topic
    Export:
      Name: !Sub ${AWS::StackName}-Topic
  Catalog:
    Value: !Ref Catalog
    Export:
      Name: !Sub ${AWS::StackName}-Catalog
  CatalogArn:
    Value: !GetAtt Catalog.Arn
    Export:
      Name: !Sub ${AWS::StackName}-CatalogArn
>>>>>>> b7de5673aac2db44e5dd308db089903344ed1d89
