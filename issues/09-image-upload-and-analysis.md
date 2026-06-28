# Image Upload and Analysis

**State:** open


---

## Summary

Implement the core feature of uploading plant photos and automatically analyzing them using Gemini Vision LLM. When a user uploads an image, it should be sent to the backend, analyzed by the LLM to identify diseases, pests, health issues, and generate treatment recommendations, then automatically saved as a plant profile. This combines frontend upload functionality with backend processing and LLM integration.

---

## Learning goals

- Learn how to handle file uploads in React and FastAPI
- Understand how to integrate vision-enabled LLMs using LangChain
- Practice implementing image analysis workflows
- Learn how to structure API endpoints that process files and call LLMs
- Understand how to automatically create database records after processing

---

## Requirements / Acceptance criteria

- [ ] Users can upload plant photos via file selection or camera capture
- [ ] Uploaded images are sent to the backend API endpoint
- [ ] Backend receives and stores uploaded image files
- [ ] Backend uses LangChain with Gemini Vision LLM to analyze the image
- [ ] LLM identifies plant diseases, pests, health issues, and provides treatment recommendations
- [ ] Analysis results are automatically saved to the database as a plant profile
- [ ] API returns complete plant data including analysis results
- [ ] Frontend displays success message and updates dashboard with new plant
- [ ] Loading states are shown during upload and analysis
- [ ] Error handling is implemented for upload and analysis failures

---

## Step-by-step guide

### Backend Implementation

1. **Set up database and models**
   - Action: Create the database structure to store plant profiles with analysis results. Design tables to store plant information including image path, disease identification, pest information, health issues, and treatment recommendations. Only essential fields are suggested; you may modify or improve the models as needed.
   - Where: Backend/database/ or Backend/models/
   - Goal: Have the necessary data layer ready before implementing the endpoint
   - Reference: [SQLite Python Documentation](https://docs.python.org/3/library/sqlite3.html)

2. **Create image storage directory**
   - Action: Set up a directory structure to store uploaded plant images. Organize images in a way that makes them easy to retrieve and serve later. Consider organizing by user or plant ID.
   - Where: Backend/uploads/ or Backend/static/images/
   - Goal: A location ready to store uploaded plant images
   - Reference: [Python File Operations](https://docs.python.org/3/tutorial/inputoutput.html)

3. **Set up LangChain with Gemini Vision**
   - Action: Configure LangChain to work with Gemini Vision LLM for image analysis. Set up the necessary imports and configuration to use vision-enabled LLM capabilities.
   - Where: Backend/services/llm_service.py or similar
   - Goal: LangChain is configured and ready to analyze images
   - Reference: [LangChain Gemini Integration](https://python.langchain.com/docs/integrations/llms/google_generative_ai)

4. **Create image analysis function**
   - Action: Build a function that takes an image file and uses LangChain with Gemini Vision LLM to analyze it. The LLM should identify diseases, detect pests, identify health issues, and generate personalized treatment recommendations. Structure the prompt to get consistent JSON responses.
   - Where: Backend/services/analysis_service.py or similar
   - Goal: A function that analyzes plant images and returns structured results
   - Reference: [LangChain Vision Models](https://python.langchain.com/docs/modules/model_io/models/vision)

5. **Create upload and analysis endpoint**
   - Action: Build a POST endpoint that accepts image file uploads. The endpoint should save the image, call the analysis function, save the results to the database as a plant profile, and return the complete plant data including analysis results.
   - Where: Backend/main.py or Backend/routes/plants.py
   - Goal: An API endpoint that handles upload, analysis, and auto-save in one step
   - Reference: [FastAPI File Uploads](https://fastapi.tiangolo.com/tutorial/request-files/)

6. **Add authentication protection**
   - Action: Protect the upload endpoint so only authenticated users can access it. Verify Firebase authentication tokens sent from the frontend to ensure the user is authenticated.
   - Where: Backend/main.py or authentication middleware
   - Goal: Upload endpoint is protected and requires authentication
   - Reference: [FastAPI Security](https://fastapi.tiangolo.com/tutorial/security/)

### Frontend Implementation

7. **Create ImageUploadModal component**
   - Action: Build a modal component that allows users to upload plant photos. Include options for file selection and camera capture. Display the selected image preview before upload.
   - Where: Frontend/src/components/ImageUploadModal.jsx
   - Goal: A modal interface for uploading plant images
   - Reference: [React File Input](https://react.dev/reference/react-dom/components/input#file-input)

8. **Implement file upload handler**
   - Action: Create a function that handles the image upload process. Convert the selected file to FormData, send it to the backend API endpoint, and handle the response. Show loading state during upload and analysis.
   - Where: Frontend/src/components/ImageUploadModal.jsx
   - Goal: Image files are successfully uploaded to the backend
   - Reference: [Fetch API FormData](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

9. **Connect UploadButton to modal**
   - Action: Update the UploadButton component to open the ImageUploadModal when clicked. Manage the modal's open/close state appropriately.
   - Where: Frontend/src/components/UploadButton.jsx and Dashboard.jsx
   - Goal: Clicking upload button opens the upload modal
   - Reference: [React State Management](https://react.dev/learn/state-a-component-s-memory)

10. **Handle upload success**
    - Action: When the upload and analysis complete successfully, close the modal, display a success message, and refresh the plant list on the dashboard to show the new plant. Handle any errors that occur during the process.
    - Where: Frontend/src/components/ImageUploadModal.jsx and Dashboard.jsx
    - Goal: Successful uploads update the dashboard with new plant data
    - Reference: [React Error Handling](https://react.dev/learn/conditional-rendering)

11. **Test complete flow**
    - Action: Test the complete upload and analysis flow with various plant images. Verify that images are uploaded correctly, analysis is performed, plant profiles are created, and the dashboard updates appropriately.
    - Where: Application end-to-end
    - Goal: Complete upload and analysis feature works correctly
    - Reference: Test with different plant images and verify results

---

## Time estimate

- Expected time: 90-120 minutes

---

## Constraints

- Tech stack: React, FastAPI, SQLite, LangChain, Gemini Vision LLM, Tailwind CSS
- Not allowed: OCR libraries (PyTesseract, Tesseract), specialized image classification models, Docker, cloud storage (use local file system)
- Notes: Use LangChain with Gemini Vision LLM for all image analysis. Do not use OCR libraries. Store images locally on the file system. The entire process (upload, analyze, save) happens in one API call.

**Note for Developers:**
The mentioned points, schemas, and structures are essential guidance. You are free to improve or add better structures if needed. Additions or deletions of files, components, or changes are allowed if they improve the project. The goal is to build a clean, complete project with good UI and proper validation.

---

## Dependencies

- Blocked by: [#08]
- Unblocks: [#10]

---

## Definition of Done

- [ ] All Requirements / Acceptance criteria are met.
- [ ] Code follows project conventions.
- [ ] Image upload works correctly from frontend to backend.
- [ ] LLM analysis successfully identifies diseases, pests, health issues, and provides recommendations.
- [ ] Plant profiles are automatically created after analysis.
- [ ] Loading states are displayed during processing.
- [ ] Error handling works for all failure scenarios.
- [ ] No console errors or warnings.

---

## Raise PR

- [ ] Create a feature branch following naming conventions.
- [ ] Commit in small logical chunks with clear messages.
- [ ] Ensure branch is up to date with `main`.
- [ ] Push branch and open a PR.
- [ ] Link the issue in the PR description.
- [ ] Add screenshots showing upload and analysis flow.
- [ ] Test with various plant images and document results.
- [ ] Request review from assigned reviewers.
