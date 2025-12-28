```markdown
# arXade

[![Project Type](https://img.shields.io/badge/Project-Web%20Application-blue.svg)](https://github.com)
[![Tech Stack](https://img.shields.io/badge/Stack-Full%20Stack-green.svg)](https://github.com)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Learning%20Project-success.svg)](https://github.com)

An AI-powered academic paper discovery platform that enables semantic search through arXiv research papers using vector embeddings and intelligent summarization. Designed to help researchers, students, and academics discover relevant papers through concept-based search rather than traditional keyword matching.

---

## 📸 Visual Preview

![Application Screenshot](./screenshots/home.png)
![Search Results](./screenshots/results.png)

> Add screenshots of the search interface, visualization dashboards, and paper details in the `screenshots/` directory to showcase the application.

---

## 🎯 Project Overview

arXade is a full-stack research discovery tool that processes academic papers from arXiv and enables semantic search through vector embeddings. The platform uses Google's Gemini embedding model to convert paper abstracts, titles, and metadata into high-dimensional vectors, allowing users to search by concepts and ideas rather than exact keyword matches.

### System Architecture

The application consists of three main components:

1. **Data Processing Pipeline**: Processes arXiv papers and generates int8-quantized embeddings for efficient storage using the Gemini text-embedding-004 model
2. **Backend API**: FastAPI service with MongoDB Atlas vector search capabilities, providing search and AI summary generation endpoints
3. **Frontend Interface**: Next.js application with interactive visualizations, filtering, and real-time search capabilities

### Key Workflows

- **Search Workflow**: User enters search query → Frontend sends request to backend → Backend generates query embedding → MongoDB performs vector similarity search → Results returned with relevance scores
- **AI Summary Generation**: Search results trigger automatic summary generation using Gemini AI, providing contextual insights
- **Deep Research Analysis**: Users can request comprehensive analysis of multiple papers with mathematical formulations and theoretical frameworks
- **Visual Analytics**: Interactive charts display paper distribution by category, publication timeline, and common research themes

---

## ✨ Key Features

- **Semantic Search Engine**: Vector-based search that understands research concepts and context beyond keyword matching
- **Embedding Generation Pipeline**: Automated system for generating and quantizing embeddings from paper metadata with rate limiting
- **AI-Powered Summaries**: Context-aware paper summaries generated using Google Gemini AI
- **Deep Research Analysis**: Comprehensive mathematical and theoretical analysis of research topics across multiple papers
- **Interactive Visualizations**: 
  - Word clouds from paper abstracts
  - Category distribution pie charts
  - Timeline views showing publication trends
  - Relevance scoring and filtering
- **LaTeX Rendering**: Full support for mathematical notation in papers and summaries
- **Batch Processing**: Efficient rate-limited API calls with int8 quantization for 4x storage optimization
- **Dockerized Architecture**: Complete containerization for seamless local development and deployment

---

## 🛠️ Tech Stack

### Frontend
- **Framework**: Next.js 15.3 with TypeScript
- **Styling**: Tailwind CSS 4.0
- **Charts & Visualization**: Recharts, Visx, Tremor
- **Math Rendering**: KaTeX for LaTeX support
- **State Management**: React 19 Hooks
- **UI Components**: Custom shine cards and animated buttons

### Backend
- **Framework**: FastAPI 0.110.0
- **Server**: Uvicorn with hot reload support
- **Validation**: Pydantic v2.6
- **Production Server**: Gunicorn 21.2.0
- **Logging**: Structured JSON logging for cloud environments

### Database & Search
- **Database**: MongoDB Atlas with Vector Search
- **Driver**: PyMongo 4.6.2
- **Indexing**: Cosine similarity vector search with int8 quantization
- **Storage**: Optimized with int8 embeddings (4x space reduction)

### AI & Machine Learning
- **Embedding Model**: Google Gemini text-embedding-004
- **Text Generation**: Gemini 2.0 Flash for summaries
- **Library**: google-generativeai SDK (v0.8.5+)
- **Computation**: NumPy 1.26.4 for vector operations

### DevOps & Deployment
- **Containerization**: Docker with Docker Compose
- **Version Control**: Git
- **Environment Management**: python-dotenv

---

## 📁 Folder Structure

```
arXade/
├── frontend/                 # Next.js application
│   ├── src/
│   │   ├── app/             # Next.js app router pages
│   │   │   ├── page.tsx     # Landing page
│   │   │   └── results/     # Search results page
│   │   ├── components/      # React components
│   │   │   ├── ui/          # Reusable UI components
│   │   │   ├── GeminiSummary.tsx
│   │   │   ├── PaperCarousel.tsx
│   │   │   ├── PieChart.tsx
│   │   │   ├── LineChart.tsx
│   │   │   ├── WordCloud.tsx
│   │   │   ├── DeepResearchModal.tsx
│   │   │   ├── LatexRenderer.tsx
│   │   │   └── FilterModal.tsx
│   │   ├── lib/             # Utility functions
│   │   │   └── api.ts       # API client
│   │   └── styles/          # Global styles
│   ├── public/              # Static assets
│   ├── Dockerfile           # Production container
│   ├── Dockerfile.dev       # Development container
│   └── package.json         # Dependencies
├── backend/                  # FastAPI server
│   ├── main.py              # API endpoints and logic
│   ├── requirements.txt     # Python dependencies
│   └── Dockerfile           # Backend container
├── data/                    # Data processing scripts
│   └── embed.py             # Embedding generation pipeline
├── docker-compose.yml       # Multi-container orchestration
├── .env.example            # Environment variables template
├── LICENSE                 # MIT License
└── README.md               # Project documentation
```

**Key Components:**
- **frontend/**: Complete Next.js 15 application with TypeScript, custom UI components, and visualization libraries
- **backend/**: FastAPI server with MongoDB integration, vector search, and Gemini AI endpoints
- **data/embed.py**: Standalone Python script for batch processing arXiv papers into vector embeddings
- **docker-compose.yml**: Orchestrates frontend and backend services for local development

---

## ⚙️ Setup & Installation

### Prerequisites

- Docker and Docker Compose installed ([Get Docker](https://docs.docker.com/get-docker/))
- MongoDB Atlas account with Vector Search enabled ([MongoDB Atlas](https://www.mongodb.com/cloud/atlas))
- Google Gemini API key ([Get API Key](https://ai.google.dev/))

### Installation Steps

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd arXade
   ```

2. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Edit `.env` and add your credentials:
   ```env
   # MongoDB Configuration
   MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/database
   MONGODB_DB_NAME=arxiv_db
   MONGODB_COLLECTION=papers
   
   # Google Gemini API
   GEMINI_API_KEY=your_gemini_api_key_here
   
   # API Protection (generate with: openssl rand -base64 32)
   API_KEY=your_secure_api_key
   NEXT_PUBLIC_API_KEY=your_secure_api_key
   ```

3. **Start the application**
   ```bash
   docker-compose up
   ```

4. **Access the application**
   - Frontend: [http://localhost:3000](http://localhost:3000)
   - Backend API: [http://localhost:8000](http://localhost:8000)
   - API Documentation: [http://localhost:8000/docs](http://localhost:8000/docs)

### Data Preparation

To work with arXiv papers, you'll need to prepare your dataset:

1. Obtain arXiv paper data in JSONL format (each line contains a JSON object with paper metadata)

2. Place your file as `input_papers.jsonl` in the `data/` directory

3. Set your Gemini API key:
   ```bash
   export GOOGLE_API_KEY='your_api_key_here'
   ```

4. Run the embedding generation script:
   ```bash
   cd data
   python embed.py
   ```

The script processes papers in batches of 100, respects rate limits (1500 requests/minute), and outputs int8-quantized embeddings. Progress is logged every 100 papers processed.

---

## 💡 Use Cases

### Academic Research
- Discover papers by research concepts rather than exact keywords
- Find related work based on semantic similarity
- Explore research trends through interactive visualizations
- Generate comprehensive analysis of research topics

### Student Projects
- Learn full-stack development with modern frameworks
- Understand vector embeddings and semantic search implementation
- Practice Docker containerization and deployment patterns
- Explore AI integration in production applications

### Learning & Demonstration
- Showcase AI-powered features in portfolio projects
- Demonstrate scalable architecture design
- Practice working with external APIs and vector databases
- Build experience with modern web technologies

---

## 📚 Learning Outcomes

Building and working with this project provides hands-on experience in:

- **Vector Databases**: Understanding embeddings, similarity search algorithms, and MongoDB Atlas vector indexing
- **AI Integration**: Working with Google Gemini API for both embeddings and text generation
- **Full-Stack Development**: Coordinating Next.js frontend, FastAPI backend, and MongoDB database
- **API Design**: RESTful API development with FastAPI, Pydantic validation, and proper error handling
- **Modern Frontend**: Next.js 15 with TypeScript, server components, and client-side interactivity
- **Data Visualization**: Building interactive charts with Recharts, Visx, and custom components
- **Containerization**: Multi-service Docker orchestration and deployment strategies
- **Data Processing**: Batch processing, rate limiting, and quantization techniques
- **Mathematical Rendering**: LaTeX integration and mathematical notation display
- **Cloud Integration**: Working with managed database services and AI APIs

---

## 📊 Dataset Information

This project works with arXiv computer science papers that have been processed with vector embeddings. The embeddings use int8 quantization, which reduces storage requirements by approximately 75% while maintaining search accuracy.

**Data Format**: JSONL files containing paper metadata (title, authors, abstract, categories, publication date) and int8-quantized embedding vectors.

**arXiv Papers**: The arXiv repository provides open access to research papers across various scientific fields. This project focuses on computer science categories including Computer Vision, Machine Learning, Natural Language Processing, and Artificial Intelligence.

---

## 👥 Credits & Attribution

Developed as a collaborative academic project and maintained independently for learning and development purposes. This project demonstrates practical implementation of vector search, AI integration, and modern web development practices.

**Data Source**: Research papers from arXiv.org, an open-access repository maintained by Cornell University.

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🚀 Future Enhancements

- **User Authentication**: Implement user accounts for personalized search history and saved paper collections
- **Advanced Filtering**: Add multi-faceted search with date ranges, citation counts, author filters, and institution tracking
- **Citation Network Analysis**: Build citation network visualization and impact metrics for papers
- **Collaborative Features**: Enable paper collections, annotations, sharing capabilities, and collaborative research groups
- **Enhanced AI Features**: Implement multi-paper summarization, research trend analysis, and automated literature reviews
- **Performance Optimization**: Add caching layers, database query optimization, and lazy loading for faster performance
- **Mobile Application**: Develop responsive mobile views with touch-optimized interfaces
- **API Rate Limiting**: Implement request throttling and usage monitoring for better resource management
- **Export Capabilities**: Add PDF export for summaries and bibliographic data export in various formats
- **Recommendation System**: Build personalized paper recommendation engine based on user interests

---

## 📝 Resume One-Liner

**Developed a full-stack AI-powered academic search platform using vector embeddings (Google Gemini), MongoDB Atlas vector search, and FastAPI, enabling semantic discovery of arXiv research papers with interactive visualizations and AI-generated analysis.**

---

**Built for researchers, students, and developers interested in AI-powered search and modern web development**
```
