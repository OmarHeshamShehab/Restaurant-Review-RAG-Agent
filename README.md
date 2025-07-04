# 🍕 Pizza Restaurant Review QA System

An interactive question-answering app that uses **LangChain**, **Ollama's LLaMA 3.2**, and **Chroma vector search** to answer questions based on real pizza restaurant reviews.

---

## ✅ Features
- Parses real reviews and creates vector embeddings using `mxbai-embed-large`
- Retrieves the top 5 relevant reviews for each question
- Uses LLaMA 3.2 to answer questions contextually
- Reuses a persistent local vector store to speed up future runs

---

## 📂 File Structure
```
.
├── main.py                      # Runs the QA loop with LangChain + LLaMA 3.2
├── vector.py                    # Loads CSV, embeds reviews, builds Chroma vector DB
├── realistic_restaurant_reviews.csv  # Dataset with Title, Review, Rating, Date
├── chrome_langchain_db/         # (Auto-created) Vector store for embeddings
```

---

## ⚙️ Requirements

- Python 3.8+
- [Ollama](https://ollama.com/) installed and running locally

### Install Python packages:

```bash
pip install pandas langchain langchain-core langchain-community langchain-chroma langchain-ollama
```

### Pull required Ollama models:

```bash
ollama pull llama3.2
ollama pull mxbai-embed-large
```

---

## 🚀 How to Run

```bash
python main.py
```

Then ask a question like:

- "What do people think about the crust?"
- "Is the pizza overpriced?"
- "How’s the atmosphere?"
- "Are the staff friendly?"

Type `q` to quit.

---

## 🗃 Dataset

`realistic_restaurant_reviews.csv` must contain:
- `Title`: Short title of the review
- `Review`: Full review text
- `Rating`: Numerical rating
- `Date`: Date of the review

---

## 🧠 How It Works

1. `vector.py` loads the CSV and generates vector embeddings for each review using `mxbai-embed-large`
2. Stores them in a persistent Chroma vector DB
3. `main.py` takes your question, finds top 5 relevant reviews, and prompts LLaMA 3.2 for an answer

---

## 📌 Notes

- The first run creates the vector database in `chrome_langchain_db`
- Future runs reuse this to avoid re-embedding
- Answers are entirely based on the retrieved review context

