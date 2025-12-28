# arXade — Semantic Research Paper Discovery Platform

<p align="center">
  <img src="https://img.shields.io/badge/Frontend-Next.js-black?style=for-the-badge&logo=next.js" />
  <img src="https://img.shields.io/badge/Backend-FastAPI-009688?style=for-the-badge&logo=fastapi" />
  <img src="https://img.shields.io/badge/Database-MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white" />
  <img src="https://img.shields.io/badge/AI-Google%20Gemini-4285F4?style=for-the-badge&logo=google" />
  <img src="https://img.shields.io/badge/License-MIT-blueviolet?style=for-the-badge" />
</p>


An AI-powered academic paper discovery platform that enables semantic search through arXiv research papers using vector embeddings and intelligent summarization. Designed to help researchers, students, and academics discover relevant papers through concept-based search rather than traditional keyword matching.


## 🎯 Project Overview

arXade is a full-stack research discovery tool that processes academic papers from arXiv and enables semantic search through vector embeddings. The platform uses Google’s Gemini embedding model to convert paper abstracts, titles, and metadata into high-dimensional vectors, allowing users to search by concepts and ideas rather than exact keyword matches.

### System Architecture

The application consists of three core components:

1. **Data Processing Pipeline**  
   Processes arXiv papers and generates int8-quantized embeddings for efficient storage using the Gemini text-embedding-004 model.

2. **Backend API**  
   FastAPI service with MongoDB Atlas vector search capabilities, providing search and AI summary generation endpoints.

3. **Frontend Interface**  
   Next.js application with interactive visualizations, filtering, and real-time search capabilities.

### Key Workflows

- **Search Workflow**: User query → Frontend → Backend embedding generation → MongoDB vector similarity search → Ranked results  
- **AI Summary Generation**: Automatic contextual summaries generated for search results  
- **Deep Research Analysis**: Multi-paper analysis with mathematical formulations and theoretical context  
- **Visual Analytics**: Charts for category distribution, publication timelines, and research trends

---

## ✨ Key Features

- Semantic vector-based search beyond keyword matching  
- Automated embedding generation with rate limiting and quantization  
- AI-powered contextual paper summaries  
- Deep research analysis across multiple papers  
- Interactive visualizations:
  - Word clouds from abstracts  
  - Category distribution pie charts  
  - Publication timeline views  
  - Relevance scoring and filtering  
- Full LaTeX rendering for mathematical notation  
- Efficient batch processing with int8 quantization (4× storage optimization)  
- Dockerized architecture for local development and deployment  

---

## 🛠️ Tech Stack

### Frontend
- Next.js 15.3 (TypeScript)
- Tailwind CSS 4.0
- Recharts, Visx, Tremor
- KaTeX for LaTeX rendering
- React 19 Hooks
- Custom UI components and animations

### Backend
- FastAPI 0.110.0
- Uvicorn (development)
- Gunicorn (production-ready)
- Pydantic v2.6
- Structured JSON logging

### Database & Search
- MongoDB Atlas with Vector Search
- PyMongo 4.6.2
- Cosine similarity indexing
- int8-quantized vector storage

### AI & Machine Learning
- Google Gemini text-embedding-004
- Gemini 2.0 Flash for summarization
- google-generativeai SDK
- NumPy for vector operations

### DevOps & Tooling
- Docker & Docker Compose
- Git version control
- Environment configuration via python-dotenv

---

## 📁 Folder Structure
```text
arXade/
├── frontend/                # Next.js client
│   ├── src/
│   │   ├── app/             # App Router pages
│   │   ├── components/      # UI & visualizations
│   │   ├── lib/             # API helpers
│   │   └── styles/          # Global styles
│   ├── public/
│   ├── Dockerfile
│   └── package.json
│
├── backend/                 # FastAPI server
│   ├── main.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── data/
│   └── embed.py             # Embedding pipeline
│
├── screenshots/             # UI previews
│   └── home.png
│
├── docker-compose.yml
├── .env.example
├── LICENSE
└── README.md
```

---

## ⚙️ Setup & Installation

### Prerequisites
- Docker & Docker Compose
- MongoDB Atlas account with Vector Search enabled
- Google Gemini API key
---

## ⚙️ Installation Steps

### 1. Clone the Repository

```bash
git clone <repository-url>
cd arXade
````

### 2. Configure Environment Variables

```bash
cp .env.example .env
```

### 3. Start the Application

```bash
docker-compose up
```

### 4. Access Services

* **Frontend:** [http://localhost:3000](http://localhost:3000)
* **Backend API:** [http://localhost:8000](http://localhost:8000)
* **API Documentation:** [http://localhost:8000/docs](http://localhost:8000/docs)

---

## 💡 Use Cases

### Academic Research

* Concept-based discovery of related research
* Semantic similarity search
* Trend exploration via visual analytics

### Student Projects

* Full-stack development practice
* Vector embeddings and AI integration
* Dockerized system design

### Learning & Demonstration

* Portfolio-grade AI project
* Modern web architecture example
* Real-world API and database integration

---

## 📚 Learning Outcomes

* Vector databases and similarity search
* AI embedding and summarization workflows
* Full-stack coordination (Next.js + FastAPI)
* REST API design and validation
* Interactive data visualization
* Containerized development practices
* Quantization and efficient data processing

---

## 📊 Dataset Information

This project works with **arXiv computer science papers** processed into vector embeddings.

| Attribute         | Details                                                            |
| ----------------- | ------------------------------------------------------------------ |
| Format            | JSONL                                                              |
| Content           | Title, authors, abstract, categories, publication date, embeddings |
| Domains           | ML, CV, NLP, AI, and related CS fields                             |
| Optimization      | Int8 quantization                                                  |
| Storage Reduction | ~75% with preserved semantic accuracy                              |

---

## 👥 Credits & Attribution

Developed as a **collaborative academic project** and maintained independently for learning and development purposes.
Research papers are sourced from **arXiv.org**, an open-access repository maintained by **Cornell University**.

---

## 🚀 Future Enhancements

| Area               | Planned Improvements                |
| ------------------ | ----------------------------------- |
| Authentication     | User accounts and saved searches    |
| Search & Analytics | Advanced filters and trend analysis |
| Visualization      | Citation network graphs             |
| Collaboration      | Shared research collections         |
| AI Features        | Multi-paper summarization           |
| Performance        | Caching and query optimization      |
| UX                 | Mobile-responsive enhancements      |
| API                | Usage monitoring and throttling     |
| Export             | Summary and citation export tools   |
| Personalization    | Recommendation engine               |

---

## 📄 License

This project is licensed under the **MIT License**.
See the `LICENSE` file for details.

<p align="center">
  <em>Built for researchers, students, and developers interested in AI-powered search and modern web development.</em>
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Status-Active%20Development-success?style=flat-square" />
</p>
