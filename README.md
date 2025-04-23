
# 🔍 Dr. X Research Q&A System – OSOS AI Technical Test

This repository contains my complete solution for the **OSOS AI Technical Test**, where I built a fully offline, NLP-driven pipeline to process, analyze, and extract insights from the mysterious research publications of **Dr. X**.

The final deliverable includes a **Retrieval-Augmented Generation (RAG) Q&A system**, a **translation tool**, and a **summarization engine**, all powered by local models and vector databases.

---

## 🎯 Project Goal

The objective of this project was to:
- Investigate Dr. X’s research publications (PDF, DOCX, XLS, CSV files).
- Build a robust NLP pipeline that extracts, chunks, summarizes, and understands the content.
- Enable users to ask intelligent questions about the publications using a local RAG system.
- Translate publications across languages (Arabic ↔ English).
- Summarize vast research into clear, concise insights.
- Ensure all components work fully **offline**, using **local models** and **open-source tools**.

---

## 🧠 Techniques & Pipeline Overview

The complete pipeline includes:

### 1. **File Parsing & Preprocessing**
- Parsed `.pdf`, `.docx`, `.csv`, `.xls`, `.xlsx`, `.xlsm` using `PyPDF2`, `python-docx`, and `pandas`.
- Extracted table text in readable form (no layout recreation).
- Mapped all extracted content with metadata: `filename`, `page`, `chunk number`.

### 2. **Token-Based Text Chunking**
- Used `tiktoken` tokenizer (`cl100k_base`) to break long texts into 300-token chunks.
- Each chunk is paired with metadata for traceability and retrieval.

### 3. **Vector Embeddings + Local Vector DB**
- Used `t5-small` (Hugging Face) locally to create embeddings for each chunk.
- Stored vectors in `FAISS` — a fully offline and fast similarity search index.

### 4. **Retrieval-Augmented Generation (RAG) Q&A System**
- Embedded user queries using the same local model (`t5-small`).
- Retrieved top-k most relevant chunks using FAISS.
- Constructed a prompt from retrieved text and answered questions using a **local LLaMA model** via `llama-cpp-python`.

### 5. **Multilingual Translation Tool**
- Auto-detected input language using `langdetect`.
- Translated Arabic ↔ English using MarianMT models from Hugging Face:
  - `opus-mt-en-ar`
  - `opus-mt-ar-en`
- Translation system worked entirely offline and preserved document structure.

### 6. **Summarization & Super-Summary Generator**
- Used `t5-small` for summarizing each chunk of the research.
- Aggregated summaries per document to create a **super-summary**.
- Optionally, generated a final **mega-summary** across all documents.

### 7. **Performance Metrics**
- Tracked and recorded:
  - Processing time per phase
  - Tokens-per-second for embedding and summarization
  - Summary quality using the **ROUGE metric**

---

## 🧪 Tools & Libraries Used

| Component       | Tool/Model                              |
|------------------|------------------------------------------|
| Text Parsing     | `PyPDF2`, `python-docx`, `pandas`        |
| Tokenization     | `tiktoken (cl100k_base)`                |
| Embeddings       | `t5-small` (Hugging Face)               |
| Vector DB        | `FAISS`                                 |
| LLM (Q&A)        | `llama-cpp-python` + GGUF model         |
| Translation      | `langdetect`, `MarianMT`                |
| Summarization    | `t5-small`                              |
| Evaluation       | `rouge_score`                           |

---

## 📈 Results & Insights

- ✅ Successfully processed and indexed Dr. X’s diverse research files.
- 🤖 Built a responsive Q&A system that answers questions based on actual text.
- 🌍 Enabled translation for multilingual publications (Arabic ↔ English).
- 📝 Created meaningful summaries that distill complex research into digestible insights.
- 🔐 Entire pipeline works **offline** — no external API or cloud access required.

---

## 🧠 Key Takeaways

- Dr. X’s work revolved around **neural microstates, cognitive modeling**, and **cross-linguistic inference**.
- The RAG system revealed consistent themes of **human-computer interaction**, **consciousness modeling**, and **language encoding** across different publications.
- The disappearance of Dr. X may be connected to unexplored intersections of neuroscience and artificial intelligence hinted at in the later research summaries.

---


