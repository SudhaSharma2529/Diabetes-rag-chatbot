# Diabetes-rag-chatbot
A diabetes information chatbot using RAG, LangChain, Ollama, ChromaDB, and Streamlit.
# 🩸 DiabetesCare — Diabetes Information Assistant

An AI-powered diabetes information chatbot built using **Retrieval-Augmented Generation (RAG)**. It answers general questions about diabetes using a curated knowledge base, helping users understand diabetes types, symptoms, management, and complications.

The project combines **Python, LangChain, Ollama, ChromaDB, and Streamlit** to retrieve relevant information and generate context-grounded responses.

## ✨ Features

- **AI-Powered Chatbot:** Ask questions about diabetes in natural language.
- **Retrieval-Augmented Generation (RAG):** Retrieves relevant information from a curated knowledge base before generating answers.
- **Semantic Search:** Uses embeddings to find relevant document passages.
- **Vector Database:** Stores and retrieves document embeddings using ChromaDB.
- **Local Language Model:** Uses Ollama to run the language model and embedding model locally.
- **Interactive UI:** Provides a chat interface built with Streamlit.
- **Source Transparency:** Displays retrieved source excerpts or document names.
- **Safety-Focused Responses:** Includes a disclaimer and instructions to avoid diagnosis and personalized medication advice.

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Streamlit | Interactive chatbot interface |
| LangChain | RAG pipeline orchestration |
| Ollama | Local language model and embeddings |
| ChromaDB | Vector storage and similarity search |
| nomic-embed-text | Text embedding model |
| Llama 3 | Language model for answer generation |
| PyPDF | PDF document loading |

## 🏗️ Architecture

The chatbot follows a Retrieval-Augmented Generation pipeline:

1. **Document Ingestion:** Loads text and PDF documents from the knowledge base.
2. **Text Chunking:** Splits documents into smaller, overlapping chunks.
3. **Embedding Generation:** Converts text chunks into numerical vector representations.
4. **Vector Storage:** Stores the embeddings in ChromaDB.
5. **Information Retrieval:** Finds relevant document chunks for a user's question.
6. **Answer Generation:** Supplies the retrieved context to the language model to generate a response.
7. **User Interface:** Displays the response through the Streamlit chatbot.

```text
Curated Diabetes Documents
          |
          v
    Document Loading
          |
          v
     Text Chunking
          |
          v
   Embedding Generation
          |
          v
      ChromaDB
          |
          v
    User's Question
          |
          v
  Similarity Search
          |
          v
  Retrieved Context
          |
          v
      Llama 3
          |
          v
   Generated Answer
          |
          v
    Streamlit UI
```

## 📂 Project Structure

```text
healthcare-rag-chatbot/
│
├── app.py
├── README.md
├── PROBLEM_DOMAIN.md
├── requirements.txt
│
├── src/
│   ├── config.py
│   ├── ingest.py
│   └── rag_chain.py
│
├── data/
│   ├── diabetes_types_and_diagnosis.txt
│   ├── diabetes_management.txt
│   └── diabetes_complications_and_emergencies.txt
│
└── vectorstore/   # Generated during ingestion
```

**Key files:**

- `app.py` — Streamlit chatbot interface.
- `src/config.py` — Configuration settings for the RAG pipeline.
- `src/ingest.py` — Loads, processes, embeds, and indexes documents.
- `src/rag_chain.py` — Retrieves relevant content and generates answers.
- `data/` — Contains the diabetes knowledge base.
- `requirements.txt` — Lists Python dependencies.
- `PROBLEM_DOMAIN.md` — Explains the problem statement, solution, and project scope.

## ⚙️ Installation and Setup

### Prerequisites

Install the following before running the application:

- Python 3.10 or later
- Git
- [Ollama](https://ollama.com/)
- The required Ollama models

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/diabetescare-rag-chatbot.git
cd diabetescare-rag-chatbot
```

Replace `YOUR-USERNAME` with your GitHub username.

### 2. Create a Virtual Environment

**Windows:**

```bash
python -m venv .venv
.venv\Scripts\activate
```

**macOS/Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Download the Ollama Models

Make sure Ollama is installed and running.

Pull the embedding model:

```bash
ollama pull nomic-embed-text
```

Pull the language model:

```bash
ollama pull llama3
```

These models are used for document embeddings and answer generation, respectively.

### 5. Build the Knowledge Base

Run the ingestion script from the project root:

```bash
python src/ingest.py
```

This processes the documents in the `data/` directory, generates embeddings, and builds the vector store.

### 6. Run the Application

Start the Streamlit application:

```bash
streamlit run app.py
```

Open the local URL displayed in your terminal, usually:

```text
http://localhost:8501
```

You can now ask questions about diabetes through the chatbot interface.

## 💬 Example Questions

Try asking:

- What is the difference between Type 1 and Type 2 diabetes?
- What is HbA1c?
- What are common symptoms of diabetes?
- What are the common complications of diabetes?
- What is hypoglycemia?
- How can diabetes be managed through lifestyle changes?

The answers depend on the documents available in the knowledge base and the information retrieved for each question.

## 📚 Updating the Knowledge Base

You can expand the chatbot's knowledge by adding relevant `.txt` or `.pdf` documents to the `data/` directory.

After adding or modifying documents, rebuild the vector store:

```bash
python src/ingest.py
```

Restart the application if necessary.

Use reliable, appropriately licensed medical education materials when expanding the knowledge base.

## 🔒 Privacy and Security

- Ollama runs the language model and embedding model locally.
- The application is designed for local execution.
- Avoid adding passwords, API keys, personal information, or confidential documents to the repository.
- Generated vector-store files can be excluded from Git and rebuilt locally.

Local model execution does not, by itself, guarantee that every component or dependency operates entirely offline.

## ⚠️ Limitations and Disclaimer

DiabetesCare is an educational project demonstrating Retrieval-Augmented Generation. It is **not a medical device or a substitute for professional medical advice**.

- It must not be used to diagnose medical conditions.
- It must not be used to prescribe or adjust medication dosages.
- Generated responses may contain errors or omit important information.
- Answer quality depends on the quality and coverage of the knowledge base and the language model.

For personal medical concerns, consult a qualified healthcare professional. Seek urgent medical care for potentially serious symptoms.

## 🚀 Future Improvements

Potential enhancements include:

- Expanding the knowledge base with trusted medical resources.
- Improving retrieval accuracy and answer evaluation.
- Adding conversation history and contextual follow-up questions.
- Implementing automated tests for retrieval and response quality.
- Exploring alternative embedding models and vector databases.
- Deploying the application to a suitable hosting environment.

## 👩‍💻 Learning Outcomes

This project demonstrates practical experience with:

- Retrieval-Augmented Generation (RAG)
- Large Language Models (LLMs)
- Text embeddings and semantic search
- Vector databases
- LangChain pipelines
- Python application development
- Streamlit UI development
- Document processing and knowledge-base construction

## 📄 License

No license has been specified yet. If you plan to make the project open source, choose an appropriate license and add a `LICENSE` file.

---

**Project:** DiabetesCare — Diabetes Information Assistant  
**Category:** Artificial Intelligence / Natural Language Processing  
**Core Concepts:** RAG, LLMs, Semantic Search, Vector Databases
