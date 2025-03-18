# 🚀 **DeepSeek RAG Chatbot 3.0 – Now with GraphRAG & Chat History Integration!**
**(100% Free, Private (No Internet), and Local PC Installation)**  

[![Your Video Title](https://img.youtube.com/vi/xDGLub5JPFE/0.jpg)](https://www.youtube.com/watch?v=xDGLub5JPFE "Watch on YouTube")

🔥 **DeepSeek + NOMIC + FAISS + Neural Reranking + HyDE + GraphRAG + Chat Memory = The Ultimate RAG Stack!**  

This chatbot enables **fast, accurate, and explainable retrieval of information** from PDFs, DOCX, and TXT files using **DeepSeek-7B**, **BM25**, **FAISS**, **Neural Reranking (Cross-Encoder)**, **GraphRAG**, and **Chat History Integration**.  

---

## **🔹 New Features in This Version**

- **GraphRAG Integration:** Builds a **Knowledge Graph** from your documents for more **contextual** and **relational** understanding.  
- **Chat Memory History Awareness:** Maintains context by referencing **chat history**, enabling more **coherent** and **contextually relevant** responses.  
- **Improved Error Handling:** Resolved issues related to **chat history clearing** and other minor bugs for a **smoother user experience**.  

---
## **Upcoming Features**
 # You can select a model from the UI interface (any Ollama model).

Example: Users can choose between models like mistral, gemma, or llama3 from a dropdown menu.
# The chat section suggests relevant questions based on the document.

Example: If the document is about "Machine Learning Basics," suggested questions could be:
What is supervised learning?
How does gradient descent work?
What are the common evaluation metrics for ML models?
# Different pipelines are available for various RAG (Retrieval-Augmented Generation) methods.

Example:
Basic RAG Pipeline: Uses FAISS for retrieval and a simple prompt format.
Advanced RAG Pipeline: Uses ChromaDB with metadata filtering for more precise document retrieval.

# Different data stores and similarity search techniques are used.

Example:
Data Stores: PostgreSQL, Pinecone, Weaviate, ChromaDB.
Similarity Search Techniques: Cosine similarity, Euclidean distance, Jaccard similarity.
  
# *Installation & Setup**

You can install and run the **DeepSeek RAG Chatbot** in one of two ways:

1. **Traditional (Python/venv) Installation**  
2. **Docker Installation** (ideal for containerized deployments)

---

## **1️⃣ Traditional (Python/venv) Installation**

### **Step A: Clone the Repository & Install Dependencies**
```
git clone https://github.com/SaiAkhil066/DeepSeek-RAG-Chatbot.git
cd DeepSeek-RAG-Chatbot

# Create a virtual environment
python -m venv venv

# Activate your environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Upgrade pip (optional, but recommended)
pip install --upgrade pip

# Install project dependencies
pip install -r requirements.txt
```

### **Step B: Download & Set Up Ollama**
1. **Download Ollama** → [https://ollama.com/](https://ollama.com/)  
2. **Pull the required models**:
   ```
   ollama pull deepseek-r1:7b
   ollama pull nomic-embed-text
   ```
   *Note: If you want to use a different model, update `MODEL` or `EMBEDDINGS_MODEL` in your environment variables or `.env` file accordingly.*

### **Step C: Run the Chatbot**
1. Make sure **Ollama** is running on your system:
   ```
   ollama serve
   ```
2. Launch the Streamlit app:
   ```
   streamlit run app.py
   ```
3. Open your browser at **[http://localhost:8501](http://localhost:8501)** to access the chatbot UI.

---

## **2️⃣ Docker Installation**

### **A) Single-Container Approach (Ollama on Your Host)**

If **Ollama** is already **installed on your host machine** and listening at `localhost:11434`, do the following:

1. **Build & Run**:
   ```
   docker-compose build
   docker-compose up
   ```
2. The app is now served at **[http://localhost:8501](http://localhost:8501)**. Ollama runs on your host, and the container accesses it via the specified URL.

### **B) Two-Container Approach (Ollama in Docker)**

If you prefer **everything** in Docker:
```
version: "3.8"

services:
  ollama:
    image: ghcr.io/jmorganca/ollama:latest
    container_name: ollama
    ports:
      - "11434:11434"

  deepgraph-rag-service:
    container_name: deepgraph-rag-service
    build: .
    ports:
      - "8501:8501"
    environment:
      - OLLAMA_API_URL=http://ollama:11434
      - MODEL=deepseek-r1:7b
      - EMBEDDINGS_MODEL=nomic-embed-text:latest
      - CROSS_ENCODER_MODEL=cross-encoder/ms-marco-MiniLM-L-6-v2
    depends_on:
      - ollama
```

Then:
```
docker-compose build
docker-compose up
```
Both **Ollama** and the chatbot run in Docker. Access the chatbot at **[http://localhost:8501](http://localhost:8501)**.


### **But consider step A) for comfort..**
---

# **How the Chatbot Works**

1. **Upload Documents**: Add PDFs, DOCX, or TXT files via the sidebar.  
2. **Hybrid Retrieval**: Combines **BM25** and **FAISS** to fetch the most relevant text chunks.  
3. **GraphRAG Processing**: Builds a **Knowledge Graph** from your documents to understand relationships and context.  
4. **Neural Reranking**: Uses a **Cross-Encoder** model for reordering the retrieved chunks by relevance.  
5. **Query Expansion (HyDE)**: Generates hypothetical answers to **expand** your query for better recall.  
6. **Chat Memory History Integration**: Maintains context by referencing previous user messages.  
7. **DeepSeek-7B Generation**: Produces the final answer based on top-ranked chunks.

---

## **🔹 Why This Upgrade?**

| Feature                       | Previous Version            | New Version                        |
|------------------------------|-----------------------------|------------------------------------|
| **Retrieval Method**         | Hybrid (BM25 + FAISS)      | Hybrid + **GraphRAG**             |
| **Contextual Understanding** | Limited                    | **Enhanced with Knowledge Graphs** |
| **User Interface**           | Standard                   | **Customizable + Themed Sidebar**  |
| **Chat History**             | Not Utilized               | **Full Memory Integration**        |
| **Error Handling**           | Basic                      | **Improved with Bug Fixes**        |


---

## **📌 Contributing**

- **Fork** this repo, submit **pull requests**, or open **issues** for new features or bug fixes.  
- We love hearing community suggestions on how to extend or improve the chatbot.

---

### **🔗 Connect & Share Your Thoughts!**

Got feedback or suggestions? Let’s discuss on [**Reddit**](https://www.reddit.com/user/akhilpanja/)! 🚀💡

---

**Enjoy building knowledge graphs, maintaining conversation memory, and harnessing powerful local LLM inference—all from your own machine.**  
_The future of retrieval-augmented AI is here—no internet required!_
