# Sentiment Command Center

A **real-time AI-powered sentiment monitoring platform** that ingests live social media–style data, analyzes sentiment and emotions, triggers alerts, and visualizes insights on an interactive dashboard.

Built using **FastAPI, Redis, PostgreSQL, Hugging Face NLP models, React, and Docker**, this project demonstrates an end-to-end **real-time data + AI system**.

---

## What Problem Does This Solve?

Brands need to understand **public sentiment in real time** to:
- Detect negative trends early
- Monitor customer feedback
- Track product perception

This system continuously processes incoming posts, analyzes sentiment instantly, and displays live insights—just like a real production monitoring platform.

---

## How the System Works (Flow)

Ingest fake social media posts

Stream data through Redis

Analyze sentiment using AI models

Store results in PostgreSQL

Push live updates via WebSockets

Visualize data on a dashboard

Trigger alerts on negative spikes

---

## Architecture Overview

```

┌────────────┐
│ Ingestor │ → Generates posts
└─────┬──────┘
│ Redis Stream
┌─────▼──────┐
│ Worker │ → AI Sentiment & Emotion Analysis
└─────┬──────┘
│ PostgreSQL
┌─────▼──────┐
│ Backend │ → APIs, WebSockets, Alerts
└─────┬──────┘
│
┌─────▼──────┐
│ Frontend │ → Live Dashboard
└────────────┘

```


---

## Core Capabilities

- Real-time data ingestion (Redis Streams)
- AI-based sentiment & emotion detection
- Async worker processing with batching
- WebSocket live updates
- Interactive React dashboard
- Automated alerting engine
- Fully Dockerized microservices
- Unit & integration testing

---

## Dashboard Highlights

- Total posts processed
- Positive / Negative / Neutral counters
- Live sentiment trend graph
- Sentiment distribution chart
- Real-time post feed with sentiment labels
- Connection health indicator

---

## Repository Structure

```
sentiment-platform/
│
├── backend/ # FastAPI backend (APIs, alerts, WebSockets)
├── worker/ # AI sentiment analysis worker
├── ingester/ # Fake social media data generator
├── frontend/ # React + Vite dashboard
├── docker-compose.yml
├── .env
├── .env.example
├── ARCHITECTURE.md
└── README.md
```


---

## AI & NLP Details

- **Sentiment Model**: DistilBERT (positive / negative)
- **Emotion Model**: DistilRoBERTa (joy, anger, etc.)
- **External LLM Support** (optional): Groq / OpenAI-compatible
- Fallback to local models if external API is unavailable

---

## Alerting Logic

Alerts are triggered when:
- A minimum number of posts are processed
- The **negative-to-positive sentiment ratio** exceeds a threshold
- Evaluated over a rolling time window

Alerts are stored in the database for audit and monitoring.

---

## Environment Setup

Create environment file:

```bash
cp .env.example .env
```

---

## Key variables:

DATABASE_URL=postgresql+asyncpg://user:password@postgres:5432/sentiment_db
REDIS_HOST=redis
REDIS_PORT=6379
API_PORT=8000
FRONTEND_PORT=3000
ALERT_NEGATIVE_RATIO_THRESHOLD=0.5

---

## How to Run the Project
Prerequisites

Docker

Docker Compose

Start Everything

```bash
docker-compose up --build
```

## Access Services

Frontend Dashboard: http://localhost:3000

Backend API: http://localhost:8000

Swagger Docs: http://localhost:8000/docs

Health Check: http://localhost:8000/api/health

---

## Key API Endpoints
GET /api/health
GET /api/posts
GET /api/sentiment/distribution
GET /api/sentiment/aggregate

---

## WebSocket:

ws://localhost:8000/ws/sentiment

---
## Testing

Run backend tests:

cd backend

```bash
pytest --cov
```

---

## Ideal Use Cases

Brand sentiment monitoring

Social media analytics

Real-time NLP pipelines

Data & AI engineering portfolio project
