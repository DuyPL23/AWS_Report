---
title: "Blog 3"
<<<<<<< HEAD
date: 2025-03-27
weight: 3
chapter: false
pre: " <b> 3.4. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy it verbatim** for your report, including this warning.
{{% /notice %}}

# Simplifying Private API Integration with Amazon EventBridge and AWS Step Functions

By Eric Johnson | March 27, 2025

This article was written by Pawan Puthran (Principal Specialist TAM – Serverless) and Vamsi Vikash Ankam (Senior Serverless Solutions Architect – Serverless).

## Introduction

In December 2024, AWS announced that Amazon EventBridge and AWS Step Functions support integration with **private APIs** via **AWS PrivateLink** and **Amazon VPC Lattice**. This feature:

- Enables seamless integration between private networks, on-premises infrastructure, and the cloud  
- Simplifies operations  
- Ensures secure, controlled communication between services inside a VPC  

This article guides how to integrate Step Functions with private APIs to enable efficient and secure private network interactions.

## Overview

Previously, EventBridge and Step Functions required proxies (AWS Lambda, SQS) to send events to HTTPS applications in a VPC. Now, you can call **private HTTPS endpoints** directly within your VPC.

### Benefits

1. **Security and compliance**: Keep APIs private, reduce Internet exposure, meet industry regulations such as finance and healthcare.  
2. **Simplified architecture**: Remove proxies and complex network setup, allowing developers to focus on core logic.  
3. **Performance and reliability**: Direct connection over AWS backbone network, faster, fewer errors, reduced dependency on external networks.

## Architectural Components

- **Resource Gateway**: Secure entry point for data to resources in the VPC.  
- **Resource Configuration**: Defines resources and access permissions.  
- **EventBridge Connections**: Connect to private HTTPS endpoints using resource configuration.  
- **AWS Resource Access Manager (RAM)**: Safely share resource configurations across accounts.

## Workload Overview

Example Step Functions workflow for classifying product reviews:

- Calls **Amazon Nova Micro** via Amazon Bedrock to classify reviews.  
- If review is fake → sends event to EventBridge bus  
- If review is genuine → calls **private HTTPS endpoint** inside VPC (hosted on AWS Fargate, behind internal ALB)

### Figure 1: Step Functions workflow calling a private HTTPS endpoint

The workflow analyzes text, user behavior, and linguistic signals to determine review authenticity. Suspicious reviews are automatically flagged via a custom workflow.

## Example Deployment

1. Create a **Route 53 public hosted zone** (e.g., api.com) and ACM certificate.  
2. Use the sample application with deployment guide.  

### Scenario 1: Single Account

- Step Functions, EventBridge Connections, and private resources are in the same account.  
- **Resource Gateway**: Entry point for private resources, spanning multiple subnets for HA.  
- **Resource Configurations**: Setup connection from private endpoint → Gateway.  
- **EventBridge Connection**: Allows Step Functions to connect to private API.

Example Step Functions test payload:

```json
{
  "items": [
    {
      "asin": "B000FA64PA",
      "helpful": [0, 0],
      "overall": 5,
      "reviewText": "Darth Maul working under cloak of darkness...",
      "reviewTime": "10 11, 2013",
      "unixReviewTime": 1381449600
    },
    {
      "asin": "B000F83SZQ",
      "helpful": [1, 1],
      "overall": 4,
      "reviewText": "Never heard of Amy Brewster...",
      "reviewTime": "03 22, 2014",
      "unixReviewTime": 1395446400
    }
  ]
}
=======
date: 2025-09-16
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
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
