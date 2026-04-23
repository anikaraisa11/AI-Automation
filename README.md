# AI Prescription Analyzer 🏥
A full-stack mobile solution that uses Multi-Model AI (GPT-4o & Gemini) to interpret, summarize, and explain handwritten or printed doctor prescriptions.

# 📝 Overview
Deciphering medical prescriptions can be stressful and error-prone for patients. The **AI Prescription Analyzer** bridges this gap by providing an intelligent "translation layer." Users can simply snap a photo of their prescription, and within seconds, receive a structured breakdown of medications, dosages, and critical warnings.

The project uses a decoupled architecture: a high-performance React Native (Expo) frontend for the user interface and a robust n8n-based backend for AI orchestration.

# 📱 The Android App (React Native / Expo)
The mobile frontend provides a seamless interface for users to input medical data and view AI-generated insights.

**Core Functionalities**
**Multi-Modal Input:** Users can capture a new photo via the Camera, select an existing file from the Gallery, or Type Text manually.

**State Management:** Uses a loading state (spinner) to manage the asynchronous "Handshake" with the backend.

**Formatted Display:** The app parses JSON responses from the backend to display a structured "Summary Card" with distinct sections for Medicines, Warnings, and Confidence scores.

# Technical Working (The Handshake)
When the "Analyze" button is pressed, the app performs the following:

**1.Binary Preparation:** Images are converted into a multipart/form-data payload.

**2.API Communication:** A POST request is dispatched to the n8n Webhook.

  *Text Path:* Sends a JSON body: { "type": "text", "user_text": "..." }.

  *Image Path:* Sends a form-data body where the file is attached under the key image.

**3.Result Rendering:** The app listens for a successful HTTP 200 response and maps the summary_text directly to the UI.

# ⚙️ Backend Logic (n8n Workflow)
The backend is a sophisticated automation pipeline built in n8n that intelligently routes and processes data using specialized AI models.

**1. Trigger & Routing (The Switch)**
The Webhook Node receives the incoming request. A Switch Node immediately evaluates the input:

If type == text: Routes to the "User Query" branch.

If type == image: Routes to the "Analyze Image" branch.

**2. Vision Intelligence (GPT-4o-mini)**
The Analyze Image Node uses GPT-4o-mini to perform high-accuracy OCR.

Goal: To extract "messy" handwritten medication names, dosages, and durations.

Output: Structured JSON containing the raw medical data found in the image.

**3. Contextual Reasoning (Gemini 1.5 Flash)**
The data from both branches merges into the AI Agent (Gemini).

*Role:* Medical Scribe & Translator.

*Logic:* It combines the extracted OCR text with medical context. It converts technical jargon (e.g., "1+0+1") into human-readable instructions ("Twice daily: Morning and Night").

*Formatting:* It applies Markdown and ensures the response is strictly structured for the mobile UI.

**4. Response Delivery**
The Respond to Webhook node closes the loop, returning the AI's final brain-work back to the mobile app in under 5-10 seconds.

# ✨ Key Features
**Hybrid Input System:** Support for real-time camera capture, gallery image uploads, and manual text entry.

**Dual-Model Intelligence**: * OpenAI GPT-4o: Handles high-precision OCR and visual feature extraction.

**Google Gemini:** Acts as the medical scribe to format and explain instructions.

**Intelligent Routing:** A backend switch automatically distinguishes between text and image data to optimize processing paths.

**Multi-Language Support:** Capable of interpreting medical shorthand and responding in human-readable formats (English/Bangla).

**Real-time Processing:** Visual feedback via a loading system while the AI analyzes the data.

# ⚙️ How It Works
**1. The Mobile Layer (Frontend)**
Built with *React Native and Expo*, the app handles the user's media. When an image is selected, the app converts the file into a multipart/form-data stream. This is crucial as it sends the raw binary data rather than a text-based reference, allowing the AI to "see" the actual pixels of the handwriting.

**2. The Logic Layer (Backend)**
Hosted on n8n, the workflow follows a 4-step logic:

**i. Receive:** The Webhook node accepts the incoming data.

**ii. Route:** A Switch node checks the type parameter.

  *Image path:* Sends the binary to GPT-4o.

  *Text path:* Sends the string directly to the Agent.

**iii. Analyze:** GPT-4o performs Vision-to-Text extraction to "read" the handwriting.

**iv. Refine:** The Gemini Agent takes the raw text, cross-references medical context, and produces a JSON object containing the summary and warnings.

**3. The Response Layer**
The backend sends a structured JSON response back to the app, which then parses and displays the data in organized "Medicine Cards."

# 🚀 Setup Instructions
**Frontend (Mobile)**
1.Install dependencies: npm install

2.Ensure you have Expo Go installed on your Android/iOS device.

3.Configure your Webhook URL in the api.js or logic configuration:
const WEBHOOK_URL = 'YOUR_N8N_URL_HERE';

4.Start the app: npx expo start

**Backend (n8n)**
1.Import the provided .json workflow into your n8n instance.

2.Add your OpenAI and Google Gemini API credentials.

3.Set the Webhook node to POST method and enable Binary Data.

4.Update the Analyze Image node to look for the property name image.

# 🛠️ Future Enhancements
**Medication Reminders:** Add a feature to automatically set local push notifications for the identified dosage times.

**Local History:** Implement AsyncStorage to allow users to save and view past prescription scans offline.

**PDF Export:** Allow users to download the AI summary as a clean PDF for sharing with other doctors.

**Drug Interaction Check:** Integrate a secondary medical API to flag potential harmful interactions between the identified medications.

**Voice Output:** Use Text-to-Speech (TTS) to read the instructions aloud for visually impaired users.

# ⚠️ Safety & Disclaimer
This app is an AI-assisted tool meant for educational and informational purposes only. It does not provide medical advice. All AI-generated summaries should be cross-referenced with a qualified healthcare professional or pharmacist before starting any medication.
