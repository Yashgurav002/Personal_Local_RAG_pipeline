# 🗂️ Chat With Any PDF — Local RAG Pipeline

> Ask questions about any PDF using a fully local RAG pipeline. No API keys. No internet after setup. Runs entirely on your laptop.

[![YouTube Demo](https://img.shields.io/badge/YouTube-Watch%20Demo-red?style=for-the-badge&logo=youtube)](https://www.youtube.com/watch?v=VJGAaMq6JDI&t=6s)
[![GitHub](https://img.shields.io/badge/GitHub-Repo-black?style=for-the-badge&logo=github)](https://github.com/Yashgurav002/Personal_Local_RAG_pipeline/)

---

## 📺 Demo

[![Watch the demo](https://img.youtube.com/vi/VJGAaMq6JDI/maxresdefault.jpg)](https://www.youtube.com/watch?v=VJGAaMq6JDI&t=6s)

---

## 🧠 How It Works

```
PDF File
  → PyPDFLoader        (extract text page by page)
  → RecursiveCharacterTextSplitter  (cut into overlapping chunks)
  → HuggingFace Embeddings          (convert chunks to vectors)
  → FAISS                           (store + search vectors)
  → Ollama / Mistral                (generate answer from retrieved chunks)
  → Your Answer ✅
```

This is a standard **RAG (Retrieval-Augmented Generation)** pipeline. Instead of sending the whole PDF to an LLM, it finds the most relevant chunks first and sends only those — making it accurate, fast, and context-aware.

---

## ⚙️ Stack

| Component | Tool |
|---|---|
| LLM | Ollama (Mistral) — runs locally |
| Embeddings | `all-MiniLM-L6-v2` via HuggingFace |
| Vector Store | FAISS |
| Framework | LangChain (LCEL) |
| PDF Loader | PyPDFLoader |
| Interface | Jupyter Notebook |

---

## 🚀 Quickstart

### 1. Prerequisites

Install [Ollama](https://ollama.com) and pull Mistral:

```bash
ollama pull mistral
ollama serve
```

### 2. Clone the repo

```bash
git clone https://github.com/Yashgurav002/Personal_Local_RAG_pipeline.git
cd Personal_Local_RAG_pipeline
```

### 3. Install dependencies

```bash
pip install langchain langchain-community langchain-text-splitters langchain-huggingface langchain-ollama faiss-cpu sentence-transformers pypdf
```

### 4. Run the notebook

Open `pdf_rag_local.ipynb` in Jupyter and update `PDF_PATH` in Cell 2 to point to your PDF.

Run all cells top to bottom. On first run the embedding model (~90MB) downloads and caches automatically.

---

## 📁 Project Structure

```
Personal_Local_RAG_pipeline/
│
├── pdf_rag_local.ipynb     # Main notebook — full RAG pipeline
├── faiss_store/            # Auto-generated after first run (gitignored)
└── README.md
```

---

## 💬 Features

- Upload any PDF and ask questions about it in natural language
- Answers grounded strictly in the document — no hallucination
- Shows source chunks with page numbers for every answer
- Mini chat loop for multiple questions without re-running cells
- Switch PDFs mid-session without restarting the kernel

---

## ⚠️ Known Limitations

- Works on text-based PDFs only — scanned/image PDFs will return poor results
- No conversation memory — each question is answered independently
- Ollama must be running locally before starting the notebook

---

## 🔮 What's Next

This notebook is the foundation for a full-stack **"Chat with Any PDF"** web app (in progress):

- FastAPI backend with session management
- React frontend with streaming answers
- Deployed free on Render + Vercel
- Groq (free tier) as the cloud LLM for deployment

---

## 🙋 Author

**Yash Gurav** — AI & Data Science Engineer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/yash-gurav-58bbba21a/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/Yashgurav002/)
