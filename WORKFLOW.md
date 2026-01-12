# 🔄 SERVERLESS AI IMAGE EDITING APPLICATION – WORKFLOW DOCUMENTATION

### Application Overview:
User Login → Cognito Auth → API Request → API Gateway → Lambda → Bedrock → DynamoDB → Response → CloudWatch Logs



## SECTION 1: WORKFLOW VISUALIZATION


    👤 User Accesses Web Application (AWS Amplify)
            │
            ▼
    🔐 User Authenticates via Amazon Cognito
            │
            ▼
    🎟️ Cognito Issues Access Token
            │
            ▼
    🌐 Authenticated Request Sent to API Gateway
            │
            ▼
    🛡️ API Gateway Validates Cognito Token
            │
            ▼
    ⚡ AWS Lambda Function Invoked
            │
            ▼
    🧠 Amazon Bedrock Image Generation Request
            │
            ▼
    🖼️ AI Model Processes Image & Prompt
            │
            ▼
    💾 Metadata Stored in DynamoDB
            │
            ▼
    📤 Edited Image Returned to Frontend
            │
            ▼
    📝 CloudWatch Logs Recorded

------------------------------------------------------------

## SECTION 2: DETAILED WORKFLOW BREAKDOWN

| Step | AWS Service           | Description                                                                 |
|------|-----------------------|-----------------------------------------------------------------------------|
| 1    | AWS Amplify           | User accesses the hosted frontend application.                              |
| 2    | Amazon Cognito        | User logs in using valid credentials.                                       |
| 3    | Amazon Cognito        | Cognito issues JWT access and ID tokens.                                    |
| 4    | Frontend Application | Authenticated request is sent to API Gateway with token.                    |
| 5    | Amazon API Gateway    | Validates the Cognito token using an authorizer.                            |
| 6    | Amazon API Gateway    | Routes the request to the configured Lambda function.                       |
| 7    | AWS Lambda            | Parses request payload (image, mask, prompt).                               |
| 8    | AWS Lambda            | Invokes Amazon Bedrock image generation model.                              |
| 9    | Amazon Bedrock        | Processes the image and text prompt to generate edited output.              |
| 10   | AWS Lambda            | Receives AI-generated image response.                                       |
| 11   | Amazon DynamoDB       | Stores image metadata (request ID, timestamp, user reference).              |
| 12   | AWS Lambda            | Returns the generated image to API Gateway.                                 |
| 13   | Amazon API Gateway    | Sends response back to the frontend.                                        |
| 14   | Amazon CloudWatch     | Logs execution details and metrics for monitoring.                          |

------------------------------------------------------------

## SECTION 3: APPLICATION CHARACTERISTICS

### ✅ KEY FEATURES
   
   #### Secure Authentication  
   Token-based access using Amazon Cognito ensures only authenticated users can invoke APIs.
   
   #### Serverless Architecture  
   Fully managed services eliminate server provisioning and infrastructure maintenance.
   
   #### AI-Powered Processing  
   Image editing and generation is handled using Amazon Bedrock foundation models.
   
   #### Scalable Backend  
   AWS Lambda and API Gateway automatically scale based on request volume.
   
   #### Persistent Metadata Storage  
   DynamoDB stores image generation details for tracking and auditing.
   
   #### Centralized Logging  
   CloudWatch captures logs and metrics for observability and troubleshooting.
   
   #### Cost-Efficient  
   Pay-per-use pricing ensures no cost for idle resources.

------------------------------------------------------------

## SECTION 4: DATA & RESOURCE STRUCTURE

#### 📁 DynamoDB Table Organization:

##### ImageGenerationTable
- id (Partition Key)
- user_id
- request_timestamp
- prompt
- image_reference
- status

#### 📁 CloudWatch Log Groups:

- /aws/lambda/ImageEditBackend
- /aws/apigateway/ImageEditingAppBackendAPI

------------------------------------------------------------

## SECTION 5: ERROR HANDLING & MONITORING

#### 🔍 MONITORING STRATEGY:

##### 1. CloudWatch Metrics:
   - Lambda invocation count
   - Lambda execution duration
   - Lambda error rates
   - API Gateway 4XX and 5XX errors
   - Bedrock request latency

##### 2. CloudWatch Alarms:
   - Lambda error threshold exceeded
   - Lambda timeout warnings
   - API Gateway elevated error rates

##### 3. Logging:
   - Request and response metadata logging
   - Error stack traces for failed executions
   - Authorization failure logs

------------------------------------------------------------

## SECTION 6: PERFORMANCE & SECURITY CONSIDERATIONS

### ⚙️ BEST PRACTICES:

##### 1. API Gateway:
   - Enable request validation
   - Use Cognito authorizers for all protected endpoints
   - Configure CORS explicitly

##### 2. Lambda Function:
   - Set appropriate timeout for Bedrock calls
   - Grant least-privilege IAM permissions
   - Use structured logging for observability

##### 3. Amazon Bedrock:
   - Validate prompt inputs
   - Handle model response errors gracefully
   - Monitor usage to control costs

##### 4. DynamoDB:
   - Use on-demand capacity for variable workloads
   - Store only metadata, not large binary objects

------------------------------------------------------------

## 💰 COST MANAGEMENT

Service          | Cost Factor                | Optimization Strategy
-----------------|----------------------------|-----------------------------------
AWS Amplify      | Build & hosting             | Optimize build frequency
API Gateway      | API requests                | Reduce unnecessary calls
Lambda           | Invocations & duration      | Efficient code and timeouts
Amazon Bedrock   | Model inference requests    | Prompt optimization
DynamoDB         | Read/write operations       | On-demand capacity mode
CloudWatch       | Logs and metrics storage    | Set log retention policies

------------------------------------------------------------
## END OF DOCUMENTATION
