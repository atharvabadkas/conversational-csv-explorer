# 📊 Conversational CSV Explorer  
**RAG-Powered Dataset Query & Visualization with Streamlit + FastAPI + LLaMA2**

---

## 📖 Overview

This application allows users to upload CSV files and query the data using natural language. It's built with a Retrieval-Augmented Generation (RAG) pipeline using LangChain, FAISS, HuggingFace embeddings, and LLaMA2. The app supports both intelligent data querying and real-time visualizations such as bar, line, and scatter plots.

It features a **Streamlit frontend** for intuitive user interaction and a **FastAPI backend** for file handling, embedding management, and query orchestration.

---

## 🚀 Features

- 📁 Upload and analyze CSV datasets interactively  
- 🧠 Natural language queries via LLaMA2 and LangChain  
- 📌 RAG-powered context retrieval using HuggingFace + FAISS  
- 📊 Generate bar, line, and scatter plots on demand  
- 📂 View dataset structure, columns, and stats instantly  
- 🔁 Supports chunked embedding with semantic similarity search  
- 🧰 Query classification and prompt templating  

---

## 🛠 Tech Stack Used

| Layer             | Tool / Framework        |
|------------------|-------------------------|
| UI               | Streamlit               |
| Backend API      | FastAPI                 |
| LLM              | LLaMA2                  |
| Framework        | LangChain               |
| Embeddings       | HuggingFace (MiniLM)    |
| Vector DB        | FAISS                   |
| Data Processing  | Pandas                  |
| Visualization    | Matplotlib, Seaborn     |

---

## ⚙️ Code Breakdown

### `streamlit_app.py`
Handles the user interface: uploading files, accepting queries, displaying answers, and rendering plots.

### `app.py`
FastAPI backend with endpoints for:
- Uploading CSVs  
- Query handling  
- Generating visualizations  
- Managing CORS and session state  

### `main_agent.py`
The brain of the system:
- Classifies query types  
- Retrieves relevant chunks from FAISS  
- Generates LLM responses  
- Validates results  

### `data_processor.py`
Handles:
- Loading CSVs into Pandas DataFrames  
- Listing available datasets  
- Providing schema and column information  

### `visualizer.py`
Renders:
- Bar plots  
- Line plots  
- Scatter plots  
using Matplotlib + Seaborn

### `conversation_memory.py`
Maintains context by tracking user messages in a temporary session memory.

---

## 🔄 RAG Workflow

1. **Query Understanding:**  
   Queries are classified as metadata, aggregation, or comparison.

2. **Chunked Retrieval:**  
   - CSV data is chunked using `RecursiveCharacterTextSplitter`  
   - Chunk size: 500 characters  
   - Overlap: 50 characters  

3. **Embedding Generation:**  
   - Uses HuggingFace `all-MiniLM-L6-v2` to convert text chunks into dense vectors.

4. **Context Retrieval:**  
   - FAISS searches for semantically similar chunks.

5. **Response Generation:**  
   - LLaMA2 processes the prompt using retrieved context.

6. **Verification:**  
   - Results are validated against the original data for accuracy.

---

## 📦 CSV Handling & Conversion

1. Upload CSV via Streamlit  
2. File is saved on the backend  
3. Loaded into a Pandas DataFrame  
4. Text is embedded using HuggingFace  
5. Embeddings are stored in FAISS  
6. Context is retrieved for every query  
7. Answers and visualizations are generated accordingly

> ✅ No SQL conversion — data remains in CSV/Pandas format

---

## 📊 Visualizations

- Powered by Matplotlib and Seaborn  
- Types: Bar, Line, Scatter  
- Frontend selects type + columns  
- Backend generates and sends plots for rendering

---

## 🧠 LangChain + LLM Integration

- **LangChain**: Coordinates query → retrieval → generation  
- **LLaMA2**: Handles natural language understanding + response generation  
- **Prompt Templates**: Guide the model using schema + sample data  
- **Session Agent**: Orchestrates query type detection, response formatting, and scoring

---

## 📈 Performance Tips

To improve speed and quality:
- Enable async FastAPI endpoints  
- Tune chunk size and overlap  
- Optimize embedding batch sizes  
- Use caching for repeated queries  
- Enhance prompt engineering  

---

## 🧪 Troubleshooting Incorrect Answers

- Refine the prompt templates  
- Improve semantic chunk retrieval  
- Add more context in the chunk  
- Log errors and edge cases  
- Use prompt feedback loops  

---

## 📌 Future Enhancements

- Multi-file support and comparisons  
- Persistent memory / chat history  
- More plot types (histograms, heatmaps)  
- LangChain Tools + Agents integration  
- Dockerized deployment

---
