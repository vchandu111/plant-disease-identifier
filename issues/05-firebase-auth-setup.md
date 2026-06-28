# Firebase Auth Setup

**State:** open


---

## Summary

Set up Firebase Authentication in your project by creating a Firebase project, configuring Firebase SDK in the frontend, and preparing the environment for authentication integration. This issue focuses on configuration and setup only, not the actual authentication implementation.

---

## Learning goals

- Learn how to create and configure a Firebase project
- Understand how to integrate Firebase SDK into a React application
- Learn how to manage environment variables and Firebase configuration
- Understand the Firebase Authentication service structure

---

## Requirements / Acceptance criteria

- [ ] Firebase project is created in Firebase Console
- [ ] Firebase Authentication is enabled with email/password provider
- [ ] Firebase configuration object is obtained from Firebase Console
- [ ] Firebase SDK is installed in the frontend project
- [ ] Firebase is initialized in the React application
- [ ] Firebase configuration is stored securely using environment variables
- [ ] Firebase Auth instance is accessible throughout the application
- [ ] No authentication logic is implemented yet (setup only)

---

## Step-by-step guide

1. **Create Firebase project**
   - Action: Go to Firebase Console and create a new project for the Plant Disease Identifier application. Give it an appropriate name and follow the setup wizard.
   - Where: Firebase Console (https://console.firebase.google.com/)
   - Goal: A Firebase project is created and ready for configuration
   - Reference: [Firebase Console Documentation](https://firebase.google.com/docs/web/setup)

2. **Enable Authentication service**
   - Action: In the Firebase Console, navigate to the Authentication section and enable the Email/Password authentication provider. This will allow users to sign up and log in using email and password.
   - Where: Firebase Console > Authentication
   - Goal: Email/Password authentication is enabled for the project
   - Reference: [Firebase Authentication Setup](https://firebase.google.com/docs/auth/web/start)

3. **Get Firebase configuration**
   - Action: In Firebase Console, go to Project Settings and find the web app configuration. Copy the Firebase configuration object that contains API keys, project ID, and other necessary credentials.
   - Where: Firebase Console > Project Settings > General > Your apps
   - Goal: Firebase configuration object is obtained and ready to use
   - Reference: [Firebase Configuration](https://firebase.google.com/docs/web/setup#config-object)

4. **Install Firebase SDK**
   - Action: Install the Firebase JavaScript SDK package in your frontend project using npm. This package provides all the necessary Firebase services including Authentication.
   - Where: Frontend directory (run npm install command)
   - Goal: Firebase SDK is installed and available in the project
   - Reference: [Firebase SDK Installation](https://firebase.google.com/docs/web/setup#install-sdk)

5. **Create Firebase configuration file**
   - Action: Create a configuration file in your frontend project to initialize Firebase. Store the Firebase configuration object in this file, preferably using environment variables for sensitive data.
   - Where: Frontend/src/config/firebase.js or Frontend/src/firebase.js
   - Goal: Firebase is configured and ready to be initialized
   - Reference: [Firebase Initialize App](https://firebase.google.com/docs/web/setup#initialize-app)

6. **Initialize Firebase in application**
   - Action: Initialize Firebase in your React application using the configuration. Export Firebase Auth instance so it can be used throughout the application for authentication operations.
   - Where: Frontend/src/config/firebase.js or Frontend/src/firebase.js
   - Goal: Firebase is initialized and Auth instance is available
   - Reference: [Firebase Auth Get Started](https://firebase.google.com/docs/auth/web/start)

7. **Set up environment variables**
   - Action: Create an environment file to store Firebase configuration values securely. Add the environment file to .gitignore to prevent committing sensitive data. Use environment variables in your Firebase configuration.
   - Where: Frontend/.env (and update .gitignore)
   - Goal: Firebase configuration is stored securely and not committed to version control
   - Reference: [Vite Environment Variables](https://vitejs.dev/guide/env-and-mode.html)

---

## Time estimate

- Expected time: 70-90 minutes

---

## Constraints

- Tech stack: React, Firebase SDK, Vite
- Not allowed: Authentication implementation logic, signup/login functionality, backend authentication, password hashing, session management
- Notes: This issue is about configuration and setup only. The actual authentication integration will happen in issues #06 and #07. Focus on getting Firebase properly configured and initialized.

**Note for Developers:**
The mentioned points, schemas, and structures are essential guidance. You are free to improve or add better structures if needed. Additions or deletions of files, components, or changes are allowed if they improve the project. The goal is to build a clean, complete project with good UI and proper validation.

---

## Dependencies

- Blocked by: [#01]
- Unblocks: [#06, #07]

---

## Definition of Done

- [ ] All Requirements / Acceptance criteria are met.
- [ ] Code follows project conventions.
- [ ] Firebase project is created and configured correctly.
- [ ] Firebase SDK is properly installed and initialized.
- [ ] Environment variables are set up securely.
- [ ] No console errors or warnings related to Firebase.
- [ ] Firebase Auth instance is accessible in the application.

---

## Raise PR

- [ ] Create a feature branch following naming conventions.
- [ ] Commit in small logical chunks with clear messages.
- [ ] Ensure branch is up to date with `main`.
- [ ] Push branch and open a PR.
- [ ] Link the issue in the PR description.
- [ ] Document Firebase project setup steps.
- [ ] Verify Firebase configuration is working.
- [ ] Request review from assigned reviewers.
