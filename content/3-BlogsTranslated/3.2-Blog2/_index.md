---
title: "Blog 2"
date: 2025-09-18
weight: 2
chapter: false
pre: " <b> 3.3. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
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
