# PDF Retrieval-Augmented Generation (RAG) Pipeline

This repository contains a complete, end-to-end RAG pipeline designed to ingest PDF documents, process them into semantic chunks, and provide context-aware answers using state-of-the-art LLMs via Groq.

## 🚀 Features

- **PDF Ingestion**: Bulk loading of PDF files from local directories using `PymUPDFLoader`.
- **Smart Chunking**: Utilizes `RecursiveCharacterTextSplitter` to maintain context while staying within token limits.
- **Vector Storage**: Persistent storage of document embeddings using `ChromaDB` for efficient semantic search.
- **Semantic Retrieval**: A custom `RAGretriever` class that calculates similarity scores to find the most relevant context.
- **Groq Integration**: Fast inference using models like `Qwen3-32B` hosted on Groq for high-quality generation.

## 🛠️ Tech Stack

- **Orchestration**: LangChain
- **LLM API**: Groq (Qwen-32B Model)
- **Vector DB**: ChromaDB
- **Embeddings**: Sentence-Transformers (`all-MiniLM-L6-v2`)
- **PDF Processing**: PyMuPDF




##🔧 Configuration

To run this pipeline, you will need a Groq API Key:

`API_KEY_GROQ = "your_groq_api_key_here"`
##📖 How it Works

- **Data Ingestion**: Documents are loaded and split into chunks with overlap to ensure no context is lost.
- **Embedding**: Each chunk is converted into a 384-dimensional vector using the all-MiniLM-L6-v2 model.
- **Storage**: Vectors and metadata are stored in a persistent ChromaDB collection for long-term retrieval.
- **Querying**: User queries are embedded and compared against the store using cosine similarity to find relevant matches.
- **Generation**: The top-K retrieved chunks are formatted into a prompt and sent to the LLM (Qwen-32B) to generate an answer grounded in the provided documents.
