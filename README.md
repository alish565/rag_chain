# 📱 Mobile Journalism Document QA System (RAG)

A Retrieval-Augmented Generation (RAG) pipeline built with **LangChain**, **FAISS**, and **OpenAI**. This project automatically downloads a PDF handbook on mobile journalism, processes and indexes its contents, and answers questions using strictly verified context from the document.

---

## 📌 How It Works

1. **Download & Load**: Downloads the PDF from a specified URL using `urllib` and parses it with `PyMuPDFLoader`.
2. **Chunking**: Splits the document into 500-character chunks with a 100-character overlap via `RecursiveCharacterTextSplitter`.
3. **Embeddings & Vector Store**: Converts text chunks into vector embeddings using OpenAI's `text-embedding-3-small` and indexes them in a local **FAISS** vector database.
4. **Context-Restricted QA**: Uses `gpt-3.5-turbo` with a custom prompt constraint that enforces concise responses (under 5 sentences) based strictly on retrieved document context.

---

## 🚀 Getting Started

### Prerequisites

* Python 3.9+
* OpenAI API key

### Installation

```bash
pip install langchain langchain-openai langchain-community faiss-cpu pymupdf python-dotenv
Environment Setup
Set your OpenAI API key in your environment or inside Google Colab Secrets:

Bash
export OPENAI_API_KEY="your_openai_api_key"
Usage
Run the main script:

Bash
python rag_mobile_journalism.py
The script will download the PDF to a local mobile_journalism/ folder, build the index, and print the answer to the sample query:

Query: "What applications are used for mobile journalism?"

🛠️ Tech Stack
Framework: LangChain

LLM: OpenAI gpt-3.5-turbo

Embeddings: text-embedding-3-small

Vector Database: FAISS

PDF Loader: PyMuPDF (fitz)
