# 🤖 AI-Powered Career Assistant (Agentic Workflow)
An autonomous agentic system that transforms raw resume data and job descriptions into professional application materials. Built with a focus on multi-agent orchestration, this tool generates a tailored Professional Summary and a high-impact Cover Letter, delivering them via email and a real-time web interface.

# 🌟 Overview
This project solves the "blank page" problem for job seekers. By integrating a React-based frontend (Lovable) with an advanced n8n backend, the system automates the entire document creation process using Google Gemini’s generative capabilities.

# 🚀 Key Features
**Multi-Agent Orchestration:** Separate AI agents for specialized tasks (Summary vs. Cover Letter) ensuring high-quality, focused outputs.
**PDF Intelligence:** Automated extraction of text from uploaded PDF resumes.
**Dynamic Document Generation:** Real-time HTML-to-PDF conversion with custom CSS styling.
**Automated Delivery:** Instant email delivery via Gmail API and direct binary file response to the web application.

# 🛠️ Tech Stack
Component                   Technology
Orchestration               n8n (Low-code workflow automation)
Large Language Model        Google Gemini (Agentic reasoning)
Frontend                    Lovable (React / Vite)
PDF Processing              PDFMunk / n8n Binary Tools
Communication               Gmail API

# 🏗️ Workflow Architecture 
The system follows a linear but complex 8-step pipeline:
1.Webhook Trigger: Receives multipart form data (Name, Email, Job Post, and PDF File).
2.PDF Extraction: Converts the binary resume into a structured JSON text string.
3.Agent 1 (Professional Summary): Analyzes the resume against the job post to create a 3-sentence hook.
4.Agent 2 (Cover Letter): Drafts a persuasive, 3-paragraph letter tailored to the specific role.
5.HTML Templating: A JavaScript node injects the AI outputs into a custom-styled HTML/CSS template.
6.PDF Generation: Converts the HTML into a professional A4 document.
7.Gmail Integration: Sends the document directly to the user's inbox.
8.Binary Response: Returns the PDF file to the frontend for immediate download.

# 🔮 Future Enhancements
While the current MVP successfully automates the core application process, the following features are planned for future iterations to increase the system's "Agentic" intelligence:

1.RAG Integration (Vector Database): Implement Pinecone or Supabase Vector to store and retrieve the user’s full career history, allowing the AI to pick the most relevant projects for different job types.

2.LinkedIn Web Scraping: Add a node to automatically scrape the LinkedIn profile of the Hiring Manager (using Apify or ScrapingBee) to personalize the cover letter's tone even further.

3.Multi-Format Export: Expand the document engine to support .docx and Google Docs formats using the CloudConvert API.

4.Human-in-the-Loop (HITL): Integrate an n8n Wait Node that sends a Slack/Discord notification with a draft for approval before the final PDF is generated and emailed.

5.Skill Gap Analysis: Add a third AI Agent to identify missing keywords in the resume compared to the job post and provide suggestions on what skills the user should learn next.

# 💻 Code Highlight:
Dynamic TemplatingThe system uses a custom JavaScript engine to ensure the final PDF looks polished and professional:JavaScriptconst htmlTemplate = `
  <style>
    body { font-family: 'Arial'; line-height: 1.6; color: #333; }
    .header { border-bottom: 2px solid #4A90E2; padding-bottom: 10px; }
    .section-title { color: #4A90E2; font-weight: bold; }
  </style>
  <div class="header"><h1>Application Materials</h1></div>
  <div class="section-title">SUMMARY</div>
  <div>${resumeSummary}</div>
  <div class="section-title">COVER LETTER</div>
  <div>${coverLetter}</div>
`;

# 📈 Impact
Time Savings: Reduces the average application prep time from 45 minutes to 15 seconds.
Consistency: Maintains a professional tone and layout across all generated documents.
ATS Optimization: AI agents are specifically prompted to include relevant keywords from the job description.

# 👩‍💻 About the Author
Anika Raisa AI Automation Specialist Expert in building agentic workflows, RAG systems, and autonomous business processes using n8n, Langflow, and Zapier.How to Run ThisImport the workflow.json into your n8n instance.Configure your Google Gemini and Gmail credentials.Update the Webhook URL in your Lovable frontend.Add your PDFMunk API Key to the HTML to PDF node.
