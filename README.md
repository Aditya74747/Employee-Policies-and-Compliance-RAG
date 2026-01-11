# Employee Policies and Compliance RAG

A **privacy-first Retrieval-Augmented Generation (RAG) system** designed to securely query internal organizational documents such as **employee handbooks, HR policies, IT/computer-use guidelines, compliance documents, and internal SOPs** — entirely **offline and without reliance on external APIs**.

The system runs fully on local infrastructure using **Ollama-powered local LLMs**, a **Chroma vector database**, and a **Python-based RAG pipeline**, ensuring **data confidentiality, deterministic behavior, and reproducible execution**.

Repository:  
https://github.com/Aditya74747/Employee-Policies-and-Compliance-RAG

---

## Key Capabilities

- **End-to-End Local Execution**  
  All document processing, embedding generation, retrieval, and inference are performed locally, eliminating external data exposure.

- **Context-Grounded Question Answering**  
  Responses are generated strictly from retrieved document context, reducing hallucinations and improving factual reliability.

- **Local LLM Inference via Ollama**  
  Uses the `llama3.1:8b` model, selected for its optimal balance of **model size, inference speed, and practical usability** in local, resource-constrained environments.

- **Semantic Search with ChromaDB**  
  Efficient vector-based retrieval for scalable document collections.

- **Reproducible Environment Management with `uv`**  
  Fast dependency resolution and consistent runtime environments across systems.

- **Flexible Execution Modes**  
  Supports both **Jupyter Notebooks** for experimentation and **Python scripts** for structured execution.

---

## Model Architecture

This system follows a **standard Retrieval-Augmented Generation (RAG) architecture**, optimized for **local execution and enterprise data privacy**.

### Core Components

1. **Document Loader**  
   Ingests internal documents (PDF, DOCX, TXT) using format-aware loaders.

2. **Text Chunking Layer**  
   Splits documents into semantically meaningful chunks with overlap to preserve context continuity.

3. **Embedding Model (Local)**  
   Generates dense vector representations locally using Ollama-compatible embedding models, ensuring that both document indexing and query embeddings remain fully offline.

4. **Vector Store (ChromaDB)**  
   Stores embeddings and metadata to enable fast similarity-based retrieval.

5. **Retriever**  
   Performs Top-K semantic search against the vector database.

6. **Prompt Assembly Layer**  
   Injects retrieved context into a controlled prompt template with grounding rules.

7. **Local LLM (Ollama Runtime – llama3.1:8b)**  
   Uses the `llama3.1:8b` model for response generation, chosen for its compact footprint, reliable instruction-following, and suitability for local RAG workloads without GPU dependency.

---

## Technology Stack

* **Python 3.10+**
* **Ollama** – Local LLM runtime
* **ChromaDB** – Vector database
* **LangChain / Custom RAG orchestration**
* **Jupyter Notebook**
* **uv** – Python environment and dependency management

---

## Getting Started

### 1. Install Ollama

Download and install Ollama:

```
https://ollama.com
```

Pull a local model:

```bash
ollama pull nomic-embed-text
ollama pull llama3.1:8b
```

Start Ollama:

```bash
ollama serve
```


---

### 2. Clone the Repository

```bash
git clone https://github.com/Aditya74747/Employee-Policies-and-Compliance-RAG.git
cd Employee-Policies-and-Compliance-RAG
```

---

### 3. Set Up the Python Environment

Install `uv`:

```bash
pip install uv
```

Create the environment and install dependencies:

```bash
uv venv
uv add -r requirements.txt
uv sync
```

---

### 4. Add Internal Documents

Place documents in the folder:

```
data/
```

Supported formats:

* PDF
* DOCX
* TXT

---

### 5. Run via Jupyter Notebook

```bash
uv run jupyter notebook
```
Run all cells from top to bottom.

---

### 6. Query in the Notebook

Example query and response:

```
Query: What are the things that I should not do in the workplace?

Response: Based on the provided policy excerpts, here is a list of things that you should not do in the workplace:

* Engage in any activity that is illegal under local, state, federal or international law while utilizing Holiday Market-owned resources. (Computer Use Policy.pdf | chunk 9)
* Participate in system and network activities that are strictly prohibited, with no exceptions (e.g. hacking, unauthorized access). (Computer Use Policy.pdf | chunk 9)
* Make threats, even as a joke or prank, during working hours or in company vehicles. (handbook.pdf | chunk 34)
* Commit violent acts or threaten violence during non-working hours or away from the workplace, unless:
	+ The associate's conduct adversely affects the Company's reputation. (A) (handbook.pdf | chunk 34)
	+ The Company determines that the effects of the off-duty conduct may be carried into the workplace and/or pose a threat to Company associates, visitors or property. (B) (handbook.pdf | chunk 34)
	+ The conduct results in the conviction of the associate for an assault or other felony. (C) (handbook.pdf | chunk 34)
* Work for any company in direct competition with Holiday Market without written consent. (handbook.pdf | chunk 83)
* Solicit other associates during working time. (handbook.pdf | chunk 83)
* Distribute literature on company premises during working time, except as permitted by management. (handbook.pdf | chunk 83)
* Enter or remain in the interior of the building or other working area unless you are on duty or scheduled to work. (handbook.pdf | chunk 83)

```


---

## Representative Use Cases

* HR policy clarification (leave, probation, payroll rules)
* IT and acceptable-use policy lookup
* Internal SOP and compliance reference
* Employee self-service knowledge assistant
* Audit and policy verification support

---

## Disclaimer

This project is intended for **internal and private document analysis** only.
Users are responsible for ensuring compliance with applicable **organizational, legal, and data-governance requirements**.

---

## License

MIT License.

---

## Author

Developed by **Aditya Ghatage** for privacy-first, enterprise-grade AI knowledge systems.
Contributions and improvements are welcome.
