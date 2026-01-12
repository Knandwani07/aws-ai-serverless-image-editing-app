# 🖼️ AWS Serverless AI Image Editing Application

<img width="2752" height="1536" alt="Professional AWS Architecture Diagram" src="https://github.com/user-attachments/assets/ad0ed80c-68c6-4725-a5ba-4cc5af2508f0" />

### 📌 Project Level: Intermediate
A hands-on AWS serverless application demonstrating how to build a secure, scalable, AI-powered image editing solution using Amazon Bedrock and fully managed AWS services.

---

### 📝 Project Overview

This project focuses on implementing a serverless image editing application where users can authenticate, upload images, apply masked edits, and generate AI-based image modifications using natural language prompts.

• Frontend is hosted as a single-page application using AWS Amplify  
• User authentication is handled using Amazon Cognito  
• Backend processing is performed by AWS Lambda  
• Image generation and editing is powered by Amazon Bedrock  
• API requests are managed through Amazon API Gateway  
• Image metadata is stored in Amazon DynamoDB  

The architecture eliminates server management while ensuring scalability, security, and high availability.

---

### 🎯 Objective

• Build a fully serverless AI-based image editing application  
• Secure application access using token-based authentication  
• Integrate AI image generation using Amazon Bedrock  
• Design a scalable backend using AWS Lambda and API Gateway  
• Persist image generation metadata using DynamoDB  
• Demonstrate cloud-native application design patterns  

---

### 🧰 AWS Services Used

| AWS Service        | Purpose                                                         |
|--------------------|-----------------------------------------------------------------|
| Amazon Cognito     | Manages user authentication and authorization                  |
| AWS Lambda         | Executes backend logic for image generation and data storage   |
| Amazon Bedrock    | Provides AI foundation models for image editing                |
| Amazon DynamoDB   | Stores image generation metadata                               |
| Amazon API Gateway| Exposes secure REST APIs for frontend communication            |
| AWS Amplify       | Hosts and deploys the frontend application                     |
| AWS IAM           | Manages permissions using least-privilege access control       |
| Amazon CloudWatch | Provides logging and monitoring for backend operations         |

---

### 🧠 What This Project Teaches

• Serverless application architecture on AWS  
• Secure authentication using Amazon Cognito  
• REST API design using API Gateway and Lambda  
• AI service integration using Amazon Bedrock  
• Event-driven backend processing  
• NoSQL data modeling using DynamoDB  
• Applying IAM roles and permission boundaries  
• Building scalable applications with minimal operational overhead  

---

### 📂 Project Structure

| Directory     | Description                                              |
|--------------|----------------------------------------------------------|
| backend/     | AWS Lambda function code and IAM policies                |
| frontend/    | Client-side application hosted using AWS Amplify         |
| architecture/| Architecture diagram and design documentation            |
| docs/        | Setup, API usage, and cleanup documentation              |

---

### 🔄 Workflow Overview

• User accesses the application via AWS Amplify  
• User authenticates using Amazon Cognito  
• Cognito issues authentication tokens  
• Frontend sends authenticated requests to API Gateway  
• API Gateway validates requests using Cognito authorizer  
• API Gateway invokes AWS Lambda function  
• Lambda calls Amazon Bedrock for image generation  
• Image metadata is stored in Amazon DynamoDB  
• Edited images are returned to the frontend  
• Logs and metrics are captured in Amazon CloudWatch  

---

### 🚀 Key Features

• Fully serverless architecture  
• Secure user authentication and authorization  
• AI-powered image generation and editing  
• RESTful API-based backend  
• Persistent metadata storage  
• Automatic scaling based on demand  
• Centralized logging and monitoring  
• Cost-efficient, pay-per-use model  

---

### ⚙️ Architecture Highlights

• Eliminates server provisioning and maintenance  
• Uses managed AWS services for reliability and scalability  
• Separates frontend, backend, and AI processing layers  
• Secures APIs using Cognito authorizers  
• Designed to handle variable workloads efficiently  
• Follows cloud-native and least-privilege best practices  

---

### 🧹 Resource Cleanup

To avoid ongoing AWS charges, delete resources in the following order:

• AWS Amplify application  
• API Gateway REST API  
• DynamoDB table  
• Lambda function  
• IAM role  
• Amazon Cognito user pool  
• CloudWatch log groups  

---

### 🏁 Outcome

• Practical experience building serverless AI applications  
• Strong understanding of AWS service integration  
• Hands-on exposure to Amazon Bedrock usage  
• Improved knowledge of secure API design  
• Foundation for building production-ready AI-driven solutions  
