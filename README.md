# 📄 Policy RAG System (Python + Ollama + Chroma)

A **local, privacy-preserving Retrieval-Augmented Generation (RAG) system** for querying internal documents such as employee handbooks, IT/computer-use policies, HR rules, and other organizational documents.

This project uses **Python**, **Ollama (local LLMs)**, **Chroma vector database**, and can be run either via **Jupyter Notebook** or **Python scripts**, with fast and reproducible setup using **`uv`**.

---

## 🚀 Features
- 100% local execution (no data leaves your machine)
- Supports **PDF, DOCX, TXT** documents
- Ollama-based embeddings and LLM inference
- Persistent vector store using Chroma
- Works seamlessly across multiple machines
- Fast environment setup with `uv`

---

## 🧰 Prerequisites
- Python **3.10+**
- **Ollama** installed and running
- **uv** installed

Install `uv`:
```bash
pip install uv

