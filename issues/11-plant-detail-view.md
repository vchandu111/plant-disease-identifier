# Plant Detail View

**State:** open


---

## Summary

Create a detailed view page that displays complete information about a single analyzed plant. This includes the full plant image, disease identification, pest information, health issues, and all treatment recommendations. Implement both the backend endpoint to fetch plant details and the frontend page to display them.

---

## Learning goals

- Learn how to create detail view pages in React Router
- Understand how to fetch and display detailed data for a single item
- Practice implementing image viewers and structured content display
- Learn how to handle route parameters to identify specific items
- Understand how to structure detailed information displays

---

## Requirements / Acceptance criteria

- [ ] Plant detail page displays at /plants/:id route
- [ ] Page is protected and requires authentication
- [ ] Backend endpoint returns complete plant data including all analysis results
- [ ] Page displays plant image in a viewer component
- [ ] Page displays disease identification with appropriate styling
- [ ] Page displays pest information if pests are detected
- [ ] Page displays health issues identified by the LLM
- [ ] Page displays all treatment recommendations in a list
- [ ] Page includes navigation back to dashboard
- [ ] Page includes delete and export buttons (functionality in later issues)
- [ ] Error handling is implemented for invalid plant IDs or access errors

---

## Step-by-step guide

### Backend Implementation

