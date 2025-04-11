# LLM-Embeddings: A Custom RAG Implementation

This project is my personal exploration into Retrieval-Augmented Generation (RAG) using LangChain and OpenAI’s models. I built this demo to solidify my understanding of important NLP concepts, including embeddings, document chunking, and the use of vector databases for semantic search.

The core idea behind the project is to show how external context—retrieved from pre-processed documents—can be integrated with a language model to produce more informed and precise answers.

---

## What I Learned

- **Embeddings & Contextual Representations:**  
  I explored how text can be transformed into numerical embeddings. This process allows the model to “understand” semantic relationships within the documents.

- **Document Chunking:**  
  Chunking large documents into smaller pieces is crucial. I learned that preserving context through overlapping chunks enhances retrieval accuracy and ensures that critical information isn’t lost.

- **Vector Search & Databases:**  
  Building an in-memory vector store demonstrated the power of combining vector search with retrieval-based methods. This approach minimizes hallucination by grounding generated responses in real, retrievable content.

- **Practical RAG Pipeline:**  
  The end-to-end process—from document loading to answering queries—showed me how to integrate various components (embedding generation, vector storage, context retrieval, and response generation) into a unified RAG system.

---

## Repository Structure
```
LLM-EMBEDDINGS/
├── documents/
│   ├── sample1.txt
│   └── sample2.txt
├── node_modules/
├── utils/
│   ├── chromaClient.js
│   └── documentUtils.js
├── .env
├── .gitignore
├── index.js
├── package-lock.json
├── package.json
└── README.md
```



---

## Setup Instructions

### 1. Clone the Repository

Clone this repository to your local machine:

### 2. Environment Configuration
Create a .env file in the root directory and add your OpenAI API key:

OPENAI_API_KEY=your-openai-api-key-here
Reminder: Add .env to your .gitignore to protect your API key if you share the repository publicly.

### 3. Install Dependencies
Ensure you are in the project directory and run:

npm install

### 4. Run the Demo
Start the demo by running:

node index.js

---

## What the Demo Does

- **Document Loading**
    The demo loads two text documents from the documents/ folder using LangChain loaders.
- **Chunking**
    It splits the documents into smaller chunks (8 in total) using a recursive text splitter. This ensures that each chunk fits within model token limits while still retaining important context.
- **Vector Store Creation**
    The chunks are converted into embeddings using OpenAI's text-embedding-ada-002 model and are stored in an in-memory vector store for quick retrieval.
- **Query Processing**
    The demo processes three predefined queries by retrieving the most relevant document chunks from the vector store.
    It then uses a ChatOpenAI model (gpt-3.5-turbo) to generate responses based on the augmented context.
    The generated responses include citations (e.g., [Document 1]) indicating the source of the context.

---

## Sample Output

```🚀 Starting RAG Demo with LangChain and OpenAI

📚 Loading documents...
Looking for documents in: /path/to/LLM-Embeddings-Demo/documents
Loaded 2 documents.

✂️ Splitting documents into chunks...
Created 8 chunks.

🧠 Creating in-memory vector store...
Vector store created successfully.

❓ Question: What is RAG and what are its key components?
Retrieving relevant documents...
Found 2 relevant documents.
Generating answer using context...

🔍 Answer:
RAG stands for Retrieval-Augmented Generation, which enhances a language model by incorporating external context before generating responses. Its key components include document ingestion, chunking, embedding generation, vector storage, context retrieval, and response generation [Document 1].

... (other queries and answers follow)

RAG demo completed.
```
