# Dashboard UI

**State:** open


---

## Summary

Create a protected dashboard page that displays after users log in. The dashboard will show a list of all analyzed plants (initially empty) and provide an upload button to add new plant photos. This page will be protected so only authenticated users can access it.

---

## Learning goals

- Learn how to create protected routes in React Router
- Understand how to check authentication status and redirect unauthenticated users
- Practice building dashboard layouts with multiple components
- Learn how to structure a page that will display dynamic data later

---

## Requirements / Acceptance criteria

- [ ] Dashboard page displays at the /dashboard route
- [ ] Dashboard is protected and redirects unauthenticated users to login
- [ ] Page includes a Navbar component with logout functionality
- [ ] Page displays a heading or welcome message for the user
- [ ] Page includes an Upload button or component for uploading plant photos
- [ ] Page includes a section to display plant cards (initially empty or with placeholder)
- [ ] Page includes a Footer component
- [ ] Page is styled using Tailwind CSS and is responsive
- [ ] No backend integration or data fetching is implemented yet (static UI only)

---

## Step-by-step guide

1. **Create protected route component**
   - Action: Build a component that checks if a user is authenticated before allowing access to protected routes. If the user is not authenticated, redirect them to the login page. This component will wrap protected pages.
   - Where: Frontend/src/components/ProtectedRoute.jsx or Frontend/src/components/AuthGuard.jsx
   - Goal: A reusable component that protects routes based on authentication status
   - Reference: [React Router Protected Routes](https://reactrouter.com/en/main/examples/auth)

2. **Set up dashboard route**
   - Action: Create a route for the dashboard page in your React Router configuration. Wrap the dashboard route with the protected route component to ensure only authenticated users can access it.
   - Where: Frontend/src/App.jsx or routing configuration file
   - Goal: Dashboard page is accessible at /dashboard route and is protected
   - Reference: [React Router DOM Documentation](https://reactrouter.com/)

3. **Create dashboard page component**
   - Action: Build the main dashboard page component that will serve as the container for all dashboard content. Include basic structure and layout.
   - Where: Frontend/src/pages/Dashboard.jsx or Frontend/src/components/Dashboard.jsx
   - Goal: A dashboard page component ready to hold other components
   - Reference: [React Component Structure](https://react.dev/learn/your-first-component)

4. **Add Navbar with logout**
   - Action: Include the Navbar component in the dashboard and add logout functionality. The logout should sign out the user from Firebase and redirect them to the login page.
   - Where: Frontend/src/pages/Dashboard.jsx
   - Goal: Dashboard has navigation with working logout functionality
   - Reference: [Firebase Sign Out](https://firebase.google.com/docs/reference/js/auth#signout)

5. **Create UploadButton component**
   - Action: Build a button component that will trigger the plant photo upload process. For now, this can be a simple button that opens a modal or triggers an action (the actual upload functionality will be added later).
   - Where: Frontend/src/components/UploadButton.jsx
   - Goal: An upload button component ready to be connected to upload functionality
   - Reference: [Tailwind CSS Buttons](https://tailwindcss.com/docs/buttons)

6. **Create PlantList component**
   - Action: Build a component that will display a list of plant cards. Initially, this can show an empty state message or placeholder content. Structure it to accept an array of plants as props (which will be populated later).
   - Where: Frontend/src/components/PlantList.jsx
   - Goal: A component ready to display plant cards when data is available
   - Reference: [React Lists and Keys](https://react.dev/learn/rendering-lists)

7. **Create PlantCard component**
   - Action: Build a card component that will display information about a single analyzed plant. Include placeholders for plant image, disease name, and other key information. This will be used by the PlantList component.
   - Where: Frontend/src/components/PlantCard.jsx
   - Goal: A reusable card component for displaying plant information
   - Reference: [Tailwind CSS Cards](https://tailwindcss.com/docs)

8. **Assemble dashboard layout**
   - Action: Combine all components (Navbar, UploadButton, PlantList, Footer) in the dashboard page. Arrange them in a logical layout using Tailwind CSS grid or flexbox. Ensure the layout is responsive.
   - Where: Frontend/src/pages/Dashboard.jsx
   - Goal: A complete dashboard page with all components properly arranged
   - Reference: [Tailwind CSS Layout](https://tailwindcss.com/docs/display)

9. **Style and test responsiveness**
   - Action: Use Tailwind CSS to style the dashboard and ensure it looks good on different screen sizes. Test the layout on mobile, tablet, and desktop views. Verify that protected route functionality works correctly.
   - Where: All dashboard-related components
   - Goal: A fully responsive dashboard that properly protects routes
   - Reference: [Tailwind CSS Responsive Design](https://tailwindcss.com/docs/responsive-design)

---

## Time estimate

- Expected time: 75-90 minutes

---

## Constraints

- Tech stack: React, Tailwind CSS, React Router DOM, Firebase Authentication
- Not allowed: Backend API calls, data fetching, file upload functionality, image upload implementation
- Notes: This is a static UI page only. The upload button and plant list are placeholders for now. Actual data fetching and upload functionality will be implemented in later issues. Focus on creating the protected route and dashboard layout.

**Note for Developers:**
The mentioned points, schemas, and structures are essential guidance. You are free to improve or add better structures if needed. Additions or deletions of files, components, or changes are allowed if they improve the project. The goal is to build a clean, complete project with good UI and proper validation.

---

## Dependencies

- Blocked by: [#06, #07]
- Unblocks: [#09]

---

## Definition of Done

- [ ] All Requirements / Acceptance criteria are met.
- [ ] Code follows project conventions.
- [ ] Dashboard displays correctly without errors.
- [ ] Protected route redirects unauthenticated users to login.
- [ ] Logout functionality works correctly.
- [ ] No console errors or warnings.
- [ ] Page is responsive across different screen sizes.
- [ ] All components are properly structured and ready for data integration.

---

## Raise PR

- [ ] Create a feature branch following naming conventions.
- [ ] Commit in small logical chunks with clear messages.
- [ ] Ensure branch is up to date with `main`.
- [ ] Push branch and open a PR.
- [ ] Link the issue in the PR description.
- [ ] Add screenshots of the dashboard.
- [ ] Test protected route functionality and document results.
- [ ] Request review from assigned reviewers.
