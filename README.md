# 🧾 Autonomous Invoice Processing & Accounting AI Agent

An enterprise-grade, zero-touch automation system built on **n8n** that intercepts incoming financial documents via email, extracts and validates critical metadata using **OpenAI Large Language Models (LLMs)** with structured JSON parsing, and synchronizes records seamlessly across cloud storage and relational databases (**Notion**).

The system features intelligent quality gates to auto-reject invalid files, ensuring an audit-ready, hallucination-free financial data ledger without manual intervention.

---

## 🏗️ Overview

Manual invoice processing is a classic operational bottleneck prone to human error, delayed entries, and scattered file management. This project completely automates the pipeline by linking communication channels, secure cloud storage, artificial intelligence, and database ledgers into a single cohesive ecosystem. 

By utilizing **Agentic workflows** and **Structured Output Parsers**, the system guarantees that unstructured documents (like raw PDFs or text extracts) are converted into highly accurate, structured data variables before ever interacting with business-critical databases.

---

## 🛠️ Tech Stack

* **Orchestration & Workflow Automation:** [n8n](https://n8n.io/) (Advanced Agentic Framework)
* **Artificial Intelligence & LLM Layer:** [OpenAI](https://openai.com/) (GPT models via native Chat Model nodes)
* **AI Tooling & Formatting:** LangChain / n8n Structured Output Parsers
* **Document Parsing Engine:** Native Binary Extract PDF (OCR / Text Extraction)
* **Cloud Storage:** Google Drive API
* **Communication & Ingestion:** Gmail API
* **Data Ledger & ERP:** Notion API

---

## 🌟 Key Features

* **Zero-Touch Automated Ingestion:** Continuous monitoring of financial inbox streams to capture billing documents immediately upon arrival.
* **Deterministic AI Extraction:** Solves LLM unpredictability by enforcing strict JSON formatting constraints using Structured Output Parsers, ensuring schema compliance before database writing.
* **Multi-Stage Validation Gate:** Uses a dedicated conditional logic router (`If` node) to filter out spam, corrupted data, or non-invoice attachments before they hit critical accounting layers.
* **Self-Cleaning Storage Lifecycle:** Automatically purges unverified or failed files from cloud drives to maintain minimal storage footprints and lower compliance risks.
* **Advanced Agentic Routing:** Leverages an interactive AI Agent node with custom memory configurations to categorize expenses, tax brackets, or vendor codes dynamically.

---

## ⚙️ How It Works

### Phase 1: Ingestion & Payload Initialization
* The **Search Invoices (Gmail Trigger)** polls the specified inbox matching filter parameters (e.g., `has:attachment filename:pdf invoice`).
* An **Edit Fields** node normalizes the attachment properties and prepares internal variables.
* The payload passes through a **Split Out** and **Merge** block, isolating multiple attachments inside a single email and queuing them sequentially for atomic, error-isolated processing.

### Phase 2: Cloud Ingestion & Raw Extraction
* The workflow pushes the binary attachment to a secure landing folder via **Upload File (Google Drive)**. 
* It instantly downloads it locally back to the n8n execution environment via **Download File** to generate a clean binary buffer.
* The **Extract From File** node targets the PDF binary, stripping text, layout strings, and tables into a single plaintext variable.

### Phase 3: LLM Parsing & Quality Assurance Gate
* The extracted text is injected into the **Basic LLM Chain**. Assisted by an **OpenAI Chat Model** and a **Structured Output Parser**, it forces the LLM to output a strict schema:
  ```json
  {
    "is_invoice": true,
    "invoice_id": "INV-2026-004",
    "vendor_name": "Acme Industrial Corp",
    "total_amount": 1450.00,
    "currency": "USD",
    "due_date": "2026-06-30"
  }
  An If Router evaluates the boolean outcome:

# False Branch:
The file is not an invoice or extraction failed. The flow moves to Delete a File (Google Drive), removing the record from cloud storage and ending execution.

# True Branch: 
The invoice is valid. Execution routes forward to the agentic layer.

### Phase 4: Agentic Contextual Enrichment & Database Logging
AI Agent 1 intercepts the validated schema. It utilizes conversational memory tools to cross-reference vendors and tag transactions dynamically into structural bookkeeping types.

Edit Fields 1 reformats the final dictionary arrays into exact database properties.

Create a Database Page (Notion) maps the payload attributes directly into your financial ledger tables.

Send a Message (Gmail) drafts and dispatches an automated notification summary back to the accounting or operations team confirming ledger entry creation.

## 🚀 Setup Instructions
Prerequisites
n8n Instance: Self-hosted (Docker/NPM) or n8n Cloud account.

API Credentials:

OpenAI API Key (with access to GPT-4o models).

Google Workspace Account (OAuth2 Credentials configured via Google Cloud Console with Gmail and Google Drive API scopes enabled).

Notion Integration Token (with read/write workspace access to your target database).

Workflow Deployment
Import the Workflow:

Download the workflow JSON file from this repository.

In your n8n dashboard, click Workflows > Add Workflow > Import from File... and upload the JSON.

Configure Node Credentials:

Open the Search Invoices and Send a Message nodes, select your Gmail credential profile, or follow the OAuth2 setup wizard.

Open the Upload File, Download File, and Delete a File nodes to bind your Google Drive credentials.

Attach your OpenAI API key to both OpenAI Chat Model nodes inside the chain and agent configurations.

Connect the Create a database page node to your Notion integration account and pick your target database workspace.

Set Up Database Properties: Ensure your target Notion Database table contains the following matching column schemas:

Invoice ID (Title/Text)

Vendor Name (Select / Text)

Total Amount (Number)

Due Date (Date)

Status (Status / Select)

Activate: Set the workflow toggle from Inactive to Active in the top right corner.

## 🔮 Future Enhancements
*Line-Item Breakdown Parsing:* Upgrade the structured output schemas to capture array matrices of line items inside an invoice rather than just the high-level metadata.

*Automated Payment Gateway Trigger:* Integrate Stripe, PayPal, or Wise API nodes directly after the Notion logging step to queue automated bank transfers or invoice approvals.

*Multi-Currency Conversion Hook:* Embed a live Exchange Rate API node to auto-convert foreign currencies to a default base currency before pushing rows to Notion.

*Human-in-the-Loop Slack Escalations:* Reroute the False logic path to send an interactive Slack button to operations managers, allowing manual overrules or text corrections for blurred or hard-to-read invoices.

*Vector Embeddings Auditing:* Add an vector database ingestion node (e.g., Pinecone or Qdrant) to create searchable embeddings of historical invoices for cross-referencing past billing patterns.
