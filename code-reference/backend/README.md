# 🧠 Backend – AWS Lambda (Image Editing Service)

This directory contains the backend implementation for the AWS Serverless AI Image Editing Application. The backend is implemented as an AWS Lambda function that processes authenticated image editing requests, invokes Amazon Bedrock for AI-powered image generation, and logs execution metadata to Amazon DynamoDB.

---

## `📂 File Overview`

### lambda_function.py

The main AWS Lambda function responsible for handling image editing requests and coordinating all backend operations.

---

## Purpose

- Act as the backend API handler for image editing requests.
- Invoke Amazon Bedrock image generation models.
- Process Base64-encoded images and masks.
- Store request metadata and execution details in Amazon DynamoDB.
- Return AI-generated images and request identifiers to the client.

---

## Key Responsibilities

- Parse and validate incoming requests from Amazon API Gateway.
- Support image inpainting and outpainting modes.
- Prepare and submit inference requests to Amazon Bedrock.
- Measure model inference execution time and output size.
- Persist execution logs and request metadata in DynamoDB.
- Handle error scenarios gracefully and return meaningful responses.
- Emit structured logs to Amazon CloudWatch for observability.

---

## AWS Services Used

- **Amazon Bedrock** – AI image generation using foundation models
- **AWS Lambda** – Serverless compute for backend logic
- **Amazon DynamoDB** – Storage for request and execution metadata
- **Amazon API Gateway** – REST API entry point
- **Amazon CloudWatch** – Logging and monitoring
- **AWS IAM** – Access control using least-privilege permissions

---

## Configuration

### Environment Variables

| Variable Name | Description |
|--------------|------------|
| DYNAMODB_TABLE_NAME | DynamoDB table name for logging requests (default: ImageGenerationTable) |

---

## Supported Model

- amazon.titan-image-generator-v2

---

## Request Handling Notes

- Requests must be authenticated using Amazon Cognito (via API Gateway authorizer).
- Image and mask inputs must be Base64-encoded.
- The function is designed to be stateless and horizontally scalable.
- CORS headers are included to support browser-based clients.

---

## Runtime & Deployment

- **Runtime**: Python 3.13
- **Recommended timeout**: ≥ 60 seconds
- **Deployment target**: AWS Lambda behind API Gateway

Ensure the Lambda execution role includes permissions for:
- **bedrock**:InvokeModel
- **dynamodb**:PutItem
- **logs**:CreateLogGroup, CreateLogStream, PutLogEvents

---

## Summary

This backend Lambda function serves as the core processing layer of the application, enabling secure, scalable, and observable AI-powered image editing using AWS managed services and serverless architecture.

