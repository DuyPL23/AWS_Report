---
title: "Blog 1"
date: 2025-09-16
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
<<<<<<< HEAD

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy it verbatim** for your report, including this warning.
{{% /notice %}}

# Shorthills AI Collaborates with AWS and Leverages DataStax to Transform Enterprise Data Search

By Ganesh Sawhney | June 13, 2025

## Introduction

Extracting value from unstructured data remains a challenge for organizations. They struggle to derive insights from emails, reports, legal documents, and other digital assets, leading to delayed decision-making. According to IDC's 2023 study, 90% of enterprise-generated data is unstructured, while only 10% is structured.

Organizations require advanced solutions such as **vector search** and **graph indexing** to transform petabytes of unstructured data into actionable insights. Customers also need capabilities like automatic summarization and contextualized responses based on organizational data.

This article explains how the collaboration between Shorthills AI, AWS, and DataStax's Astra DB applies advanced search technologies and natural language processing (NLP) for enterprise search. The solution helps customers make data-driven business decisions by leveraging AWS enterprise-grade security and DataStax’s high-performance **vector search** capabilities.

## Business Needs and Opportunities

Industries such as legal, e-commerce, healthcare, and financial services rely heavily on data for strategic decisions and customer engagement optimization. This data includes legal rulings, reviews, invoices in PDF, and other documents. Advanced techniques like vector search and graph indexing are essential to process these datasets.

Shorthills AI has developed a domain-optimized chatbot based on the **RAG (Retrieval-Augmented Generation)** framework and **knowledge graph** to deliver AI-powered insights. The solution helps lawyers, legal consultants, doctors, healthcare specialists, and e-commerce product managers gain competitive advantages through data-driven decisions.

With organizations accelerating digital transformation, the demand for flexible, secure, and scalable AI solutions has become essential. By collaborating with AWS and DataStax, Shorthills AI offers a robust solution that reduces search time by up to 70% compared to traditional methods.

## Solution Overview

Shorthills AI transitioned from open-source solutions to **Astra DB on AWS**, enabling AI-powered search capabilities and real-time insights. The solution standardizes unstructured data through parsing and chunking, then applies advanced NLP, vector search, and graph algorithms such as **Degree Centrality** and **Article Rank**.

This approach allows metadata extraction, relationship discovery, and insight generation from data stored in a data lake. Organizations can quickly access actionable information on legal rulings, customer sentiment, and market trends.

### Key Features

- **Industry-specific customization**: Legal, healthcare, e-commerce, etc.  
- **Optimized data processing**: Efficient chunking for large datasets  
- **Advanced understanding**: Graph-based indexing captures complex relationships  
- **Real-time adaptation**: Incremental updates in OptimizeRAG for new data

### Performance Comparison

| Model        | Comprehensiveness | Diversity | Empowerment | Overall |
| ------------ | ---------------- | --------- | ----------- | ------- |
| NaiveRAG     | 19.05%           | 10.98%    | 17.59%      | 17.46%  |
| OptimizeRAG  | 80.95%           | 89.02%    | 82.41%      | 82.54%  |

### Core Benefits

- **Improved search accuracy**: Combines multiple models, graph building, and vector search  
- **Reduced management costs**: 50% TCO reduction with Astra DB on AWS  
- **Data security**: AWS KMS, Amazon VPC endpoints, production-ready vector search

## Architecture

- Data ingested into **Amazon S3**  
- **Amazon Textract** extracts text and data  
- Lambda functions split (chunk) the text  
- LLMs (Amazon Bedrock) process entities and relationships  
- Embeddings stored in **Astra DB**  
- **AWS Step Functions** orchestrates the workflow

### Steps:

1. **Data storage**: S3 bucket + EventBridge + CSV validation  
2. **Chunking and entity-relationship extraction**: Amazon Bedrock  
3. **Embedding creation and storage**: Neptune for entity-relationship, Astra DB for vector embeddings

## Conclusion

By leveraging **DataStax Astra DB vector search** and AWS security features, Shorthills AI delivers a scalable, compliant, and high-performance enterprise search solution.

## Call to Action

Contact the Shorthills AI team or explore the **AWS Startup Showcase** and the **DataStax marketplace listing on AWS**.
=======
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
