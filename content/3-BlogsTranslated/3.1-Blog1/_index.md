---
title: "Blog 1"
date: 2025-09-16
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
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
