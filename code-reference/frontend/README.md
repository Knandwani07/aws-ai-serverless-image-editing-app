#  ✨ Frontend – Application UI

This directory contains the frontend source code for the AWS Serverless AI Image Editing Application. The frontend is responsible for user interaction, authentication, image masking, prompt submission, and displaying AI-generated results.

---

## 📄 File Overview

### `index.html`

The main entry point of the frontend application.

**Purpose:**
- Defines the overall structure of the web interface.
- Loads required CSS and JavaScript resources.
- Provides containers for authentication, image editing, prompt input, and result display.
- Acts as the bootstrap file for the frontend application logic.

---

### `styles.css`

Handles the visual styling and layout of the application.

**Purpose:**
- Defines the application’s visual theme and layout.
- Ensures responsive behavior across different screen sizes.
- Styles authentication forms, image editor, buttons, and result sections.
- Maintains consistent UI presentation across the application.

---

### `js/ (JavaScript Directory)`

Contains all client-side JavaScript logic used by the application.

**Purpose:**
- Implements frontend application behavior and state management.
- Handles authentication, API communication, and image processing logic.
- Manages user interactions, request payload construction, and UI updates.
- Acts as the bridge between the user interface and the backend API.

**Note:**
- Detailed documentation for individual JavaScript files is provided in a separate README within the `js` directory.
- This directory is packaged together with `index.html` and `styles.css` for deployment.

---

## 🚀 Deployment Notes

- All frontend files (`index.html`, `styles.css`, and the `js` directory) must be included when packaging the application.
- Compress the contents of this directory into a ZIP archive before deploying via AWS Amplify.
- Ensure backend API CORS settings allow browser-based access.

---

## ✅ Summary

These frontend components collectively provide a complete, browser-based interface for interacting with the serverless backend, enabling secure authentication, intuitive image editing, and seamless visualization of AI-generated results.
