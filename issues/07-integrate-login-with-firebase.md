# Integrate Login with Firebase

**State:** open


---

## Summary

Connect the login form to Firebase Authentication so users can sign in to their accounts. When users submit the login form, their credentials will be verified by Firebase. Handle success and error cases appropriately and redirect authenticated users to the dashboard.

---

## Learning goals

- Learn how to integrate Firebase Authentication sign-in functionality with React forms
- Understand how to manage authenticated user state in React
- Practice implementing protected routes based on authentication status
- Learn how to handle authentication errors and edge cases

---

## Requirements / Acceptance criteria

- [ ] Login form submission triggers Firebase Authentication sign-in
- [ ] Firebase verifies user credentials and signs in the user
- [ ] Success message is displayed when login is successful
- [ ] Error messages are displayed for various failure scenarios (invalid credentials, user not found, wrong password)
- [ ] Authenticated user is redirected to dashboard after successful login
- [ ] Form shows loading state during authentication process
- [ ] User authentication state is tracked in the application
- [ ] No backend authentication logic is implemented (Firebase handles everything)

---

## Step-by-step guide

1. **Import Firebase Auth**
   - Action: Import the Firebase Auth instance that was set up earlier. Make sure you have access to Firebase Authentication methods in your login form component.
   - Where: Frontend/src/components/LoginForm.jsx
   - Goal: Firebase Auth is available in the login form component
   - Reference: [Firebase Auth Methods](https://firebase.google.com/docs/auth/web/start#sign_in_existing_users)

2. **Create login handler function**
   - Action: Create an async function that handles the login form submission. This function should use Firebase's signInWithEmailAndPassword method to authenticate the user.
   - Where: Frontend/src/components/LoginForm.jsx
   - Goal: A function ready to handle user authentication with Firebase
   - Reference: [Firebase signInWithEmailAndPassword](https://firebase.google.com/docs/reference/js/auth#signinwithemailandpassword)

3. **Connect form submission to handler**
   - Action: Update the form's onSubmit handler to call the login function. Prevent the default form submission behavior and call your Firebase login handler instead.
   - Where: Frontend/src/components/LoginForm.jsx
   - Goal: Form submission triggers Firebase authentication
   - Reference: [React Form Handling](https://react.dev/reference/react-dom/components/form)

4. **Implement loading state**
   - Action: Add state to track when the authentication process is in progress. Display a loading indicator or disable the submit button while Firebase is processing the login request.
   - Where: Frontend/src/components/LoginForm.jsx
   - Goal: Users see feedback that their request is being processed
   - Reference: [React useState Hook](https://react.dev/reference/react/useState)

5. **Handle success case**
   - Action: When Firebase successfully authenticates the user, store the user information in application state and redirect the user to the dashboard. Use React Router's navigation functionality for the redirect.
   - Where: Frontend/src/components/LoginForm.jsx
   - Goal: Users are authenticated and redirected to the dashboard
   - Reference: [React Router useNavigate](https://reactrouter.com/en/main/hooks/use-navigate)

6. **Handle error cases**
   - Action: Implement error handling for various Firebase authentication errors. Catch different error types (user not found, wrong password, invalid email format) and display appropriate error messages to the user.
   - Where: Frontend/src/components/LoginForm.jsx
   - Goal: Users receive clear feedback when login fails
   - Reference: [Firebase Auth Error Codes](https://firebase.google.com/docs/auth/admin/errors)

7. **Set up authentication state management**
   - Action: Create a way to track the authenticated user state throughout the application. This can be done using React Context or a state management solution. The user state should be accessible to components that need to check authentication status.
   - Where: Frontend/src/context/AuthContext.jsx or similar
   - Goal: Authentication state is available throughout the application
   - Reference: [React Context API](https://react.dev/learn/passing-data-deeply-with-context)

8. **Test login flow**
   - Action: Test the complete login flow with valid and invalid credentials. Verify that successful logins work, error messages display correctly, redirects happen as expected, and user state is properly maintained.
   - Where: Application
   - Goal: Login functionality works correctly end-to-end
   - Reference: Test with accounts created in issue #06

---

## Time estimate

- Expected time: 70-90 minutes

---

## Constraints

- Tech stack: React, Firebase Authentication, React Router DOM
- Not allowed: Backend authentication logic, password hashing, session management, JWT tokens
- Notes: All authentication is handled by Firebase SDK in the frontend. No backend authentication endpoints are needed. Focus on integrating Firebase Auth methods with the existing login form and managing user state.

**Note for Developers:**
The mentioned points, schemas, and structures are essential guidance. You are free to improve or add better structures if needed. Additions or deletions of files, components, or changes are allowed if they improve the project. The goal is to build a clean, complete project with good UI and proper validation.

---

## Dependencies

- Blocked by: [#04, #05]
- Unblocks: [#08]

---

## Definition of Done

- [ ] All Requirements / Acceptance criteria are met.
- [ ] Code follows project conventions.
- [ ] Login form successfully authenticates users with Firebase.
- [ ] Error handling works correctly for all error scenarios.
- [ ] Loading states are displayed during authentication.
- [ ] Users are redirected to dashboard after successful login.
- [ ] User authentication state is tracked in the application.
- [ ] No console errors or warnings.

---

## Raise PR

- [ ] Create a feature branch following naming conventions.
- [ ] Commit in small logical chunks with clear messages.
- [ ] Ensure branch is up to date with `main`.
- [ ] Push branch and open a PR.
- [ ] Link the issue in the PR description.
- [ ] Add screenshots showing login flow.
- [ ] Test login with various scenarios and document results.
- [ ] Request review from assigned reviewers.
