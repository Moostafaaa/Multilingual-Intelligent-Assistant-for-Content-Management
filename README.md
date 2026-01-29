# 🤖 Multilingual Intelligent Content Assistant

A high-performance, asynchronous FastAPI service that leverages **Hugging Face Transformers** to generate, summarize, translate, and perform question-answering on specific topics.

## 🌟 Overview

This project implements a complete NLP content management pipeline:

1. **Content Generation:** Uses `GPT-2` to draft informative text based on a user-provided topic.
2. **Summarization:** Utilizes `DistilBART` to condense the generated text into a concise summary.
3. **Translation:** Employs a specialized English-to-Egyptian-Arabic translator (`NAMAA-Space`) to make the summary locally accessible.
4. **Question Answering:** Uses `DistilBERT` to answer specific user questions based on the context of the generated content.

## 🚀 Key Features

* **Optimized Inference:** Automatic device detection (GPU/CUDA support).
* **Modular Pipeline:** Uses Hugging Face's `pipeline` API for clean, maintainable code.
* **Notebook Compatible:** Implements `nest_asyncio` and `threading` to run a live FastAPI server directly within Jupyter/Colab.
* **Schema Validation:** Strong typing using Pydantic models for predictable API interactions.

---

## 🛠️ Technical Stack

* **Framework:** FastAPI
* **Language:** Python 3.10+
* **AI Engine:** Hugging Face Transformers (PyTorch)
* **Server:** Uvicorn

---

## 📥 Installation & Setup

1. **Clone the repository:**
```bash
git clone https://github.com/Moostafaaa/Multilingual-Intelligent-Assistant-for-Content-Management.git
cd your-repo-name

```


2. **Install dependencies:**
```bash
pip install fastapi uvicorn transformers torch nest_asyncio requests

```


3. **Run the Notebook/Script:**
If running in a local environment, you can start the server via terminal:
```bash
uvicorn main:app --reload

```



---

## 📡 API Documentation

### **Endpoint:** `POST /ai-assistant`

**Request Body:**

```json
{
  "topic": "Vitamins Importance",
  "question": "How do Vitamins help health of people?"
}

```

**Response Example:**

```json
{
  "topic": "Vitamins Importance",
  "generated_text": "Explain the impact of Vitamins Importance: Vitamins play a crucial role...",
  "summary": "Vitamins are essential nutrients that support immune function...",
  "translated_summary_ar": "الفيتامينات هي عناصر غذائية أساسية بتدعم وظائف المناعة...",
  "question_answer": {
    "question": "How do Vitamins help health of people?",
    "answer": "support immune function"
  }
}

```

---

## 🧠 Model Details

| Task | Model Used |
| --- | --- |
| **Generation** | `gpt2` |
| **Summarization** | `sshleifer/distilbart-cnn-6-6` |
| **Translation** | `NAMAA-Space/masrawy-english-to-egyptian-arabic-translator-v2.9` |
| **QA** | `distilbert-base-cased-distilled-squad` |

---
