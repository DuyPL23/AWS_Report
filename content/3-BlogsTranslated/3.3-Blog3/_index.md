---
title: "Blog 3"
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
