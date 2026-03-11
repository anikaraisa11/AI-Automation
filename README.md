# AI-Automation
# 🚀 AI-Powered Career Roadmap Generator
An automated system built with n8n that captures user data, stores it in Airtable, and leverages Google Gemini AI to generate personalized, professional career roadmaps delivered instantly via a dynamic web interface.

# 📋 Project Overview
This project automates the career consultancy process. By capturing a user's specific interests and target profession, the system creates a bespoke learning path. This eliminates the manual effort of researching career steps and provides the user with an immediate, actionable PDF-ready roadmap.

# The Workflow
Data Capture: User submits a form (Name, Email, Phone, Profession, Interests).

Lead Management: Data is instantly synced to an Airtable base for CRM purposes.

AI Analysis: An n8n AI Agent (powered by Gemini) processes the profession and interests.

Content Generation: Gemini generates a multi-step, detailed career roadmap.

Data Enrichment: The generated roadmap is updated back into the specific Airtable record.

Instant Delivery: The final node triggers a Form Ending page, displaying the roadmap to the user in real-time.

# 🛠️ Tech Stack
Automation: n8n.io

Database: Airtable

LLM: Google Gemini

Logic: JavaScript (via n8n nodes)

# ⚙️ Setup Instructions
1. Airtable Configuration
Create a base with a table containing the following fields:

Name (Single line text)

Email (Email)

Phone (Phone number)

Profession (Single select)

Interests (Long text)

Roadmap (Long text) — This is where the AI will write the output.

2. n8n Workflow Setup
Form Trigger: Create the input fields matching your Airtable columns. Set Response Mode to When Last Node Finishes.

Airtable Node: Set action to Create to log the initial user submission.

AI Agent Node: * Connect the Google Gemini Chat Model.

Use a prompt like: "Generate a detailed career roadmap for a user interested in {{profession}}. Their specific interests are {{interest}}."

Airtable Update Node: Use the Record ID from the first Airtable node to update the Roadmap field with the AI's output.

Form Node (Ending): Set the Page Type to Form Ending. Use expressions to display the {{roadmap}} data.

# 🚀 Future Enhancements
[ ] PDF Generation: Automatically convert the roadmap into a stylized PDF for download.

[ ] Multi-Language Support: Use the AI to detect user language and provide the roadmap in Bengali or English.

[ ] Email Backup: Send a copy of the roadmap via SendGrid or Gmail for long-term access.

# 👤 Author
Anika Raisa

LinkedIn: https://www.linkedin.com/in/anikaraisabd/

GitHub: https://github.com/anikaraisa11

Project Goal: Exploring the intersection of AI Automation and Professional Development.
