# Local Privacy-Preserving RAG for Internal Documents

A **privacy-first Retrieval-Augmented Generation (RAG) system** designed to securely query internal organizational documents such as **employee handbooks, HR policies, IT/computer-use guidelines, compliance documents, and internal SOPs** — entirely **offline and without reliance on external APIs**.

The system runs fully on local infrastructure using **Ollama-powered local LLMs**, a **Chroma vector database**, and a **Python-based RAG pipeline**, ensuring **data confidentiality, deterministic behavior, and reproducible execution**.

---

## Key Capabilities

- **End-to-End Local Execution**  
  All document processing, embedding generation, retrieval, and inference are performed locally, eliminating external data exposure.

- **Context-Grounded Question Answering**  
  Responses are generated strictly from retrieved document context, reducing hallucinations and improving factual reliability.

- **Local LLM Inference via Ollama**  
  Compatible with models such as `llama3`, `mistral`, `gemma`, and other Ollama-supported architectures.

- **Semantic Search with ChromaDB**  
  Efficient vector-based retrieval for scalable document collections.

- **Reproducible Environment Management with `uv`**  
  Fast dependency resolution and consistent runtime environments across systems.

- **Flexible Execution Modes**  
  Supports both **Jupyter Notebooks** for experimentation and **Python scripts** for structured execution.

---

## Model Architecture

The system follows a **standard Retrieval-Augmented Generation (RAG) architecture**, optimized for **local execution and privacy preservation**.

### Core Components

1. **Document Loader**
   - Ingests internal documents (PDF, DOCX, TXT)
   - Extracts raw text using format-aware loaders

2. **Text Chunking Layer**
   - Splits documents into semantically meaningful chunks
   - Applies overlap strategies to preserve context continuity

3. **Embedding Model (Local)**
   - Generates dense vector representations of text chunks
   - Runs locally using Ollama-compatible embedding models

4. **Vector Store (ChromaDB)**
   - Stores embeddings and associated metadata
   - Enables fast similarity-based retrieval

5. **Retriever**
   - Performs Top-K semantic search against ChromaDB
   - Filters the most relevant document chunks for a query

6. **Prompt Assembly Layer**
   - Injects retrieved context into a controlled prompt template
   - Applies system rules to enforce grounded responses

7. **Local LLM (Ollama Runtime)**
   - Generates answers using retrieved context only
   - Ensures offline inference and deterministic execution

---

## Processing Pipeline

The end-to-end processing pipeline consists of two distinct phases:

---

### 1. Indexing / Ingestion Pipeline

This phase prepares documents for retrieval.

**Steps:**
1. Load internal documents from disk  
2. Clean and normalize extracted text  
3. Chunk text into fixed-size segments with overlap  
4. Generate vector embeddings locally  
5. Persist embeddings and metadata into ChromaDB  

**Execution:**
```bash
uv run python src/ingest.py
````

This pipeline is typically executed **once per document update cycle**.

---

### 2. Query / Inference Pipeline

This phase handles user questions and answer generation.

**Steps:**

1. Accept user query (CLI or Notebook)
2. Convert query into embedding
3. Perform Top-K similarity search in ChromaDB
4. Assemble retrieved context into a structured prompt
5. Generate response using a local LLM via Ollama
6. Return a grounded, context-aware answer

**Execution:**

```bash
uv run python src/main.py
```

---

## Technology Stack

* **Python 3.10+**
* **Ollama** (Local LLM runtime)
* **ChromaDB** (Vector database)
* **LangChain / Custom RAG orchestration**
* **Jupyter Notebook**
* **uv** (Python environment and dependency management)

---

## Getting Started

### 1. Install Ollama

Download and install Ollama:

```
https://ollama.com
```

Pull a local language model:

```bash
ollama pull llama3
```

---

### 2. Clone the Repository

```bash
git clone https://github.com/your-username/local-rag-internal-docs.git
cd local-rag-internal-docs
```

---

### 3. Set Up the Python Environment

Install `uv` (one-time setup):

```bash
pip install uv
```

Create the environment and install dependencies:

```bash
uv sync
```

---

### 4. Add Internal Documents

Place internal documents in the following directory:

```
data/documents/
```

Supported formats:

* PDF
* DOCX
* TXT

---

### 5. Ingest Documents

```bash
uv run python src/ingest.py
```

---

### 6. Query the System

```bash
uv run python src/main.py
```

Example query:

```
What is the annual leave policy during probation?
```

---

### 7. Jupyter Notebook Mode (Optional)

```bash
uv run jupyter notebook
```

Use notebooks for experimentation, debugging, and prompt iteration.

---

## Representative Use Cases

* HR policy clarification (leave, probation, payroll rules)
* IT and acceptable-use policy lookup
* Internal SOP and compliance reference
* Employee self-service knowledge assistant
* Audit and policy verification support

---

## Rationale for Local RAG

| Dimension             | Cloud-Based LLMs | This System  |
| --------------------- | ---------------- | ------------ |
| Data Privacy          | Limited          | Full         |
| External Connectivity | Required         | Not Required |
| Vendor Lock-in        | High             | None         |
| Custom Documents      | Restricted       | Native       |
| Cost at Scale         | Variable         | Predictable  |

---

## Disclaimer

This project is intended for **internal and private document analysis** only.
Users are responsible for ensuring compliance with applicable **organizational, legal, and data-governance requirements**.

---

## Roadmap

* Source-level citations in generated responses
* Multi-model routing and evaluation
* Web-based interface (Streamlit / FastAPI)
* Role-based document access controls
* Usage telemetry and feedback mechanisms

---

## License

MIT License.

---

## Author

Developed for privacy-first, enterprise-grade AI knowledge systems.
Contributions and improvements are welcome.

```
