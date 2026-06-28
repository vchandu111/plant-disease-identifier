# Export to Markdown

**State:** open


---

## Summary

Implement functionality to export plant analysis results as a Markdown file. Create a backend endpoint that generates a well-formatted Markdown document containing all plant analysis information and a frontend button that triggers the download.

---

## Learning goals

- Learn how to generate formatted text files in the backend
- Understand how to structure Markdown documents programmatically
- Practice implementing file download functionality in React
- Learn how to format complex data into readable documents
- Understand how to handle file downloads from APIs

---

## Requirements / Acceptance criteria

- [ ] Backend endpoint generates Markdown file with plant analysis
- [ ] Markdown includes plant image reference, disease, pests, health issues, and recommendations
- [ ] Markdown is well-formatted with proper headers and structure
- [ ] Frontend export button is accessible from plant detail page
- [ ] Clicking export button downloads the Markdown file
- [ ] Downloaded file has appropriate name (e.g., plant-analysis-[id].md)
- [ ] File content is readable and properly formatted
- [ ] Error handling is implemented for export failures
- [ ] Loading state is shown during file generation

---

## Step-by-step guide

### Backend Implementation

1. **Create export endpoint**
   - Action: Build a GET endpoint that generates a Markdown file for a specific plant. Retrieve the plant data from the database, format it as Markdown, and return it as a downloadable file response.
   - Where: Backend/main.py or Backend/routes/plants.py
   - Goal: An API endpoint that generates Markdown files
   - Reference: [FastAPI File Responses](https://fastapi.tiangolo.com/tutorial/custom-response/)

2. **Implement Markdown generation**
   - Action: Create a function that takes plant data and formats it into a well-structured Markdown document. Include headers for different sections, format lists for recommendations, and include all analysis information.
   - Where: Backend/services/export_service.py or similar
   - Goal: Plant data is formatted as readable Markdown
   - Reference: [Markdown Syntax Guide](https://www.markdownguide.org/basic-syntax/)

3. **Structure Markdown content**
   - Action: Organize the Markdown document with clear sections for plant information, disease identification, pest information, health issues, and treatment recommendations. Use appropriate Markdown formatting (headers, lists, emphasis).
   - Where: Backend/services/export_service.py or Markdown generation logic
   - Goal: Markdown document is well-organized and readable
   - Reference: [Markdown Formatting](https://www.markdownguide.org/cheat-sheet/)

4. **Set file response headers**
   - Action: Configure the API response to indicate it's a file download. Set appropriate content type (text/markdown) and content disposition headers to trigger browser download with a proper filename.
   - Where: Backend/main.py or response configuration
   - Goal: Browser recognizes response as downloadable file
   - Reference: [FastAPI Response Headers](https://fastapi.tiangolo.com/advanced/response-headers/)

5. **Add authorization check**
   - Action: Ensure the export endpoint verifies that the plant belongs to the authenticated user before generating the export. Return an error if the user tries to export a plant that doesn't belong to them.
   - Where: Backend/main.py or authorization logic
   - Goal: Users can only export their own plants
   - Reference: [FastAPI Security](https://fastapi.tiangolo.com/tutorial/security/)

### Frontend Implementation

6. **Create export handler function**
   - Action: Build a function that calls the export API endpoint and handles the file download. Use the Fetch API to download the file and trigger browser download.
   - Where: Frontend/src/services/api.js or Frontend/src/utils/api.js
   - Goal: A reusable function to export plants as Markdown
   - Reference: [Fetch API Blob Handling](https://developer.mozilla.org/en-US/docs/Web/API/Blob)

7. **Create ExportButton component**
   - Action: Build a button component that triggers the export functionality. Style it appropriately and position it on the plant detail page near other action buttons.
   - Where: Frontend/src/components/ExportButton.jsx
   - Goal: Export button is visible and accessible
   - Reference: [Tailwind CSS Buttons](https://tailwindcss.com/docs/buttons)

8. **Implement download handling**
   - Action: When the export button is clicked, call the export API function, create a blob from the response, and trigger a browser download. Set an appropriate filename for the downloaded file.
   - Where: Frontend/src/components/ExportButton.jsx
   - Goal: Markdown file downloads correctly when button is clicked
   - Reference: [JavaScript Blob Download](https://developer.mozilla.org/en-US/docs/Web/API/Blob)

9. **Add loading state**
   - Action: Show a loading indicator while the Markdown file is being generated and downloaded. Disable the export button during the process to prevent multiple requests.
   - Where: Frontend/src/components/ExportButton.jsx
   - Goal: Users see feedback during export process
   - Reference: [React State Management](https://react.dev/learn/state-a-component-s-memory)

10. **Handle errors**
    - Action: Implement error handling for export failures. Display appropriate error messages if export fails due to network issues, authorization problems, or other errors.
    - Where: Frontend/src/components/ExportButton.jsx
    - Goal: Errors are handled gracefully with user feedback
    - Reference: [React Error Handling](https://react.dev/learn/conditional-rendering)

11. **Add export button to detail page**
    - Action: Include the ExportButton component in the PlantDetail page. Position it alongside other action buttons in a logical location.
    - Where: Frontend/src/pages/PlantDetail.jsx
    - Goal: Export button is accessible from plant detail page
    - Reference: [React Component Composition](https://react.dev/learn/passing-props-to-a-component)

12. **Test export functionality**
    - Action: Test the complete export flow by exporting various plants. Verify that Markdown files are generated correctly, downloaded properly, contain all information, and are well-formatted and readable.
    - Where: Application end-to-end
    - Goal: Export functionality works correctly end-to-end
    - Reference: Test with various plants and verify Markdown content

---

## Time estimate

- Expected time: 75-90 minutes

---

## Constraints

- Tech stack: React, FastAPI, SQLite, Firebase Authentication, Tailwind CSS
- Not allowed: Complex document generation libraries, PDF generation, multiple export formats
- Notes: Focus on generating simple, well-formatted Markdown files. Keep the implementation straightforward. The Markdown should be readable and include all analysis information.

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
- [ ] Markdown files are generated correctly with all plant information.
- [ ] Files download successfully with appropriate names.
- [ ] Markdown content is well-formatted and readable.
- [ ] Export endpoint only allows export of user's own plants.
- [ ] Loading states and error handling work correctly.
- [ ] No console errors or warnings.

---

## Raise PR

- [ ] Create a feature branch following naming conventions.
- [ ] Commit in small logical chunks with clear messages.
- [ ] Link the issue in the PR description.
- [ ] Add screenshots showing export functionality.
- [ ] Include a sample exported Markdown file in the PR.
- [ ] Test export with various plants and document results.
- [ ] Request review from assigned reviewers.