1. **Create GET plant by ID endpoint**
   - Action: Build a GET endpoint that retrieves a single plant profile by its ID. Verify that the plant belongs to the authenticated user before returning it. Return complete plant data including all analysis results.
   - Where: Backend/main.py or Backend/routes/plants.py
   - Goal: An API endpoint that returns detailed plant information
   - Reference: [FastAPI Path Parameters](https://fastapi.tiangolo.com/tutorial/path-params/)

2. **Implement authorization check**
   - Action: Ensure the endpoint verifies that the requested plant belongs to the authenticated user. Return an error if the user tries to access a plant that doesn't belong to them or doesn't exist.
   - Where: Backend/main.py or authorization logic
   - Goal: Users can only access their own plants
   - Reference: [FastAPI Security](https://fastapi.tiangolo.com/tutorial/security/)

3. **Return complete plant data**
   - Action: Structure the API response to include all plant information including image path, disease, pests, health issues, treatment recommendations array, and timestamps. Ensure the response format matches what the frontend expects.
   - Where: Backend/main.py or response models
   - Goal: API returns complete plant details
   - Reference: [FastAPI Response Models](https://fastapi.tiangolo.com/tutorial/response-model/)

### Frontend Implementation

4. **Set up plant detail route**
   - Action: Create a route for the plant detail page that accepts a plant ID parameter. Wrap the route with the protected route component to ensure only authenticated users can access it.
   - Where: Frontend/src/App.jsx or routing configuration
   - Goal: Plant detail page is accessible at /plants/:id route and is protected
   - Reference: [React Router Dynamic Routes](https://reactrouter.com/en/main/route/route#dynamic-segments)

5. **Create PlantDetail page component**
   - Action: Build the main plant detail page component that will serve as the container for all detail view content. Extract the plant ID from the route parameters.
   - Where: Frontend/src/pages/PlantDetail.jsx
   - Goal: A plant detail page component ready to display plant information
   - Reference: [React Router useParams](https://reactrouter.com/en/main/hooks/use-params)

6. **Fetch plant details**
   - Action: Create a function to fetch plant details from the API using the plant ID. Call this function when the component mounts and store the plant data in component state. Handle loading and error states.
   - Where: Frontend/src/pages/PlantDetail.jsx
   - Goal: Plant details are fetched and stored in component state
   - Reference: [React useEffect Hook](https://react.dev/reference/react/useEffect)

7. **Create ImageViewer component**
   - Action: Build a component that displays the plant image in a viewer. Make the image large and clear so users can see plant details. Handle image loading errors gracefully.
   - Where: Frontend/src/components/ImageViewer.jsx
   - Goal: Plant images are displayed clearly in the detail view
   - Reference: [React Image Component](https://react.dev/reference/react-dom/components/img)

8. **Create DiseaseBadge component**
   - Action: Build a component that displays the disease identification with appropriate styling. Use badges or cards to make the disease information prominent and easy to read.
   - Where: Frontend/src/components/DiseaseBadge.jsx
   - Goal: Disease information is displayed clearly and prominently
   - Reference: [Tailwind CSS Badges](https://tailwindcss.com/docs)

9. **Create PestBadge component**
   - Action: Build a component that displays pest information if pests are detected. Show appropriate styling to indicate pest presence and details.
   - Where: Frontend/src/components/PestBadge.jsx
   - Goal: Pest information is displayed clearly when present
   - Reference: [Tailwind CSS Components](https://tailwindcss.com/docs)

10. **Create RecommendationList component**
    - Action: Build a component that displays all treatment recommendations in a list format. Each recommendation should be displayed clearly with proper formatting. Use cards or list items to organize recommendations.
    - Where: Frontend/src/components/RecommendationList.jsx
    - Goal: Treatment recommendations are displayed in an organized list
    - Reference: [React Lists](https://react.dev/learn/rendering-lists)

11. **Create RecommendationCard component**
    - Action: Build a component that displays a single treatment recommendation. Style it appropriately so recommendations are easy to read and understand.
    - Where: Frontend/src/components/RecommendationCard.jsx
    - Goal: Individual recommendations are displayed clearly
    - Reference: [Tailwind CSS Cards](https://tailwindcss.com/docs)

12. **Add navigation and action buttons**
    - Action: Add a button to navigate back to the dashboard. Include placeholder buttons for delete and export functionality (these will be implemented in later issues). Style buttons appropriately.
    - Where: Frontend/src/pages/PlantDetail.jsx
    - Goal: Users can navigate back and see action buttons
    - Reference: [React Router useNavigate](https://reactrouter.com/en/main/hooks/use-navigate)

13. **Assemble detail page layout**
    - Action: Combine all components (ImageViewer, DiseaseBadge, PestBadge, RecommendationList) in the PlantDetail page. Arrange them in a logical, visually appealing layout using Tailwind CSS. Ensure the page is responsive.
    - Where: Frontend/src/pages/PlantDetail.jsx
    - Goal: Complete plant detail page with all information displayed
    - Reference: [Tailwind CSS Layout](https://tailwindcss.com/docs/display)

14. **Test complete flow**
    - Action: Test the complete detail view flow by navigating to different plants from the dashboard. Verify that plant details are fetched correctly, all information displays properly, and error handling works for invalid IDs.
    - Where: Application end-to-end
    - Goal: Plant detail view works correctly end-to-end
    - Reference: Test with various plants and verify display

---

## Time estimate

- Expected time: 90-105 minutes

---

## Constraints

- Tech stack: React, FastAPI, SQLite, Firebase Authentication, Tailwind CSS, React Router DOM
- Not allowed: Public access to plant details, displaying other users' plants, complex image editing features
- Notes: Ensure plant details are only accessible to the owner. Keep the implementation focused on displaying information clearly. Delete and export functionality will be added in later issues.

**Note for Developers:**
The mentioned points, schemas, and structures are essential guidance. You are free to improve or add better structures if needed. Additions or deletions of files, components, or changes are allowed if they improve the project. The goal is to build a clean, complete project with good UI and proper validation.

---

## Dependencies

- Blocked by: [#10]
- Unblocks: [#12, #13]

---

## Definition of Done

- [ ] All Requirements / Acceptance criteria are met.
- [ ] Code follows project conventions.
- [ ] Plant detail page displays complete plant information.
- [ ] Backend endpoint returns only plants owned by authenticated user.
- [ ] All components display information correctly.
- [ ] Error handling works for invalid IDs and unauthorized access.
- [ ] Page is responsive and accessible.
- [ ] No console errors or warnings.

---

## Raise PR

- [ ] Create a feature branch following naming conventions.
- [ ] Commit in small logical chunks with clear messages.
- [ ] Ensure branch is up to date with `main`.
- [ ] Push branch and open a PR.
- [ ] Link the issue in the PR description.
- [ ] Add screenshots showing plant detail view.
- [ ] Test with various plants and document results.
- [ ] Request review from assigned reviewers.
