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

## Technology Stack

- **Python 3.10+**
- **Ollama** (Local LLM runtime)
- **ChromaDB** (Vector database)
- **LangChain / Custom RAG orchestration**
- **Jupyter Notebook**
- **uv** (Python environment and dependency management)

---

## Getting Started

### 1. Install Ollama

Download and install Ollama:
```

[https://ollama.com](https://ollama.com)

````

Pull a local language model:
```bash
ollama pull llama3
````

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

Supported formats include:

* PDF
* DOCX
* TXT

---

### 5. Ingest Documents into the Vector Store

```bash
uv run python src/ingest.py
```

This process:

* Loads and parses documents
* Chunks text into semantically meaningful segments
* Generates embeddings
* Persists vectors in ChromaDB

---

### 6. Query the System (Script Mode)

```bash
uv run python src/main.py
```

Example query:

```
What is the annual leave policy during probation?
```

---

### 7. Run via Jupyter Notebook (Optional)

```bash
uv run jupyter notebook
```

Use the notebook interface to experiment with retrieval parameters, prompts, and model behavior interactively.

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
| Custom Document Use   | Restricted       | Native       |
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

---

### If you want next (recommended for portfolio impact):
- Tight **1-paragraph GitHub repo description**
- **Recruiter-optimized project summary** for your CV
- **Badges** (Python | Ollama | Local-Only | MIT)
- A **“Why this matters”** section tailored for AI/ML interviews

Just tell me what you’d like to add.
```
