# PsychTutor

<p align="center">
  <strong>Intelligent Cognitive Psychology Tutor & Textbook Knowledge Retrieval Assistant</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Interface-Streamlit-18181B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit" />
  <img src="https://img.shields.io/badge/Language-Python_3.10+-18181B?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Orchestration-LangChain-18181B?style=for-the-badge&logo=chainlink&logoColor=white" alt="LangChain" />
  <img src="https://img.shields.io/badge/License-MIT-18181B?style=for-the-badge" alt="License" />
</p>

---

## Overview

**PsychTutor** is an interactive educational AI assistant built to tutor students in psychology using authoritative university textbooks (including MIT Psychology and OpenStax Psychology 2e).

Powered by Retrieval-Augmented Generation (RAG), PsychTutor chunks and indexes curriculum textbooks into ChromaDB with dense transformer embeddings, queries Groq high-speed LPU inference, and guides learners through Socratic explanations, clinical concept breakdowns, and self-assessment quizzes without generating hallucinated psychology claims.

---

## Tech Stack

<p align="center">
  <img src="https://img.shields.io/badge/Streamlit-18181B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit" />
  <img src="https://img.shields.io/badge/Python-18181B?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/LangChain-18181B?style=for-the-badge&logo=chainlink&logoColor=white" alt="LangChain" />
  <img src="https://img.shields.io/badge/Groq_LPU-18181B?style=for-the-badge&logo=fastapi&logoColor=white" alt="Groq" />
  <img src="https://img.shields.io/badge/ChromaDB-18181B?style=for-the-badge&logo=databricks&logoColor=white" alt="ChromaDB" />
  <img src="https://img.shields.io/badge/PyTorch-18181B?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch" />
  <img src="https://img.shields.io/badge/Hugging_Face-18181B?style=for-the-badge&logo=huggingface&logoColor=white" alt="Hugging Face" />
</p>

---

## Pipeline Architecture

```
Authoritative Psychology Textbooks (PDF Corpus)
                      │
                      ▼
        [Document Parsing & Chunking]    (pdfplumber, NLTK)
                      │
                      ▼
          [Dense Vector Embeddings]      (sentence-transformers)
                      │
                      ▼
          [ChromaDB Local Vector DB]
                      │
    ┌─────────────────┴─────────────────┐
    ▼                                   ▼
[Student Question Input]      [Semantic Similarity Search]
 (Streamlit Web Interface)    (Extract Relevant Textbook Passages)
    └─────────────────┬─────────────────┘
                      │
                      ▼
          [Groq High-Speed LPU API]       (LangChain ChatGroq)
                      │
                      ▼
     [Socratic Pedagogical Explanations & Citations]
```

---

## Key Features

- **Textbook-Grounded QA**: Directly grounded in MIT Psychology and Psychology 2e textbooks to ensure clinical and academic rigor.
- **Ultra-Low Latency Inference**: Uses Groq LPU acceleration via `langchain-groq` for near-instant conversational feedback.
- **Interactive Streamlit Interface**: Clean, conversational web UI supporting follow-up inquiries, citations, and concept breakdowns.
- **Persistent Vector Index**: ChromaDB vector store enables fast offline semantic lookup without re-indexing textbooks on every launch.

---

## Repository Structure

```
PsychTutor/
├── .devcontainer/             # DevContainer development configuration
│   └── devcontainer.json
├── app.py                     # Streamlit frontend & LangChain RAG pipeline
├── psychology_books/          # Authoritative psychology textbook PDF library
│   ├── mit_psychology.pdf
│   └── psychology_2e.pdf
├── requirements.txt           # Python dependencies
└── README.md
```

---

## Getting Started

### 1. Prerequisites
* Python 3.10+
* Groq API Key (get free access at [console.groq.com](https://console.groq.com))

### 2. Installation
```bash
git clone https://github.com/prannesshkva/PsychTutor.git
cd PsychTutor
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Environment Configuration
Create a `.env` file in the root directory:
```env
GROQ_API_KEY=your_groq_api_key_here
```

### 4. Run Application
```bash
streamlit run app.py
```
Open your browser at `http://localhost:8501`.

---

## Author

* **Architect**: [Prannessh KVA](https://github.com/prannesshkva)
* **Focus**: Educational AI Systems, Cognitive Science, and Retrieval-Augmented Generation

---

## License

This project is licensed under the MIT License.
