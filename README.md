# 🔍 FinRAG-Assistant – Context-Aware Retrieval-Augmented Generation Assistant

## 📘 Description

FinRAG-Assistant harnesses the power of **Retrieval-Augmented Generation (RAG)** to deliver intelligent, context-aware insights by integrating information from diverse and dynamic document sources. It is designed to assist analysts, professionals, and decision-makers by synthesizing relevant, accurate, and up-to-date content across domains such as business, research, policy, and more.

---

## 🎯 Objective

To assist analysts, professionals, and decision-makers by providing **accurate, context-aware insights** sourced directly from uploaded documents. FinRAG-Assistant eliminates hallucinations common in chatbots by grounding responses in the actual content.

---

## 💡 How Can It Be Useful?

1. **Efficient Data Retrieval** – Quickly retrieves relevant documents, market data, and reports from multiple sources, saving time and effort in manual collection.
2. **Comprehensive Analysis** – Generates insightful summaries and detailed analysis to help users understand a topic’s depth, sentiment, or trends.
3. **Up-to-date Information** – Ensures users have access to the latest information and developments, enabling timely and strategic decision-making.

---

## ⚙️ RAG Pipeline Steps

### 1. Indexing
- Parsing documents (PDF, DOCX, etc.)
- Splitting content into smaller chunks
- Creating semantic embeddings
- Upserting vectors into MongoDB Atlas

### 2. Retrieval
- Rewriting queries for clarity
- Performing semantic search
- (Optional) Web retrieval augmentation

### 3. Generation
- Using LLM (Google Gemini) to generate a factual answer
- Validating output and re-triggering retrieval if needed

---

## 🧠 How It Works

1. **Document Ingestion**
   - Parse supported files using `LlamaParse`
   - Split content into overlapping chunks for embedding

2. **Vector Indexing**
   - Create semantic embeddings using **Google Generative AI**
   - Store them in **MongoDB Atlas Vector Store**

3. **Query Handling**
   - User asks a question via web UI
   - Perform **semantic search** to fetch top-matching document chunks
   - Pass relevant context and the query to a **Google Gemini LLM** via LangChain

4. **Answer Generation**
   - Generate concise, grounded responses using RAG architecture

---

## 🛠️ Tech Stack

| Component            | Technology                          |
|----------------------|--------------------------------------|
| Backend              | Python, Flask                       |
| Language Model       | Google Gemini (via LangChain)       |
| Document Parsing     | LlamaParse                          |
| Embedding Model      | Google Generative AI Embeddings     |
| Vector Database      | MongoDB Atlas Vector Search         |
| LLM Orchestration    | LangChain                           |
| Frontend             | HTML, CSS, JS via Flask templates   |
| Config Management    | python-dotenv (`.env` file)         |

---

## 🚀 Features

- ✅ Plug-and-play RAG system
- ✅ Works with PDFs, DOCX, TXT, PPTX, and more
- ✅ Intelligent document parsing with `LlamaParse`
- ✅ LLM-powered QA grounded in your data
- ✅ Fast semantic retrieval using vector search
- ✅ Extensible to web retrieval or other vector DBs (e.g., Pinecone)

---

## 📂 File Structure

```
FinRAG-Assistant/
├── app.py                # Flask server
├── indexer.py            # Document parser + vector store indexer
├── query_processor.py    # RAG pipeline using LangChain
├── requirements.txt      # Dependencies
├── templates/
│   └── index.html        # UI interface
├── data/                 # Folder where you place your documents
├── .env                  # Your API keys (not committed)
```

---

## ⚙️ How to Run the Project

### 1. 🧪 Clone the Repository

```bash
git clone https://github.com/arrnavgg/FinRAG-Assistant.git
cd FinRAG-Assistant
```

### 2. 🐍 Set Up Virtual Environment (Optional but Recommended)

```bash
python -m venv venv
# Windows
venv\Scripts\activate
# Mac/Linux
source venv/bin/activate
```

### 3. 📦 Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. 🔐 Configure Environment Variables

Create a `.env` file in the root directory:

```env
LLAMA_INDEX=your_llama_parse_api_key
GOOGLE_API_KEY=your_google_genai_key
MONGO_URI=your_mongodb_atlas_uri
LANGCHAIN_API_KEY=your_langchain_key
```

> Note: Use free-tier or trial APIs where possible for testing

---

### 5. 📄 Add Documents

Place your `.pdf`, `.docx`, `.txt`, `.csv`, etc. files in the `data/` folder.

---

### 6. 🧠 Run the Indexer

This step parses, chunks, embeds, and upserts documents to MongoDB.

```bash
python indexer.py
```

---

### 7. 💬 Start the Flask App

```bash
python app.py
```

Then go to `http://localhost:5000` in your browser to interact.

---

## 🖼️ Sample Use Case

> User: “What were Apple’s major sources of revenue in Q4 2023?”

The system:
- Retrieves relevant chunks from the Apple financial report
- Passes them to Gemini via LangChain
- Returns a grounded, concise answer

---

## 👨‍💻 Author

**Arnav Gupta**  
🟢 GitHub: [arrnavgg](https://github.com/arrnavgg)  
📫 Reach out via GitHub issues for feedback or questions!

---

## 🙏 Acknowledgments

- [LangChain](https://www.langchain.com/)
- [MongoDB Atlas](https://www.mongodb.com/)
- [Google Generative AI](https://makersuite.google.com/)
- [LlamaParse](https://www.llamaindex.ai/)
