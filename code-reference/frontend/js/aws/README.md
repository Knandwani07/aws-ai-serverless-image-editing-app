# 📁 AWS JavaScript SDK Dependencies – Cognito Support

This directory contains AWS-provided JavaScript libraries required by the frontend of the **AWS Serverless AI Image Editing Application**.

The files in this folder are third-party dependencies used to enable secure authentication with Amazon Cognito directly from the browser. These libraries are vendor-managed and are not part of the application’s custom business logic.

---

## 📄 File Overview

### 📂 `amazon-cognito-identity.min.js`

This file is the minified Amazon Cognito Identity SDK for JavaScript.

**🎯 Purpose:**
- Enable browser-based authentication using Amazon Cognito User Pools.
- Provide client-side implementations for Cognito authentication flows.

**🛠️ Key Responsibilities:**
- Authenticate users against a Cognito User Pool.
- Handle Secure Remote Password (SRP) authentication.
- Manage access tokens, ID tokens, and refresh tokens.
- Support password challenges such as first-time login and password reset.
- Perform cryptographic operations required by Cognito authentication flows.
- Manage browser-side session state and token handling.

**📌 Characteristics:**
- Vendor-managed and minified for production use.
- Licensed under the Apache 2.0 License.
- Intended to be consumed directly by browser-based applications.
- Not meant to be modified or extended directly.

---

## 🔐 Security Considerations

- This file performs sensitive authentication-related operations.
- It should be served only over HTTPS.
- No credentials or secrets should be hardcoded alongside this library.
- Configuration values such as User Pool ID and Client ID must be provided externally via `config.js`.

---

## 🧪 Usage Notes

- This library is used internally by `cognito-authentication.js` for user login flows.
- It must be loaded before any custom authentication logic is executed.
- Updates to this file should only be performed by replacing it with a newer official release from AWS.
- Do not manually edit the contents of this file.

---

## 📚 Related Files

This directory works in conjunction with:
- `js/cognito-authentication.js` – Application-level authentication logic
- `js/config.js` – Environment-specific Cognito configuration
- Root `README.md`
- `execution-guide.md`

---

## ⚠️ Maintenance Guidance

- Treat this directory as a **vendor dependency folder**.
- Track the version externally if upgrading the Cognito SDK.
- Validate authentication flows after any library upgrade.
- Keep this file under source control to ensure consistent builds.

