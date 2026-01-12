# 🛠️ Execution Guide: AWS Serverless AI Image Editing Application Using Amazon Bedrock


## 📘 Introduction

This execution guide provides step-by-step instructions to deploy and run a serverless AI-powered image editing application using AWS managed services.

The application allows authenticated users to upload images, apply masked edits, and generate AI-based image modifications using Amazon Bedrock foundation models. Secure access is enforced through Amazon Cognito, while backend processing is handled using AWS Lambda and API Gateway. Image metadata is stored in Amazon DynamoDB, and the frontend is hosted using AWS Amplify.

The solution is fully serverless, scalable, and requires no infrastructure management.

---

## 🏗️ Architecture Overview

The architecture follows a secure, cloud-native, serverless design where AWS managed services interact through authenticated API requests.

---

### 1. **AWS Amplify**

Hosts the frontend application.

- Serves the single-page web application
- Handles build and deployment of frontend assets
- Provides HTTPS endpoints with managed SSL
- Integrates with backend APIs
- Supports scalable global content delivery


### 2. **Amazon Cognito**

Manages user authentication and authorization.

- Provides user pools for identity management
- Handles user login and password policies
- Issues JWT access and ID tokens
- Integrates with API Gateway for request authorization
- Prevents unauthorized access to backend APIs


### 3. **Amazon API Gateway**

Acts as the secure entry point for backend services.

- Exposes REST APIs to the frontend
- Validates Cognito-issued tokens
- Enforces CORS policies
- Routes requests to AWS Lambda
- Supports request throttling and monitoring


### 4. **AWS Lambda**

Executes backend processing logic.

- Processes image upload and edit requests
- Invokes Amazon Bedrock for image generation
- Stores metadata in DynamoDB
- Returns AI-generated results to API Gateway
- Logs execution details to CloudWatch
- Scales automatically with demand


### 5. **Amazon Bedrock**

Provides AI-powered image generation capabilities.

- Uses foundation models for image editing
- Accepts image and text prompt inputs
- Generates edited images based on masked regions
- Handles inference without model management
- Integrates securely via IAM permissions


### 6. **Amazon DynamoDB**

Stores application metadata.

- Stores image generation request details
- Tracks user requests and timestamps
- Provides low-latency access
- Scales automatically based on traffic
- Eliminates database administration


### 7. **Amazon CloudWatch**

Provides centralized logging and monitoring.

- Captures Lambda execution logs
- Tracks API Gateway metrics
- Enables troubleshooting and auditing
- Supports alarms and log retention policies


### 8. **AWS IAM**

Ensures secure access between services.

- Manages role-based permissions
- Enforces least-privilege access
- Controls Lambda access to Bedrock and DynamoDB
- Secures service-to-service interactions

---

## 🎯 Why This Project?

This project demonstrates a real-world serverless AI application using AWS managed services.

- Showcases secure API-based application design
- Demonstrates AI integration using Amazon Bedrock
- Eliminates server provisioning and maintenance
- Provides scalable and cost-efficient architecture
- Suitable for production-style cloud applications

---

## ✨ Key Features

- Fully serverless architecture
- Secure user authentication
- AI-powered image editing
- REST-based backend APIs
- Automatic scaling and high availability
- Centralized logging and monitoring
- Pay-per-use cost model

---

## 🛠️ Execution Workflow

---

## I. Amazon Cognito User Pool Setup

1. Log in to the AWS Management Console  
2. Navigate to **Amazon Cognito**
3. Select **User Pools**
4. Click **Create user pool**

**Configuration:**
- Application type: Single-Page Application (SPA)
- User pool name: `ImageEditUserPool`
- Sign-in options: Email and Username
- Disable self-sign-up
- Required attribute: Email

5. Create the user pool
6. Save the **User Pool ID** and **Client ID**
7. Create a test user under **Users**
8. Set a temporary password for first-time login

---

## II. IAM Role Creation for Lambda

1. Navigate to **IAM Console**
2. Click **Create role**
3. Select **AWS service**
4. Use case: **Lambda**

**Attach Policies:**
- `AWSLambdaBasicExecutionRole`
- `AmazonBedrockFullAccess`
- `AmazonDynamoDBFullAccess`

**Role Name:**
- `bedrock-image-editing-role`

5. Create the role

---

## III. AWS Lambda Function Setup

1. Navigate to **AWS Lambda**
2. Click **Create function**

**Basic Configuration:**
- Function name: `ImageEditBackend`
- Runtime: Python 3.13
- Execution role: Use existing role
- Select `bedrock-image-editing-role`

3. Create the function

### Lambda Configuration
- Timeout: 60 seconds
- Memory: Default (adjust if needed)

4. Deploy the backend code
5. Verify successful deployment

---

## IV. DynamoDB Table Creation

1. Navigate to **Amazon DynamoDB**
2. Click **Create table**

**Table Configuration:**
- Table name: `ImageGenerationTable`
- Partition key: `id` (String)
- Capacity mode: On-demand

3. Create the table
4. Wait for table status to become **Active**

---

## V. API Gateway Configuration

1. Navigate to **Amazon API Gateway**
2. Click **Create API**
3. Select **REST API**
4. Create a new API

**Configuration:**
- API name: `ImageEditingAppBackendAPI`
- Endpoint type: Regional

5. Create a **POST** method
6. Integration type: Lambda
7. Enable Lambda proxy integration
8. Select `ImageEditBackend` function

---

## VI. Cognito Authorizer Setup

1. In API Gateway, go to **Authorizers**
2. Click **Create authorizer**

**Configuration:**
- Name: `cognito-authorizer`
- Type: Cognito
- User pool: `ImageEditUserPool`
- Token source: Authorization

3. Attach the authorizer to the POST method

---

## VII. CORS Configuration

1. Select the API resource
2. Click **Enable CORS**
3. Allow methods:
   - OPTIONS
   - POST
4. Allow headers:
   - Content-Type
   - Authorization
   - Access-Control-Allow-Origin
   - Access-Control-Allow-Headers

5. Save changes

---

## VIII. API Deployment

1. Click **Deploy API**
2. Create a new stage:
   - Stage name: `prod`
3. Deploy the API
4. Copy the **Invoke URL**

---

## IX. Frontend Configuration

1. Open `config.js`
2. Update values:
   - `userPoolId`
   - `userPoolClientId`
   - `region`
   - `invokeUrl`

3. Save changes

---

## X. AWS Amplify Deployment

1. Compress frontend files into a ZIP archive
2. Navigate to **AWS Amplify**
3. Click **Deploy an app**
4. Select **Deploy without Git**
5. Upload ZIP file
6. Deploy application
7. Access the provided Amplify URL

---

## XI. Application Testing

1. Open the Amplify application URL
2. Log in using Cognito user credentials
3. Change password on first login
4. Upload an image
5. Apply mask to desired region
6. Enter image edit prompt
7. Submit request
8. Wait for processing
9. View generated images

---

## XII. Resource Cleanup

Delete resources in the following order to avoid charges:

1. AWS Amplify application
2. API Gateway API
3. DynamoDB table
4. Lambda function
5. IAM role
6. Amazon Cognito user pool
7. CloudWatch log groups

---

## ✅ Conclusion

This execution guide demonstrates the complete deployment of a secure, serverless AI image editing application using AWS managed services. By integrating Amazon Cognito, API Gateway, AWS Lambda, Amazon Bedrock, DynamoDB, and AWS Amplify, the solution achieves scalability, security, and operational simplicity, making it suitable for both learning and production use cases.
