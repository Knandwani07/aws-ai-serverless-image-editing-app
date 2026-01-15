# 📁 JavaScript Source Directory – Frontend Logic Reference

This directory contains all client-side JavaScript files used by the **AWS Serverless AI Image Editing Application**.

The files in this folder collectively implement authentication, image manipulation, API communication, application state management, and user interface orchestration. The frontend interacts securely with AWS backend services using Amazon Cognito for authentication and Amazon API Gateway for API requests.

---

## 📄 File Overview

### 📂 `config.js`

Stores environment-specific configuration values required by the frontend.

**🎯 Purpose:**
- Centralize AWS configuration for the client application.

**🛠️ Responsibilities:**
- Define Amazon Cognito User Pool ID.
- Define Cognito App Client ID.
- Specify AWS region.
- Store API Gateway invoke URL.
- Decouple environment configuration from application logic.

---

### 📂 `cognito-authentication.js`

Handles user authentication using Amazon Cognito.

**🎯 Purpose:**
- Authenticate users before allowing access to image editing features.

**🛠️ Responsibilities:**
- Perform user authentication using Cognito User Pools.
- Handle incorrect credentials and authentication failures.
- Manage first-time login password change flow.
- Retrieve and return JWT tokens upon successful authentication.
- Provide tokens for authenticated API requests.

---

### 📂 `api.js`

Implements communication with the backend API.

**🎯 Purpose:**
- Abstract HTTP communication between frontend and backend services.

**🛠️ Responsibilities:**
- Send authenticated POST requests to API Gateway.
- Attach required headers including Authorization token.
- Handle API success and error responses.
- Parse JSON responses returned by AWS Lambda.

---

### 📂 `global.js`

Contains shared global variables and helper functions.

**🎯 Purpose:**
- Maintain application-wide state and reusable utilities.

**🛠️ Responsibilities:**
- Define the API payload structure.
- Store global configuration values (image size limits, stroke size).
- Update and display API payload for debugging.
- Convert canvas data to Base64 format.
- Provide helper functions for UI visibility and state toggling.

---

### 📂 `image-manipulation.js`

Implements image loading, resizing, and mask creation logic.

**🎯 Purpose:**
- Enable users to visually create masks on uploaded images.

**🛠️ Responsibilities:**
- Load and preview user-uploaded images.
- Scale images based on viewport constraints.
- Create a canvas overlay for drawing masks.
- Support mouse and touch-based drawing.
- Convert drawn masks to black-and-white format.
- Encode images and masks in Base64 format.
- Update API payload with image and mask data.

---

### 📂 `script.js`

Acts as the main application controller and event coordinator.

**🎯 Purpose:**
- Orchestrate the end-to-end user interaction workflow.

**🛠️ Responsibilities:**
- Manage authentication flow and token storage.
- Handle image upload and mask editor initialization.
- Capture prompt and mode inputs.
- Submit requests to the backend API.
- Display AI-generated image results.
- Manage error handling and UI feedback.
- Enable download of generated images.
- Coordinate interactions across all JavaScript modules.

---

## 🔗 Execution Flow Summary

- User authenticates via Amazon Cognito.
- JWT token is stored in the API payload.
- User uploads an image and creates a mask.
- Image, mask, and prompt are assembled into the API request.
- Authenticated request is sent to API Gateway.
- Backend Lambda processes the request and returns results.
- Generated images are rendered and made available for download.

---

## 🧪 Usage Notes

- All files in this directory are loaded client-side.
- `config.js` must be updated to match deployed AWS resources.
- Cognito authentication is mandatory before API calls.
- No secrets should be committed to this directory.
- These files are intended for deployment via AWS Amplify or static hosting.
- Backend logic is not present in this directory.

---

## 📚 Related Documentation

For additional context, refer to:
- `execution-guide.md`
- `workflow.md`
- `code-reference.md`
- Root `README.md`
