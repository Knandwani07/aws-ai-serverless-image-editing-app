# 💻 Code Reference

This directory contains the source code for the AWS Serverless AI Image Editing Application using Amazon Bedrock.

The codebase is divided into backend and frontend components. The backend is implemented as an AWS Lambda function that integrates with Amazon Bedrock and DynamoDB, while the frontend is a browser-based application that handles user authentication, image masking, and API interactions.

---

## 📄 Backend Code Overview

### `📂lambda_function.py`

This file contains the AWS Lambda function responsible for handling authenticated image editing requests and invoking Amazon Bedrock for AI-powered image generation.

**🎯 Purpose:**
- Serve as the backend API handler for image editing requests.
- Invoke Amazon Bedrock image generation models.
- Store request metadata and execution details in Amazon DynamoDB.
- Return AI-generated images to the frontend application.

**🛠️ Key Responsibilities:**
- Parse and validate incoming API Gateway requests.
- Handle Base64-encoded images and mask data.
- Support inpainting and outpainting modes.
- Construct and send inference requests to Amazon Bedrock.
- Measure inference execution time and output size.
- Persist request metadata and execution status in DynamoDB.
- Return generated images and request identifiers to the client.
- Log all execution details to Amazon CloudWatch.

**📌 Notes:**
- The function uses the amazon.titan-image-generator-v2 model.
- DynamoDB table name is configurable via environment variables.
- Implements CORS headers for browser-based access.
- Designed to run statelessly in a serverless environment.

---

## 📄 Frontend Code Overview

The frontend is a static web application hosted using AWS Amplify. It provides the user interface for authentication, image masking, prompt input, and result visualization.

---

### `📂 index.html`

Defines the structure of the web application.

**Responsibilities:**
- Renders the user interface layout.
- Includes authentication, image editor, prompt input, and results sections.
- Loads required JavaScript and CSS resources.
- Displays debugging and API payload information.

---

### 📂 `styles.css`

Handles application styling.

**Responsibilities:**
- Provides terminal-style visual theme.
- Manages layout responsiveness for desktop and mobile devices.
- Styles authentication forms, image editor, and result display areas.

---

### `📂 config.js`

Stores environment-specific configuration.

**Responsibilities:**
- Defines Amazon Cognito User Pool ID and Client ID.
- Specifies AWS region.
- Stores API Gateway invoke URL.
- Acts as a centralized configuration file for the frontend.

---

### `📂 cognito-authentication.js`

Manages Amazon Cognito authentication logic.

**Responsibilities:**
- Authenticates users using Cognito credentials.
- Handles first-time login password change flow.
- Retrieves and stores JWT tokens.
- Supplies authorization tokens for API requests.

---

### `📂 api.js`

Handles API communication with the backend.

**Responsibilities:**
- Sends authenticated POST requests to API Gateway.
- Attaches required headers including Authorization token.
- Handles API responses and error conditions.
- Abstracts XMLHttpRequest logic from application code.

---

### `📂 global.js`

Contains shared global variables and utility functions.

**Responsibilities:**
- Maintains API payload structure.
- Manages application-wide configuration values.
- Provides helper functions for payload updates and UI toggling.
- Converts canvas data to Base64 format.

---

### `📂 image-manipulation.js`

Implements image masking and canvas interaction logic.

**Responsibilities:**
- Loads and scales uploaded images.
- Creates a canvas layer for mask drawing.
- Supports mouse and touch-based drawing.
- Converts drawn masks into black-and-white format.
- Updates API payload with Base64-encoded image and mask data.

---

### 📂 `script.js`

Acts as the main application controller.

**Responsibilities:**
- Coordinates authentication flow.
- Handles user input for prompts and modes.
- Submits API requests to the backend.
- Displays AI-generated image results.
- Manages UI state transitions and error handling.
- Enables image download functionality.

---

## `📂 Image Assets Directory`

### `📂 images/ (Separate Folder)`

This directory contains sample images used for testing and demonstration purposes.

**Purpose:**
- Provide reference images for validating image upload and masking functionality.
- Used only on the client side.
- Not accessed by AWS Lambda or backend services.
- Kept separate to maintain clean separation between application logic and assets.

---

## 🧪 Usage Notes

- The Lambda function must be deployed behind API Gateway with a Cognito authorizer.
- Frontend configuration values in config.js must match deployed AWS resources.
- IAM permissions are required for:
  - Bedrock model invocation
  - DynamoDB write access
  - CloudWatch logging
- All backend components are stateless and serverless.
- Frontend files can be deployed directly using AWS Amplify or S3 static hosting.

---

## 📚 Related Documentation

For additional context, refer to:
- execution-guide.md
- workflow.md
- Root README.md
