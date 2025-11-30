# ☁️ Cloud Resume Challenge - Ken Chen

![Build Status](https://img.shields.io/github/actions/workflow/status/kchenfs/cloud-resume/build-deploy.yml?style=flat-square&logo=github-actions)
![Terraform](https://img.shields.io/badge/Terraform-v1.9+-purple?style=flat-square&logo=terraform)
![AWS](https://img.shields.io/badge/AWS-Serverless-orange?style=flat-square&logo=amazon-aws)

> **Live Site:** [kchenfs.com](https://kchenfs.com)

This repository contains the source code and Infrastructure-as-Code (IaC) for my personal resume website. Built as part of the **Cloud Resume Challenge**, this project demonstrates a full-stack serverless application deployed via a CI/CD pipeline.

---

## 🏗️ Architecture

This project leverages a modern **Serverless Architecture** on AWS to ensure high availability, zero server management, and cost efficiency.



[Image of AWS serverless architecture diagram with Lambda and API Gateway]


### Data Flow
1.  **Client:** User visits `kchenfs.com`.
2.  **CDN & Caching:** **Amazon CloudFront** serves the static content from edge locations globally, enforcing HTTPS.
3.  **Frontend:** Static assets (HTML, CSS, JS) are hosted in an **Amazon S3** bucket.
4.  **API Call:** The JavaScript on the frontend calls an **API Gateway** endpoint to fetch visitor stats.
5.  **Compute:** API Gateway triggers an **AWS Lambda** function (Python).
6.  **Persistence:** Lambda reads/writes the atomic counter to **Amazon DynamoDB**.

---

## 🛠️ Technology Stack

| Category | Technology | Usage |
|----------|------------|-------|
| **Frontend** | HTML5, Tailwind CSS, JS | Responsive UI and dynamic API integration. |
| **Compute** | AWS Lambda (Python) | Serverless backend logic for the visitor counter. |
| **Database** | Amazon DynamoDB | NoSQL database for state management. |
| **Networking** | CloudFront, API Gateway, Route53 | CDN, API management, and DNS. |
| **IaC** | Terraform | Declarative infrastructure provisioning. |
| **CI/CD** | GitHub Actions | Automated testing and deployment pipeline. |

---
