📄 Policy RAG System (Ollama + Python)

A local, privacy-preserving Retrieval-Augmented Generation (RAG) system for querying internal documents such as:

Employee Handbooks

Computer / IT Usage Policies

HR, Leave, Payroll, Security documents

Built with Python, Ollama (local LLMs), Chroma vector DB, and usable via Jupyter Notebook or scripts.

🚀 Key Features

100% local (no data leaves your machine)

Supports PDF, DOCX, TXT

Uses Ollama for embeddings + LLM

Persistent vector store (Chroma)

Works seamlessly across work laptop → personal laptop

Fast setup using uv

🗂 Project Structure
policy-rag/
│
├── notebook/
│   └── rag.ipynb            # Main Jupyter notebook
│
├── src/
│   ├── loaders.py           # PDF / DOCX / TXT loaders
│   ├── ingest.py            # Document ingestion & indexing
│   ├── query.py             # CLI querying
│   └── config.py            # Central configuration
│
├── data_sample/             # Public dummy documents (optional)
├── requirements.txt
├── .gitignore
└── README.md


⚠️ Do NOT commit real company documents or the db/ folder

🧰 Prerequisites

Python 3.10+

Ollama installed and running

uv installed

Install uv (once):

pip install uv


Install Ollama from: https://ollama.com

Then pull models:

ollama pull nomic-embed-text
ollama pull llama3.1:8b


Start Ollama:

ollama serve

⚡ Quick Start (Using uv)
1️⃣ Clone the repository
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

2️⃣ Create environment & install dependencies
uv venv
uv pip install -r requirements.txt


Activate the environment:

Windows

.venv\Scripts\activate


macOS / Linux

source .venv/bin/activate

3️⃣ (Optional) Register kernel for Jupyter
python -m ipykernel install --user --name policy-rag --display-name "Policy RAG (uv)"

📥 Add Your Documents

Create a local data/ folder (ignored by Git):

data/
 ├── Employee_Handbook.pdf
 ├── Computer_Use_Policy.docx
 └── Leave_Policy.txt

📌 Option A: Run via Jupyter Notebook
jupyter notebook


Open:

notebook/rag.ipynb


Select kernel:

Policy RAG (uv)


Run cells top → bottom:

Load documents

Chunk + embed

Store in Chroma

Ask questions

Example question:

ask("What is the annual leave policy during probation?")

📌 Option B: Run via Python scripts
Ingest documents
python -m src.ingest

Query documents
python -m src.query "What is the IT policy on personal device usage?"

🧠 Models Used
Purpose	Model
Embeddings	nomic-embed-text
LLM	llama3.1:8b

You can change models in src/config.py.

🔐 Security & Compliance Notes

No cloud APIs used

No documents pushed to GitHub

Embeddings stored locally only

Suitable for confidential internal documents

🛠 Common Issues

Ollama not responding

ollama serve


Retriever error
Make sure LangChain versions match requirements.txt.

Empty answers

PDFs may be scanned → OCR needed

Check document text extraction

📈 Future Enhancements

Page-number citations

Document-level filters (HR vs IT)

Streamlit / FastAPI UI

Reranking for higher accuracy

📄 License

MIT (for code only — not documents)