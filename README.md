# 🧠 PDF-RAG (Retrieval-Augmented Generation on PDFs)

A full-stack AI project that allows users to **upload PDFs and ask questions** about their content using natural language.  
It leverages **LangChain**, **OpenAI**, and **Qdrant** for document embeddings and semantic search, providing accurate context-aware responses.

| Technology          | Purpose                                                                |
| ------------------- | ---------------------------------------------------------------------- |
| **Clerk**           | Authentication and user management (login/signup, sessions).           |
| **LangChain**       | Orchestrates document parsing, embedding, and OpenAI interactions.     |
| **OpenAI**          | Used for generating responses to user questions.                       |
| **Qdrant**          | Vector database for semantic search and storing embeddings.            |
| **BullMQ + Valkey** | Background job processing (e.g., embedding large PDFs asynchronously). |
| **Docker Compose**  | Spins up required backend services (Qdrant, Valkey).                   |

🧾 Features

PDF upload and content parsing.

Context-based question answering using embeddings.

Authenticated user flow with Clerk.

Distributed background jobs for scalability.

Vector-based document retrieval with Qdrant.

🧰 Folder Structure

pdf-rag/
├── client/ # Frontend (Next.js + Clerk)
├── server/ # Backend (Express + LangChain + OpenAI)
├── Dockerfile
├── docker-compose.yml
└── README.md

## 🧩 Architecture Overview

- **Client:** Next.js app with **Clerk** for authentication and **Tailwind CSS** for styling.
- **Server:** Express backend powered by **LangChain**, **Qdrant**, **OpenAI**, and **BullMQ** for background jobs.
- **Vector Database:** **Qdrant** (for storing and querying embeddings).
- **Queue System:** **Valkey** (Redis-compatible) used with BullMQ.
- **Containerization:** Managed through **Docker Compose** for Qdrant and Valkey.

---

## 🧰 Example .env for server

API_KEY=your_openai_api_key_here
QDRANT_URL=http://localhost:6333
REDIS_HOST=localhost
REDIS_PORT=6379
PORT=8000

## ⚙️ Setup & Run Instructions

### 🐳 1. Start Required Services

In the root directory (parent repo):

```bash
docker compose up -d
```

This starts:

Valkey on port 6379

Qdrant on port 6333

## Client

cd client
pnpm install
pnpm dev

Runs the Next.js frontend at http://localhost:3000

## Server

cd server
pnpm install
pnpm dev
pnpm dev:worker # for background processing jobs

Server runs on http://localhost:8000
