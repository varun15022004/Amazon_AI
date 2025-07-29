# Amazon_AI
Here's a `README.md` file for your RAG-based Question-Answering system using LangChain, FAISS, HuggingFace, and Groq with Gradio UI support. This also includes **setup instructions**, **known issues (missing Groq API key)**, and **usage flow**.

---

````markdown
# 📊 Amazon 10-Q Financial QA System using RAG (LangChain + FAISS + Groq)

This project implements a Retrieval-Augmented Generation (RAG) pipeline that allows you to upload Amazon 10-Q financial reports (PDF), convert them into markdown using `docling`, split the content, embed using Sentence Transformers, and retrieve answers to user queries via Groq-hosted LLaMA3 model.

## ✅ Features

- 📄 PDF to Markdown conversion via `docling`
- 📚 Semantic chunking using markdown headers
- 🧠 Vector store using `FAISS` and `sentence-transformers`
- 🤖 RAG-based QA powered by `Groq`'s `llama3-8b-8192`
- 🎛️ Interactive interface using Gradio
- 🔁 MMR-based semantic retrieval (top 3 relevant chunks)

---

## 🚀 Installation

Ensure you're running this in a Python 3.10+ environment (e.g., Google Colab or local virtualenv):

```bash
pip install langchain langchain-community langchain-core langchain-groq \
            faiss-cpu sentence-transformers docling gradio
````

---

## 🔧 Configuration

### Step 1: Groq API Key 🔑

This project uses **Groq's LLaMA3 model** to power the QA system.

> **❗ You MUST set your Groq API key for this to work.**

#### How to get it:

1. Go to [https://console.groq.com/keys](https://console.groq.com/keys)
2. Sign in and generate your API key.
3. Add your key in the line:

```python
model = ChatGroq(model_name="llama3-8b-8192", api_key="YOUR_API_KEY_HERE")
```

---

## 🛠️ Usage Flow

### 🔹 Programmatic (Console)

1. Set `source` PDF path (`/content/amazon-10-q-q3-2024.pdf`)
2. Convert → Split → Embed → Retrieve
3. Ask pre-defined or custom questions
4. Stream output from Groq model

### 🔹 Interactive (Gradio UI)

Run the script, then:

1. Upload your 10-Q PDF via Gradio file input
2. Once processed, ask financial questions
3. Output will be shown in a textbox

```python
gr.Blocks()  # Gradio App Interface
```

---

## 📁 Directory & File Structure

```
📦 project/
├── amazon-10-q-q3-2024.pdf        # Example 10-Q file (user provided)
├── app.py                         # Main code file
├── README.md                      # You're reading it!
```

---

## 📌 Known Issues

### 1. ⛔ `KeyboardInterrupt` or Timeout on PDF Conversion

* `docling` may take several minutes especially with table-heavy PDFs.
* Try reducing the number of pages or use a lighter PDF for testing.

### 2. ❌ `Missing Groq API Key`

* You must supply `api_key="..."` in `ChatGroq(...)` or it will throw runtime errors.
* Make sure you're not accidentally committing it to public repos.

### 3. ⚠️ `HF_TOKEN` warning (Optional)

* Hugging Face models may raise auth warning but work fine without token for public models.

---

## 🤖 Predefined Questions (Sample)

```text
- What was Amazon’s total revenue in Q3 2024?
- What was the net income for Q3 2024?
- What were earnings per share (EPS)?
- How much was spent on operating expenses?
- What were AWS segment results?
- Were there any major lawsuits or tax contingencies?
```

You can edit or extend these in the `questions` list in the script.

---

## 📞 Support

Feel free to open an issue or discuss if you encounter any specific errors with FAISS, LangChain, or Groq models.

---

## 📜 License

This project is intended for educational, academic, and non-commercial purposes only. Please comply with the terms of use of each dependency (e.g., Hugging Face, Groq).

---

Made with ❤️ using [LangChain](https://www.langchain.com/), [Groq](https://groq.com/), and [Gradio](https://www.gradio.app/)

```

---

Let me know if you'd like this in a downloadable format or want the code split into modular files (e.g., `app.py`, `qa_chain.py`, `utils.py`).
```
