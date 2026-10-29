# 📚 AI Study Buddy — PDF-Based RAG Assistant

AI Study Buddy is an AI-powered learning assistant that lets users upload PDF documents, ask questions about their content, and receive context-aware answers generated using Google's Gemini API.

The application uses **Retrieval-Augmented Generation (RAG)** to retrieve relevant passages from uploaded documents before generating answers, helping users study and understand their learning materials more effectively.

## ✨ Features

- **PDF Processing:** Extracts readable text and page numbers from PDF documents.
- **Text Chunking:** Splits document text into smaller, overlapping chunks for retrieval.
- **Semantic Search:** Uses sentence embeddings and FAISS to retrieve relevant passages.
- **AI-Powered Answers:** Uses the Gemini API to generate answers grounded in retrieved PDF content.
- **Page References:** Includes relevant page information to help users locate source material.
- **Chat History:** Supports follow-up questions using recent conversation context.
- **Index Persistence:** Saves processed chunks and the FAISS index locally to reduce repeated embedding computation.
- **Environment-Based Configuration:** Keeps API credentials outside the source code.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core application logic |
| Streamlit | Interactive web interface |
| Google Gemini API | Answer generation |
| Sentence Transformers | Text embeddings |
| FAISS | Similarity search |
| PyPDF | PDF text extraction |
| NumPy | Numerical operations |
| python-dotenv | Local environment configuration |

## 🔄 How It Works

1. **Upload:** The user uploads a text-based PDF.
2. **Extract:** Text and page numbers are extracted from the document.
3. **Chunk:** Extracted text is split into smaller overlapping chunks.
4. **Embed:** Sentence Transformers converts chunks into numerical vectors.
5. **Index:** FAISS stores the vectors for efficient similarity search.
6. **Retrieve:** The user's question is embedded and matched against relevant chunks.
7. **Generate:** Retrieved passages and recent conversation context are sent to Gemini.
8. **Answer:** The application displays the generated answer and relevant source passages.

## 🧰 Prerequisites

- Python 3.12
- A Google Gemini API key
- Git
- A supported PDF containing extractable text

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd ai-study-buddy
```

### 2. Create and activate a virtual environment

**Windows PowerShell**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file in the project root:

```env
GEMINI_API_KEY=your_gemini_api_key
GEMINI_MODEL=your_working_gemini_model
```

Replace the placeholder values with your own credentials and a model available to your API account.

**Security:** Never commit `.env` or expose your API key in source code, screenshots, or public repositories.

### 5. Run the application

```bash
streamlit run app.py
```

Open the local URL printed in the terminal by Streamlit.

## ☁️ Deployment

The application can be deployed using Streamlit Community Cloud.

1. Push the project to GitHub.
2. Create an app and select the repository, branch, and `app.py` entry point.
3. Add `GEMINI_API_KEY` and `GEMINI_MODEL` in the app's Secrets settings.
4. Deploy and verify the application using a sample PDF.

Cloud deployment may require dependency adjustments because sentence-transformer models and PyTorch can increase build size and startup time.

**Note:** The current FAISS index and chunk files are stored locally. They are not included in Git because the `storage/` directory is ignored. A fresh deployment may therefore need the PDF to be processed again. Persistent storage or a suitable hosted vector store can be added later.

## 🔐 Security and Limitations

- API credentials must be stored in environment variables or the deployment platform's Secrets settings.
- Answers depend on the quality and relevance of the retrieved PDF passages.
- Scanned PDFs may require OCR before their content can be searched.
- The current implementation is designed around one active saved PDF index.
- Local index persistence does not automatically provide durable cloud storage.
- Gemini API usage may incur costs or be subject to account-specific quotas and rate limits.

## 🗺️ Future Improvements

- Support multiple PDFs and document collections.
- Improve follow-up question retrieval.
- Add OCR for scanned documents.
- Add source citations with clickable page references.
- Introduce configurable answer length and retrieval settings.
- Add persistent cloud storage for document indexes.
- Improve error handling, file validation, and deployment efficiency.

## 🎯 Learning Outcomes

This project provides hands-on experience with:

- Retrieval-Augmented Generation (RAG)
- Embeddings and semantic search
- Vector indexing with FAISS
- LLM API integration
- Prompt design and context grounding
- Session state and conversational interfaces
- Environment configuration and deployment

## 📄 License

Choose a license before distributing or reusing this project publicly. For example, an MIT License can be added if that matches your intended use.

---

**Built with Python, Streamlit, FAISS, Sentence Transformers, and Google Gemini.**
