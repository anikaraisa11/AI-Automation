# AI-Powered PDF Query Assistant (RAG Pipeline)

A robust Retrieval-Augmented Generation (RAG) system built using **Langflow**, **DataStax Astra DB**, and **OpenAI**. This project allows users to upload complex PDF documents and interact with the content through a natural language chat interface.

## 🚀 How It Works

The project is divided into two core phases:

### 1. Ingestion Phase (Data Pipeline)
* **Document Loading:** Reads and parses PDF files.
* **Text Splitting:** Breaks down the document into manageable chunks to maintain context and stay within token limits.
* **Vector Embeddings:** Utilizes `text-embedding-3-small` from OpenAI to convert text into high-dimensional vectors.
* **Vector Storage:** Stores these embeddings in **Astra DB** (powered by Apache Cassandra) for high-speed similarity searches.

### 2. Retrieval Phase (Chat Pipeline)
* **Semantic Search:** When a user asks a question, the system generates an embedding for the query.
* **Context Retrieval:** It searches Astra DB for the most relevant document chunks.
* **LLM Processing:** The retrieved context and the user question are sent to **GPT-4o-mini**, which generates a precise, context-aware answer.

## 🛠️ Tech Stack
* **Orchestration:** Langflow
* **Database:** Astra DB (Vector Store)
* **AI Models:** OpenAI (GPT-4o-mini & Embeddings)
* **Infrastucture:** Docker
