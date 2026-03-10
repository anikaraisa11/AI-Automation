# AI-Automation
# AI-Powered Lead Management System (n8n)

An automated workflow that captures leads, processes them with AI, and notifies the team in real-time.

## 🚀 Overview
This project automates the entire lead response journey. It validates emails, stores data in Airtable, generates personalized responses using OpenAI, and alerts the team via Slack.

## 🛠 Tech Stack
- **n8n** (Workflow Orchestration)
- **OpenAI API** (Personalized Email Generation)
- **Airtable** (CRM/Database)
- **Gmail** (Email Automation)
- **Slack** (Team Notifications)

## ⚙️ Key Features
- **Email Validation:** Uses Regex to filter out invalid entries.
- **Error Handling:** Built-in retry logic for API stability.
- **CRM Integration:** Seamless data sync with Airtable.

## 📸 Workflow Preview
![Workflow Screenshot](./your-image-link.png)

## 📥 How to Use
1. Install n8n.
2. Import the `workflow.json` file.
3. Replace the credentials for OpenAI, Airtable, and Gmail.
