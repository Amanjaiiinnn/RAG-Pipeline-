# PDF Retrieval-Augmented Generation (RAG) Pipeline

This repository contains a complete end-to-end RAG pipeline designed to ingest PDF documents, process them into semantic chunks, and generate context-aware answers using state-of-the-art LLMs through Groq.

---

## 🚀 Features

- **PDF Ingestion**  
  Bulk loading of PDF files from local directories using `PyMuPDFLoader`.

- **Smart Chunking**  
  Uses `RecursiveCharacterTextSplitter` to preserve semantic context while staying within token limits.

- **Vector Storage**  
  Persistent embedding storage using `ChromaDB` for efficient semantic retrieval.

- **Semantic Retrieval**  
  Custom `RAGRetriever` class for similarity-based document retrieval with ranking and scoring.

- **Groq Integration**  
  Fast LLM inference using models such as `Qwen/Qwen3-32B` hosted on Groq.

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Orchestration | LangChain |
| LLM API | Groq |
| LLM Model | Qwen3-32B |
| Vector Database | ChromaDB |
| Embedding Model | Sentence-Transformers (`all-MiniLM-L6-v2`) |
| PDF Processing | PyMuPDF |

---


##📖 How it Works

- **Data Ingestion**: Documents are loaded and split into chunks with overlap to ensure no context is lost.
- **Embedding**: Each chunk is converted into a 384-dimensional vector using the all-MiniLM-L6-v2 model.
- **Storage**: Vectors and metadata are stored in a persistent ChromaDB collection for long-term retrieval.
- **Querying**: User queries are embedded and compared against the store using cosine similarity to find relevant matches.
- **Generation**: The top-K retrieved chunks are formatted into a prompt and sent to the LLM (Qwen-32B) to generate an answer grounded in the provided documents.

  ---

## 🔧 Configuration

To run this pipeline, add your Groq API key:

```python
API_KEY_GROQ = "your_groq_api_key_here" ```



