# 📘 RAG-APP-PHASE1 — Chat With Your Documents

RAG-APP is a complete Retrieval-Augmented Generation system where users can upload documents (PDF, DOCX, TXT), process them, and instantly chat with their content using LLMs — along with accurate, clickable citations.

---

**It includes:**

⚡ FastAPI backend

🎨 Streamlit frontend

🧠 BGE-small embedding model

🗃️ Qdrant vector database

🧵 Session-aware memory

🔗 Precise source citations

---

## 🚀 Project Overview

| Feature |	Description	| Why it Matters |
|------|--------------|-------------|
| **Document Upload**	| Accepts PDF, DOCX, TXT | Flexible input formats |
| **Processing Pipeline** | Extract → Clean → Chunk → Embed → Store	| Full RAG preparation |
| **Qdrant Vector DB** | Stores embeddings for semantic search | Fast & scalable RAG |
| **LLM Querying**	| Chat with documents	| Real-time question answering |
| **Session Memory**	| Maintains conversation context	| More coherent answers |
| **Citations Engine**	| Clickable sources with chunk details	| Transparency & trust |

---

## 🏗️ System Architecture

```bash
User → Streamlit UI → FastAPI Backend → Qdrant Vector DB
                             ↓
                       LLM (Gemini)
                             ↓
                     Response + Citations
```

## 📁 Project Structure

```bash
APP/
│
├── backend/
│   ├── api/
│   │   ├── routes/
│   │   │   ├── upload.py
│   │   │   ├── process.py
│   │   │   ├── query.py
│   │   │   ├── reset_session.py
│   │   │   └── list_docs.py
│   │   └── __init__.py
│   │
│   ├── core/
│   │   ├── text_extractor.py
│   │   ├── text_cleaner.py
│   │   ├── chunking.py
│   │   ├── embedding_engine.py
│   │   ├── model_manager.py
│   │   ├── rag/
│   │   │   ├── rag_pipeline.py
│   │   │   ├── citation_handler.py
│   │   │   ├── retriever.py
│   │   │   ├── llm_engine.py
│   │   │   └── session_memory.py
│   │   └── qdrant_manager.py
│   │
│   ├── utils/
│   │   ├── config.py
│   │   ├── file_manager.py
│   │   └── logger.py
│   │
│   ├── data/
│   │   ├── uploads/
│   │   └── processed/
│   │
│   ├── model/
│   │   └── schemas.py
│   │
│   ├── main.py
│   └── requirements.txt
│
├── frontend/
│   ├── components/
│   │   ├── upload_section.py
│   │   ├── chat_section.py
│   │   └── citation_box.py
│   │
│   ├── utils/
│   │   ├── api_client.py
│   │   └── config.py
│   │
│   ├── app.py
│   └── requirements.txt
│
├── .gitignore
└── README.md
```
---

## ⚙️ Tech Stack

| Layer	| Technology |
|------|--------------|
| **Frontend**	| Streamlit, Requests |
| **Backend** |	FastAPI, Uvicorn |
| **Embeddings** |	BAAI/bge-small-en-v1.5 |
| **Vector DB**	| Qdrant (Docker) |
| **LLM	Google** | Gemini API |
| **Processing**	| PyPDF, Docx, TextCleaner |

---

## 🛠️ Installation & Setup

## 1️⃣ Clone the Repository
```bash
git clone https://github.com/Gauravmupase09/RAG-APP.git
cd RAG-APP
```
---

## 🔧 Backend Setup (FastAPI)

## 2️⃣ Create Virtual Environment
```bash
cd backend
python -m venv venv
venv\Scripts\activate
```
---

## 3️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```
---

## 4️⃣ Start Qdrant (Docker)
```bash
docker pull qdrant/qdrant
docker run -p 6333:6333 qdrant/qdrant
```
Then run backend:
```bash
uvicorn main:app --reload
```
Backend available at:

👉 http://localhost:8000

👉 http://localhost:8000/docs

---

## 🎨 Frontend Setup (Streamlit)
```bash
cd ../frontend
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```
Frontend available at:
👉 http://localhost:8501

---

## 🔄 Workflow: How the App Works

## 📤 1. Upload Documents

- Upload PDF, DOCX, or TXT

- Stored in session-specific folder

## ⚙️ 2. Process Documents

- Processing pipeline:

| Step | Action |
|------|--------------|
| 1	| Extract text |
| 2 |	Clean & normalize text |
| 3	| Chunk documents |
| 4	| Generate embeddings |
| 5 | Upsert to Qdrant |

## 💬 3. Chat With Your Documents

- Ask any question

- Top-k chunk retrieval

- LLM response with memory

- Citation panel shows:
  
  - File name

  - Chunk number

  - Semantic score

  - Clickable PDF source

---

## 📚 API Reference

| Method |	Route |	Description |
|------|--------------|-------------|
| **POST** |	/api/upload	| Upload document |
| **POST** |	/api/process/{session_id}	| Run processing pipeline |
| **POST**	| /api/query/{session_id}	| Query documents |
| **GET**	| /api/list_docs	| List uploaded documents |
| **POST**	| /api/reset_session	| Clear session & Qdrant |

---

## 🧠 RAG Pipeline Internals

**🔹 Retrieval Step**

- Vectorize query

- Search in Qdrant

- Get top-k chunks with scores

**🔹 Augmentation**

- Merge:

  - context chunks
  
  - session memory

**🔹 Generation**

- Gemini API produces final answer

- Citations formatted & returned

---

## 🎯 Key Features
| Feature |	Benefit |
|------|--------------|
| Session-based storage	| Multi-document conversations |
| Chunk-level citations	| Accurate reference tracking |
| Memory-aware chat	| More natural responses |
| Streamlit UI	|Clean and simple |
| FastAPI backend	| High-performance processing |
| Docker Qdrant	| Zero-config vector DB |

---

## 📝 Example Output

**❓ Query**

"Give me a summary of the project abstract."

**💡 Answer**

(Generated by LLM + retrieved chunks)

**📚 Citations**

- Project Abstract.pdf (chunk 1/2)

- Project Abstract.pdf (chunk 2/2)

---

## 🤝 Contributing

Pull requests are welcome!
Feel free to open issues or suggest improvements.

---

## 📜 License

MIT License


