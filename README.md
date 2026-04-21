# 📖 Overview
This project is an automated RAG-based Chatbot built on n8n. It allows an AI Agent to "read" and understand documents uploaded to a specific Google Drive folder by indexing them into a Pinecone vector database. When a user asks a question via the chat interface, the agent retrieves the most relevant information from those documents to provide accurate, grounded, and context-aware responses.

# 🛠 Tech Stack
**Automation:**  n8n

**LLM:** Google Gemini 1.5 Pro

**Vector Database:** Pinecone

**Embeddings:** OpenAI (text-embedding-3-small)

**Storage/Trigger:** Google Drive

**Memory:** n8n Window Buffer Memory

# ⚙️ Key Features
**Automated Ingestion:** Real-time monitoring of Google Drive; any new PDF or document is automatically processed and indexed.

**Intelligent Retrieval:** Uses vector similarity search to find exact paragraphs relevant to user queries.

**Conversational Memory:** The agent remembers previous turns in the conversation for a natural chat experience.

**Agentic Reasoning:** The AI determines when it needs to search the database and when it can answer directly.

# 🚀 How it Works
**Ingestion:** A file is uploaded to Google Drive. The Google Drive Trigger starts the flow, downloads the file, and passes it to the Default Data Loader.

**Vectorization:** The OpenAI Embeddings node converts the text into mathematical vectors, which are then stored in the Pinecone Vector Store.

**Querying:** A user sends a message through the Chat Trigger.

**Processing:** The AI Agent uses Gemini 1.5 Pro to analyze the intent. It calls the Pinecone Tool to fetch the "relative document" data.

**Response:** The agent combines the retrieved context with its reasoning to generate a final response to the user.

# 📥 Setup Instructions
**Credentials:** Set up API keys for OpenAI, Google Gemini, Pinecone, and OAuth2 credentials for Google Drive in n8n.

**Pinecone Index:** Create a serverless index in Pinecone with 1536 dimensions (to match OpenAI embeddings).

**Environment Variables:** Ensure the Description field in your Pinecone Tool node is set to: "Use this tool to retrieve information and data from the relative document stored in the vector database."

**Test Run:** Upload a sample PDF to your Drive folder and execute the ingestion branch to verify the data is indexed.

# 🔮 Future Enhancements
**Multi-Source Integration:** Adding web search capabilities via SerpApi.

**Feedback Loop:** Logging all queries and responses to Airtable or Google Sheets for quality monitoring.

**Advanced Filtering:** Implementing metadata filtering to allow the user to select specific documents to chat with.

# 👤 Author
Anika Raisa

**LinkedIn:** https://www.linkedin.com/in/anikaraisabd/ 
AI Automation Specialist & Architect of AI Systems
