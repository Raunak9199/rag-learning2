# YTRAG

A local RAG (Retrieval-Augmented Generation) learning project that ingests documents, builds a vector store, and performs semantic search with LLM-based summarization.

## Overview

This repository demonstrates a simple RAG pipeline using:

- `langchain` and `langchain-community` for document loading and prompt workflows
- `sentence-transformers` for embeddings
- `faiss` for vector indexing and similarity search
- `chromadb` support in notebooks for alternate vector storage
- `langchain-groq` for LLM generation

## Features

- Load documents from `data/` in multiple formats: PDF, TXT, CSV, Excel, DOCX, JSON
- Chunk and embed text for semantic retrieval
- Build and persist a FAISS vector store in `faiss_store/`
- Query the stored embeddings and summarize results using an LLM
- Notebook examples in `notebook/` showing PDF ingestion, embedding creation, and RAG pipelines

## Repository Structure

- `app.py` - example entrypoint for loading documents, initializing FAISS, and running RAG search
- `requirements.txt` - Python package dependencies
- `src/data_loader.py` - document ingest utilities
- `src/embedding.py` - embedding/chunking pipeline (used by FAISS store)
- `src/vectorstore.py` - FAISS vector store build, save, load, and query logic
- `src/search.py` - RAG search workflow with Groq LLM summarization
- `notebook/` - exploratory notebooks for PDF loading and pipeline experimentation
- `data/` - source documents and persisted vector store data

## Setup

1. Create or activate a Python environment.

```bash
python -m venv .venv
source .venv/bin/activate
```

2. Install dependencies.

```bash
pip install -r requirements.txt
```

3. (Optional) Create a `.env` file and set any API keys required by your LLM integrations.

```text
GROQ_API_KEY=your_api_key_here
```

## Usage

Run the example application:

```bash
python app.py
```

This script will:

- load supported documents from `data/`
- initialize the `FaissVectorStore`
- optionally build or load a saved FAISS index
- run a sample query and print a summary

## Notebook

The notebook `notebook/pdf_loader.ipynb` contains hands-on examples for:

- loading PDFs
- splitting text into chunks
- generating embeddings
- storing vectors in ChromaDB
- querying and building a RAG response pipeline

## Notes

- `faiss_store/` contains the persisted FAISS index and metadata file.
- `data/vector_store/` is used by the notebook for ChromaDB persistence.
- If you add new documents, rebuild the FAISS store by running the relevant build path in `src/vectorstore.py` or `app.py`.

## License

This repository does not include a license file. Add one if you want to make the project reusable by others.
