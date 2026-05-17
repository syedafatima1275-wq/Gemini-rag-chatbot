# GenAI Domain Assistant Chatbot

A domain-specific chatbot that answers questions using **Retrieval-Augmented Generation (RAG)** with **Google Gemini 2.5 Flash**.  
It ensures responses are grounded only in your provided documents, reducing hallucinations.

Built with **Python, LangChain, and Google Gemini**.

---

## Features

- **Document Ingestion**  
  Load HR policy PDFs and text files.

- **Text Chunking**  
  Splits documents into optimized chunks with configurable size and overlap.

- **RAG Pipeline**  
  Retrieves relevant context and generates grounded answers using Gemini.

- **Keyword Retrieval (Baseline)**  
  Simple keyword-based search for testing without embeddings.

- **Comparison Mode**  
  Compare answers with and without RAG to observe improvements.

- **Debugging Support**  
  View retrieved chunks to verify what the model is using.

---

## Project Structure
genai-hr-assistant/
│
├── data/
│ # HR policy PDFs or TXT files
│
├── notebooks/
│ └── rag_hr_assistant.ipynb # Main RAG pipeline notebook
│
├── README.md
└── requirements.txt

---

## Requirements
google-generativeai
langchain
langchain-community
pypdf
kaggle_secrets

---

## Setup Instructions

### 1. Add Google Gemini API Key

**In Kaggle Notebooks:**
- Go to *Add-ons > Secrets*
- Add secret:
  GEMINI_API_KEY
  
**Locally:**
```python
import os
os.environ["GEMINI_API_KEY"] = "your_api_key"
2. Add Documents

Place all HR policy files inside:
data/
Limitations
Keyword-based retrieval only
Simple search does not understand synonyms (e.g., "maternity leave" vs "parental leave").
Limited to provided data
The chatbot cannot answer outside uploaded documents.
No conversation memory
Each query is independent.
Future Improvements
Replace keyword search with FAISS + embeddings
Add semantic search using HuggingFace embeddings
Implement chat history for multi-turn conversations
Deploy using Streamlit or FastAPI
Goal

To build a safe, grounded, and domain-specific AI assistant that only answers from trusted HR documents using RAG.
