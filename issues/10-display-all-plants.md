# Display All Plants

**State:** open


---

## Summary

Implement functionality to fetch and display all analyzed plants for the authenticated user on the dashboard. Create a backend endpoint that returns the user's plants and integrate it with the frontend to populate the plant list with actual data.

---

## Learning goals

- Learn how to create GET endpoints that return user-specific data
- Understand how to filter database queries by user
- Practice fetching data from APIs and displaying it in React components
- Learn how to handle empty states when no data exists
- Understand how to structure API responses for frontend consumption

---

## Requirements / Acceptance criteria

- [ ] Backend endpoint returns all plants for the authenticated user
- [ ] Endpoint filters plants by user ID from Firebase token
- [ ] API returns plant data including image URL, disease, pests, health issues, and creation date
- [ ] Frontend fetches plants when dashboard loads
- [ ] PlantList component displays all user's plants
- [ ] PlantCard components show plant information correctly
- [ ] Empty state message is displayed when user has no plants
- [ ] Loading state is shown while fetching plants
- [ ] Error handling is implemented for API failures

---

## Step-by-step guide

### Backend Implementation

1. **Create GET plants endpoint**
   - Action: Build a GET endpoint that retrieves all plant profiles for the authenticated user. Extract the user ID from the Firebase authentication token and query the database to return only that user's plants.
   - Where: Backend/main.py or Backend/routes/plants.py
   - Goal: An API endpoint that returns user-specific plant data
   - Reference: [FastAPI GET Endpoints](https://fastapi.tiangolo.com/tutorial/path-params/)

2. **Implement user filtering**
   - Action: Ensure the database query filters plants by the authenticated user's ID. Use the user ID from the Firebase token to match against stored user references in plant records.
   - Where: Backend/main.py or database query logic
   - Goal: Users only see their own plants
   - Reference: [SQLite WHERE Clause](https://www.sqlite.org/lang_select.html)

3. **Format API response**
   - Action: Structure the API response to include all necessary plant information. Include image URLs (or paths), disease identification, pest information, health issues, and timestamps. Ensure the response format is consistent and easy for the frontend to consume.
   - Where: Backend/main.py or response models
   - Goal: API returns well-structured plant data
   - Reference: [FastAPI Response Models](https://fastapi.tiangolo.com/tutorial/response-model/)

4. **Add error handling**
   - Action: Implement error handling for cases where the user is not authenticated, database queries fail, or other errors occur. Return appropriate HTTP status codes and error messages.
   - Where: Backend/main.py or error handlers
   - Goal: API handles errors gracefully
   - Reference: [FastAPI Error Handling](https://fastapi.tiangolo.com/tutorial/handling-errors/)

### Frontend Implementation

5. **Create API service function**
   - Action: Build a function that fetches all plants from the backend API. Include authentication headers with the Firebase token. Handle the API response and return plant data.
   - Where: Frontend/src/services/api.js or Frontend/src/utils/api.js
   - Goal: A reusable function to fetch plants from the API
   - Reference: [Fetch API Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

6. **Fetch plants on dashboard load**
   - Action: Update the Dashboard component to fetch plants when it loads. Use useEffect hook to trigger the API call when the component mounts. Store the fetched plants in component state.
   - Where: Frontend/src/pages/Dashboard.jsx
   - Goal: Dashboard automatically loads user's plants on mount
   - Reference: [React useEffect Hook](https://react.dev/reference/react/useEffect)

7. **Update PlantList component**
   - Action: Modify the PlantList component to accept plants as props and render PlantCard components for each plant. Handle the case when the plants array is empty by displaying an appropriate message.
   - Where: Frontend/src/components/PlantList.jsx
   - Goal: PlantList displays all plants passed as props
   - Reference: [React Lists and Keys](https://react.dev/learn/rendering-lists)

8. **Update PlantCard component**
   - Action: Enhance the PlantCard component to display actual plant data including image, disease name, pest information, and other details. Style the card appropriately using Tailwind CSS.
   - Where: Frontend/src/components/PlantCard.jsx
   - Goal: PlantCard displays real plant information
   - Reference: [React Props](https://react.dev/learn/passing-props-to-a-component)

9. **Implement loading and error states**
   - Action: Add loading state while fetching plants and error state if the API call fails. Display appropriate messages to the user in both cases. Use conditional rendering to show loading spinner, error message, or plant list.
   - Where: Frontend/src/pages/Dashboard.jsx
   - Goal: Users see feedback during data fetching and errors
   - Reference: [React Conditional Rendering](https://react.dev/learn/conditional-rendering)

10. **Add image display**
    - Action: Implement image display in PlantCard components. Use the image URL or path from the API response to display plant images. Handle cases where images might not load correctly.
    - Where: Frontend/src/components/PlantCard.jsx
    - Goal: Plant images are displayed correctly in cards
    - Reference: [React Image Component](https://react.dev/reference/react-dom/components/img)

11. **Test complete flow**
    - Action: Test the complete flow of fetching and displaying plants. Verify that plants are fetched correctly, displayed properly, loading states work, and error handling functions as expected.
    - Where: Application end-to-end
    - Goal: Display plants feature works correctly end-to-end
    - Reference: Test with multiple plants and verify display

---

## Time estimate

- Expected time: 75-90 minutes

---

## Constraints

- Tech stack: React, FastAPI, SQLite, Firebase Authentication, Tailwind CSS
- Not allowed: Public endpoints without authentication, displaying other users' plants, complex pagination (keep it simple)
- Notes: Ensure plants are filtered by authenticated user. Keep the implementation simple - fetch all plants at once without pagination for now.

**Note for Developers:**
The mentioned points, schemas, and structures are essential guidance. You are free to improve or add better structures if needed. Additions or deletions of files, components, or changes are allowed if they improve the project. The goal is to build a clean, complete project with good UI and proper validation.

---

## Dependencies

- Blocked by: [#09]
- Unblocks: [#11]

---

## Definition of Done

- [ ] All Requirements / Acceptance criteria are met.
- [ ] Code follows project conventions.
- [ ] Backend endpoint returns only the authenticated user's plants.
- [ ] Frontend successfully fetches and displays plants.
- [ ] Loading and error states work correctly.
- [ ] Empty state is displayed when no plants exist.
- [ ] Plant images are displayed correctly.
- [ ] No console errors or warnings.

---

## Raise PR

- [ ] Create a feature branch following naming conventions.
- [ ] Commit in small logical chunks with clear messages.
- [ ] Ensure branch is up to date with `main`.
- [ ] Push branch and open a PR.
- [ ] Link the issue in the PR description.
- [ ] Add screenshots showing plants displayed on dashboard.
- [ ] Test with various scenarios and document results.
- [ ] Request review from assigned reviewers.
