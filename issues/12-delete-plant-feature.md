# Delete Plant Feature

**State:** open


---

## Summary

Implement functionality to delete plant profiles from the application. Create a backend endpoint that removes plants from the database and frontend integration that allows users to delete plants from the detail view and updates the UI accordingly.

---

## Learning goals

- Learn how to create DELETE endpoints in FastAPI
- Understand how to implement soft deletes or hard deletes in databases
- Practice implementing delete functionality with confirmation dialogs
- Learn how to update UI after deleting items
- Understand how to handle file cleanup when deleting records

---

## Requirements / Acceptance criteria

- [ ] Backend DELETE endpoint removes plant from database
- [ ] Endpoint verifies plant belongs to authenticated user before deletion
- [ ] Endpoint handles associated image file deletion (optional cleanup)
- [ ] Frontend delete button is accessible from plant detail page
- [ ] Delete action shows confirmation dialog before proceeding
- [ ] Successful deletion removes plant from database and UI
- [ ] User is redirected to dashboard after deletion
- [ ] Dashboard updates to reflect deleted plant
- [ ] Error handling is implemented for deletion failures
- [ ] Appropriate success/error messages are displayed

---

## Step-by-step guide

### Backend Implementation

1. **Create DELETE plant endpoint**
   - Action: Build a DELETE endpoint that removes a plant profile by its ID. Verify that the plant belongs to the authenticated user before allowing deletion. Return appropriate success or error responses.
   - Where: Backend/main.py or Backend/routes/plants.py
   - Goal: An API endpoint that safely deletes plant records
   - Reference: [FastAPI DELETE Endpoints](https://fastapi.tiangolo.com/tutorial/path-params/)

2. **Implement authorization check**
   - Action: Ensure the endpoint verifies that the plant to be deleted belongs to the authenticated user. Return an error if the user tries to delete a plant that doesn't belong to them or doesn't exist.
   - Where: Backend/main.py or authorization logic
   - Goal: Users can only delete their own plants
   - Reference: [FastAPI Security](https://fastapi.tiangolo.com/tutorial/security/)

3. **Handle image file cleanup**
   - Action: Optionally implement logic to delete the associated image file from storage when a plant is deleted. Consider whether to keep images for reference or remove them. Handle file deletion errors gracefully.
   - Where: Backend/main.py or file cleanup logic
   - Goal: Associated files are cleaned up appropriately
   - Reference: [Python File Operations](https://docs.python.org/3/tutorial/inputoutput.html)

4. **Return appropriate response**
   - Action: Structure the API response to indicate successful deletion. Return appropriate HTTP status codes and success messages.
   - Where: Backend/main.py or response handling
   - Goal: API returns clear success/error responses
   - Reference: [FastAPI Response Status Codes](https://fastapi.tiangolo.com/tutorial/response-status-code/)

### Frontend Implementation

5. **Create delete handler function**
   - Action: Build a function that calls the DELETE API endpoint to remove a plant. Include authentication headers and handle the API response appropriately.
   - Where: Frontend/src/services/api.js or Frontend/src/utils/api.js
   - Goal: A reusable function to delete plants via API
   - Reference: [Fetch API DELETE](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

6. **Add delete button to detail page**
   - Action: Update the PlantDetail page to include a delete button. Style it appropriately and position it in a logical location (e.g., near other action buttons).
   - Where: Frontend/src/pages/PlantDetail.jsx
   - Goal: Delete button is visible and accessible on detail page
   - Reference: [Tailwind CSS Buttons](https://tailwindcss.com/docs/buttons)

7. **Implement confirmation dialog**
   - Action: Create a confirmation dialog that appears when the user clicks the delete button. Ask the user to confirm before proceeding with deletion. Only proceed if the user confirms.
   - Where: Frontend/src/components/DeleteConfirmation.jsx or similar
   - Goal: Users must confirm before deleting plants
   - Reference: [React Conditional Rendering](https://react.dev/learn/conditional-rendering)

8. **Handle delete action**
   - Action: When the user confirms deletion, call the delete API function. Show loading state during the deletion process. Handle success and error cases appropriately.
   - Where: Frontend/src/pages/PlantDetail.jsx
   - Goal: Delete action works correctly with proper feedback
   - Reference: [React State Management](https://react.dev/learn/state-a-component-s-memory)

9. **Update UI after deletion**
   - Action: After successful deletion, redirect the user to the dashboard and update the plant list to remove the deleted plant. Show a success message to confirm the deletion.
   - Where: Frontend/src/pages/PlantDetail.jsx and Dashboard.jsx
   - Goal: UI updates correctly after deletion
   - Reference: [React Router useNavigate](https://reactrouter.com/en/main/hooks/use-navigate)

10. **Handle errors**
    - Action: Implement error handling for deletion failures. Display appropriate error messages if deletion fails due to network issues, authorization problems, or other errors.
    - Where: Frontend/src/pages/PlantDetail.jsx
    - Goal: Errors are handled gracefully with user feedback
    - Reference: [React Error Handling](https://react.dev/learn/conditional-rendering)

11. **Test delete functionality**
    - Action: Test the complete delete flow with various scenarios. Verify that deletion works correctly, confirmation dialog appears, UI updates properly, and error handling functions as expected.
    - Where: Application end-to-end
    - Goal: Delete functionality works correctly end-to-end
    - Reference: Test deletion with various plants and scenarios

---

## Time estimate

- Expected time: 70-85 minutes

---

## Constraints

- Tech stack: React, FastAPI, SQLite, Firebase Authentication, Tailwind CSS, React Router DOM
- Not allowed: Deleting other users' plants, permanent deletion without confirmation, complex undo functionality
- Notes: Always require user confirmation before deletion. Ensure users can only delete their own plants. Keep the implementation simple and focused.

**Note for Developers:**
The mentioned points, schemas, and structures are essential guidance. You are free to improve or add better structures if needed. Additions or deletions of files, components, or changes are allowed if they improve the project. The goal is to build a clean, complete project with good UI and proper validation.

---

## Dependencies

- Blocked by: [#11]
- Unblocks: [#14]

---

## Definition of Done

- [ ] All Requirements / Acceptance criteria are met.
- [ ] Code follows project conventions.
- [ ] Delete endpoint only allows deletion of user's own plants.
- [ ] Confirmation dialog appears before deletion.
- [ ] Plants are successfully removed from database.
- [ ] UI updates correctly after deletion.
- [ ] Error handling works for all failure scenarios.
- [ ] No console errors or warnings.

---

## Raise PR

- [ ] Create a feature branch following naming conventions.
- [ ] Commit in small logical chunks with clear messages.
- [ ] Ensure branch is up to date with `main`.
- [ ] Push branch and open a PR.
- [ ] Link the issue in the PR description.
- [ ] Add screenshots showing delete flow.
- [ ] Test deletion with various scenarios and document results.
- [ ] Request review from assigned reviewers.
