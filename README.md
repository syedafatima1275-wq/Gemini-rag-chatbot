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
# Week 11 - Vector Database and Semantic Search

## Overview
This lab focuses on **Semantic Search, Embeddings, Vector Databases, and Retrieval-Augmented Generation (RAG)** using **Gemini API** and **ChromaDB**.

The goal is to move beyond traditional keyword-based search and implement a semantic search system that understands the **meaning and context** of text through embeddings.

---

## Objectives
- Understand **text embeddings**
- Generate embeddings using **Google Gemini API**
- Calculate similarity using **Cosine Similarity**
- Store vector embeddings in **ChromaDB**
- Implement **Semantic Search**
- Build a simple **RAG (Retrieval-Augmented Generation) Pipeline**
- Compare **Keyword Search vs Semantic Search**

---

## Technologies Used
- **Python**
- **Google Gemini API**
- **ChromaDB**
- **LangChain**
- **NumPy**
- **LangChain Text Splitters**
- **Google Generative AI SDK**

---

## Project Structure

### Part 1: Embeddings
This section introduces embeddings and how text can be converted into numerical vector representations.

#### Task 1.1: Generate Embeddings
- Install required libraries
- Configure Gemini API
- Generate embeddings for text using Gemini models

#### Task 1.2: Calculate Similarity
- Implement **Cosine Similarity**
- Compare semantic closeness between vectors

---

### Part 2: ChromaDB Setup

#### Task 2.1: Initialize ChromaDB
- Create a vector database
- Configure document storage

#### Task 2.2: Load and Index Documents
- Split text into chunks
- Convert chunks into embeddings
- Store embeddings in ChromaDB for retrieval

---

### Part 3: Semantic RAG

#### Task 3.1: Test Vector Search
- Perform semantic search queries
- Retrieve contextually relevant documents

Example Queries:
- `time off policy`
- `vacation`
- `WFH guidelines`
- `remote work`
- `maternity leave`
- `parental leave`

#### Task 3.2: Build Semantic RAG Pipeline
- Retrieve relevant context using vector search
- Send retrieved context to Gemini
- Generate intelligent responses

---

## Keyword Search vs Semantic Search

### Keyword Search
- Matches exact words
- Limited understanding of meaning
- Fails with synonyms or paraphrased queries

### Semantic Search
- Understands intent and meaning
- Uses embeddings and vector similarity
- Retrieves contextually relevant results even with different wording

Example:
A query like **"vacation"** can still retrieve information about **"time off policy"**, even if exact words do not match.

---

## Installation

Install dependencies:

```bash
pip install chromadb
pip install langchain-community
pip install langchain-text-splitters
pip install google-generativeai
pip install google-genai
pip install langchain-google-genai
from kaggle_secrets import UserSecretsClient

user_secrets = UserSecretsClient()
api_key = user_secrets.get_secret("Gemini_API_Key")
Learning Outcomes
After completing this lab, we will be able to:

Understand how embeddings work
Use vector databases for information retrieval
Implement semantic search systems
Build a basic RAG application
Compare keyword-based and semantic search approaches
Conclusion
This lab demonstrates how Semantic Search powered by embeddings and vector databases is more intelligent than traditional keyword matching. By integrating Gemini API with ChromaDB, a simple but effective RAG pipeline was developed to retrieve meaningful context and generate relevant responses.
## Author
**Syeda Fatima Zahra**  
Week 11 Lab - Semantic Search & Vector Database
