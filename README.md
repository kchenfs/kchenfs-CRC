Cloud Resume Challenge - Ken Chen
This repository contains the source code and infrastructure-as-code for my personal resume website, built as part of the Cloud Resume Challenge. The website is a static single-page application hosted on AWS, featuring a serverless backend to track page visitors. The entire infrastructure is defined using Terraform and deployed automatically via a CI/CD pipeline with GitHub Actions.

Live Site: kchenfs.com 

Architecture Diagram
The project follows a modern serverless architecture, ensuring high availability, scalability, and cost-efficiency.

Frontend Hosting: The static website (HTML, CSS, JS) is hosted in an Amazon S3 bucket, configured for public website hosting.

Content Delivery & Security: An Amazon CloudFront distribution sits in front of the S3 bucket. This acts as a Content Delivery Network (CDN) to cache the site at edge locations globally for low-latency access and provides HTTPS security.

Backend API: The visitor counter functionality is exposed through an Amazon API Gateway REST API.

Serverless Compute: The API Gateway triggers an AWS Lambda function written in Python.

Database: The Lambda function reads and increments a counter value stored in an Amazon DynamoDB table, a NoSQL database.

CI/CD: The entire deployment process is automated using GitHub Actions. When code is pushed to the main branch, the workflow automatically deploys the frontend files to S3 and the backend code to Lambda.

Technology Stack
Frontend
HTML5

Tailwind CSS: For modern and responsive styling.

JavaScript: To handle the dynamic visitor counter API call.

Backend (Serverless)
AWS Lambda: Executes the Python code for the visitor counter logic.

Amazon API Gateway: Provides the HTTP endpoint for the Lambda function.

Amazon DynamoDB: A NoSQL database used to store and manage the visitor count.

Cloud Infrastructure & Hosting
Amazon S3 (Simple Storage Service): Stores the static website files.

Amazon CloudFront: Serves as the CDN for fast content delivery and SSL/TLS encryption.

AWS IAM (Identity and Access Management): Manages permissions for AWS services to interact securely.

Infrastructure as Code (IaC) & DevOps
Terraform: Defines and provisions all AWS resources in a declarative, version-controlled manner.

GitHub Actions: Automates the build and deployment process (CI/CD).

CI/CD Pipeline (build-deploy.yml)
The deployment process is fully automated using GitHub Actions. A push to the main branch triggers the following workflow:

Checkout Code: The repository code is checked out.

Configure AWS Credentials: Securely authenticates with AWS using secrets stored in GitHub.

Deploy Frontend: The workflow syncs the local website files (HTML, CSS, JS) with the S3 bucket.

Deploy Backend: The Python script for the visitor counter is zipped and deployed to the AWS Lambda function.

Invalidate CloudFront Cache: A cache invalidation is created in CloudFront to ensure users immediately see the latest version of the website.
