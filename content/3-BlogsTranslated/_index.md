---
title: "Translated Blogs"
date: 2025-09-16
weight: 7
chapter: false
pre: " <b> 3. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

This section will list and introduce the blogs you have translated. For example:

###  [Blog 1 - Getting started with healthcare data lakes: Using microservices](3.1-Blog1/)
This blog introduces how to start building a data lake in the healthcare sector by applying a microservices architecture. You will learn why data lakes are important for storing and analyzing diverse healthcare data (electronic medical records, lab test data, medical IoT devices…), how microservices help make the system more flexible, scalable, and easier to maintain. The article also guides you through the steps to set up the environment, organize the data processing pipeline, and ensure compliance with security & privacy standards such as HIPAA.

###  [Blog 2 - Simplifying Source Code Documentation with Amazon Q Developer](3.2-Blog2/)
This blog introduces how to automate source code documentation using Amazon Q Developer through the /doc agent. It explains why maintaining a README is important in the software development process, how AI analyzes the entire repository to create or update documentation, and how this tool reduces the time spent writing documentation. The content also walks through the steps to get started with /doc, demonstrates how to create a new README or update an existing one, and describes the iterative feedback process used to refine documentation. The blog further discusses strategies for managing documentation at different levels (root, component, service, API), how to handle documentation inheritance, and best practices to keep READMEs accurate and synchronized with the codebase. Overall, /doc transforms documentation from a manual and tedious task into an automated, fast, and consistent process throughout the software development lifecycle.

###  [Blog 3 - Simplifying Private API Integration with Amazon EventBridge and AWS Step Functions](3.3-Blog3/)
This blog introduces how to simplify private API integration with Amazon EventBridge and AWS Step Functions using AWS PrivateLink and Amazon VPC Lattice. It explains why directly calling private HTTPS endpoints inside a VPC improves security, reduces architectural complexity, and enhances performance compared to using proxies like Lambda or SQS. The content also describes related components such as the Resource Gateway, Resource Configuration, EventBridge Connections, and how to share these resources through AWS RAM. The blog includes an example Step Functions workflow for classifying product reviews, where the workflow can either send events to EventBridge or call a private API running in the VPC. Finally, it provides a practical deployment guide within a single AWS account, including setting up a hosted zone, certificates, configuring the Gateway, and establishing connections to private endpoints.

