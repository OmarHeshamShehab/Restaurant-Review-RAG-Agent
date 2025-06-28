# 🍕 Local AI RAG-Powered Restaurant Q&A Agent

A lightweight, local-first AI agent that uses Retrieval-Augmented Generation (RAG) to intelligently answer user questions about a pizza restaurant based on realistic customer reviews.

## ✨ Features

- 🔍 **RAG-based Question Answering**: Combines LLM generation with context-retrieved restaurant reviews.
- 🧠 **LLM-Powered**: Runs on [Ollama](https://ollama.ai) with support for models like LLaMA 3.
- 🗃️ **Vector Search**: Uses vector embeddings to semantically retrieve the most relevant reviews.
- 🔌 **Offline-Ready**: All components can run locally—no need for cloud APIs.
- 🧪 **Interactive Shell**: Ask any question, get smart answers backed by real reviews.

---

## 🚀 Getting Started

### 📦 Requirements

Install dependencies from `requirements.txt`:

```bash
pip install -r requirements.txt
```

Ensure you have `ollama` installed and a supported model (e.g., `llama3`) pulled locally:

```bash
ollama pull llama3
```

### ▶️ Running the Agent

```bash
python main.py
```

You'll be prompted to ask a question. Type `q` to quit the session.

---

## 🧩 Project Structure

```bash
.
├── main.py                  # Core logic: combines retrieval and generation
├── vector.py                # Vector retriever and document loading
├── realistic_restaurant_reviews.csv  # Source data for retrieval
├── requirements.txt         # Python dependencies
└── README.md                # Project overview
```

---

## 🧠 How It Works

1. **Load Reviews**: Parses a CSV of realistic restaurant reviews.
2. **Embed Documents**: Converts them into semantic vectors using a local embedding model.
3. **Retrieve**: Finds the most relevant reviews based on user input.
4. **Prompt**: Formats retrieved reviews and the question into a prompt template.
5. **Generate**: Uses a local LLM (via LangChain + Ollama) to answer based on the retrieved context.

### Prompt Template Example:

```
You are an expert in answering questions about a pizza restaurant.

Here are some relevant reviews: {reviews}

Here is the question to answer: {question}
```

---

## 📊 Example Questions

- "What do customers say about the crust?"
- "Are there complaints about service?"
- "What dishes are most popular?"

---

## 🛠️ Dependencies

- `langchain`
- `langchain_ollama`
- `pandas`
- `faiss-cpu` or another vector database backend
- `openai` (if using any fallback embedding models)
