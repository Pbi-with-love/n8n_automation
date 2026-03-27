# n8n Automation Projects

## 📌 Overview
This repository contains two **n8n-based automation projects** that combine workflow orchestration, AI models, databases, and external integrations to solve practical business and content problems. The project focuses on system architecture design and workflow automation using n8n, integrating third-party APIs, databases, and cloud services. It also demonstrates foundational knowledge of RAG, vector databases.

The projects currently included are:

- **TikTok Automation**: an AI-powered workflow for trend discovery, video analysis, and automated content generation preparation.
- **JarWise**: a finance chatbot workflow for Facebook Messenger with knowledge retrieval and invoice processing support.

---

## 🚀 Project 1: TikTok Automation

### 🎯 Objective
Build a trend-driven AI content pipeline that helps identify viral TikTok patterns, analyze high-performing videos, and prepare new AI-generated videos for publishing.

### 💡 Main Benefit
- Reduces manual work in trend research and content ideation
- Connects discovery, analysis, generation, and publishing preparation in one workflow
- Keeps AI outputs aligned with real-world viral signals instead of random prompt experimentation

### 🛠️ Tech Stack
- **Workflow Orchestration:** n8n
- **AI Models:** Google Gemini, Google Veo 3.1
- **Data Scraping:** Apify TikTok Scraper
- **Database:** PostgreSQL (Supabase)
- **Storage & Tracking:** Google Cloud Storage, Google Sheets

### ⭐ Strengths
- **Trend-driven content generation** based on recent TikTok activity
- **Modular workflow design** across discovery, analysis, and generation stages
- **Good scalability for experimentation** in AI video automation use cases

---

## 🚀 Project 2: JarWise

### 🎯 Objective
Build a finance-focused chatbot that can respond using knowledge-base documents, support invoice submission flows, and provide more structured financial guidance through chat.

### 💡 Main Benefit
- Delivers more reliable chatbot responses by grounding answers in internal documents
- Supports invoice intake and structured extraction for downstream financial analysis
- Integrates directly with Facebook Messenger for a practical user-facing experience

### 🛠️ Tech Stack
- **Workflow Orchestration:** n8n
- **Conversational AI:** Google Gemini
- **Knowledge Retrieval:** Supabase Vector Store, Gemini Embeddings
- **Database & Memory:** PostgreSQL
- **Channel Integration:** Facebook Messenger Webhook, Graph API
- **Document Source:** Google Docs
- **Invoice Processing:** OCR and AI-based structuring

### ⭐ Strengths
- **RAG-first design** to keep responses aligned with documented knowledge
- **Conversation memory support** for better multi-turn interactions
- **Combined chatbot and invoice workflow** for stronger operational value

---

## 🌐 Repository Value

This repository shows how **n8n can act as the orchestration layer** for modern AI workflows. It demonstrates how LLMs, vector search, OCR, databases, webhooks, and third-party APIs can be combined into automation systems that are practical, extensible, and product-oriented.
