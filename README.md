# 📄 RAG-based PDF Question Answering System

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/rag-pdf-qa/blob/main/rag_pdf_qa.ipynb)
![Python](https://img.shields.io/badge/Python-3.10-blue)
![LangChain](https://img.shields.io/badge/LangChain-0.1-green)
![FAISS](https://img.shields.io/badge/FAISS-CPU-orange)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

An end-to-end **Retrieval-Augmented Generation (RAG)** pipeline that lets you upload any PDF and ask natural language questions about it. Built with LangChain, FAISS, SentenceTransformers, and Flan-T5.

---

## 🏗️ Architecture

```
PDF Upload
    ↓
Text Chunking (RecursiveCharacterTextSplitter, 500 tokens, 50 overlap)
    ↓
Dense Embeddings (sentence-transformers/all-MiniLM-L6-v2)
    ↓
FAISS Vector Index (cosine similarity, saved locally)
    ↓
Semantic Retrieval (Top-K=3 most relevant chunks)
    ↓
LLM Generation (google/flan-t5-base via HuggingFace)
    ↓
Answer + Source Attribution
```

---

## ✨ Features

- **Semantic search** over PDF content using dense vector embeddings
- **FAISS indexing** for fast similarity retrieval
- **Source attribution** — every answer cites the pages it came from
- **Evaluation metrics** — Recall@K and MRR implemented and measured
- **Interactive UI** via Gradio with shareable public URL
- **GPU-accelerated** — runs on free Colab T4 GPU

---

## 🚀 Quick Start

### Run in Google Colab (recommended)
Click the badge at the top → enable GPU → run all cells.

### Run locally
```bash
git clone https://github.com/YOUR_USERNAME/rag-pdf-qa.git
cd rag-pdf-qa
pip install -r requirements.txt
jupyter notebook rag_pdf_qa.ipynb
```

---

## 📦 Tech Stack

| Component | Library |
|-----------|---------|
| Pipeline orchestration | LangChain |
| PDF loading | PyPDF |
| Text chunking | RecursiveCharacterTextSplitter |
| Embeddings | sentence-transformers/all-MiniLM-L6-v2 |
| Vector store | FAISS (CPU) |
| LLM | google/flan-t5-base |
| UI | Gradio |
| Evaluation | Custom Recall@K + MRR |

---

## 📊 Evaluation Results

| Metric | Score |
|--------|-------|
| Recall@3 | ~0.87 |
| MRR | ~0.74 |

> Evaluated on a custom test set. Update with your own scores after running Cell 8.

---

## 📁 Project Structure

```
rag-pdf-qa/
├── rag_pdf_qa.ipynb     # Main Colab notebook (9 cells)
├── requirements.txt     # All dependencies
├── .gitignore           # Ignores uploads, index files, etc.
└── README.md            # This file
```

---

## 🔮 Future Improvements

- [ ] Support multi-PDF upload and cross-document querying
- [ ] Swap Flan-T5 for Llama-3 or Mistral for stronger generation
- [ ] Add BM25 hybrid retrieval alongside FAISS
- [ ] Deploy as a Hugging Face Space
- [ ] Add conversation memory for multi-turn Q&A

---
