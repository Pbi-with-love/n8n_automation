# Automated AI Video Creation & TikTok Publishing Pipeline

## 📌 Overview
This project is an **end-to-end AI automation pipeline built with n8n** that:

- Detects trending TikTok content using real-time data
- Analyzes viral videos using AI vision models
- Generates new AI videos using Google Veo 3.1
- Prepares content for automated publishing

The system combines **LLMs + RAG + video generation models** to create a fully automated, trend-driven content production pipeline, reducing manual content ideation and ensuring outputs are grounded in real-world viral patterns.

---

## ⚙️ System Architecture

The pipeline is split into **two independent n8n workflows**:

---

## 🔁 Flow 1: TikTok Trend Discovery & Data Pipeline

### 🎯 Objective
Identify trending AI-related TikTok content and build a structured dataset for downstream AI generation.

### 🧠 Steps

#### 1. Trend Discovery (RAG + Gemini)
- Google Gemini AI agent queries trending TikTok topics
- Focus:
  - AI storytelling
  - AI animal videos
  - Viral content (>100k views / 24h)
- Output:
  - Top 3 hashtags (strict JSON format)

#### 2. Data Scraping (Apify)
- Hashtags passed to **Apify TikTok Scraper**
- Extracts trending videos under each hashtag

#### 3. Data Processing & Storage
- Filters raw data into structured format:
  - `video_id`
  - `caption`
  - `video_url`
  - `language`
  - `created_at`
- Upserts into **PostgreSQL**

---

## 🎬 Flow 2: AI Video Generation & Publishing Pipeline

### 🎯 Objective
Generate new AI videos based on viral patterns and prepare them for publishing.

---

### 🧠 Steps

#### 1. Video Retrieval & Vision Analysis
- Fetch latest videos from PostgreSQL
- Gemini Vision analyzes:
  - environment
  - characters
  - actions
- Ignores watermarks

---

#### 2. Prompt Engineering (AI Agent)
- AI agent converts analysis into:
  - `veo3_prompt`
  - `caption`
  - `hashtags`

---

#### 3. Video Generation (Google Veo 3.1)
- Sends prompt to **Veo 3.1 Fast Generate API**
- Uses `predictLongRunning` for async generation
- Handles:
  - Operation polling
  - Multi-step generation loop (due to ~8s limit per request)

---

#### 4. Storage & Archiving
- Stores generated videos in **Google Cloud Storage (GCS)**
- Logs metadata into **Google Sheets**

---

#### 5. TikTok Publishing (Integration Layer)
- Final output prepared for TikTok Graph API
- Uses:
  - GCS video URL
  - Generated captions & hashtags

---

## 🛠️ Tech Stack

- **Workflow Orchestration:** n8n  
- **AI Models:**
  - Google Gemini (Chat + Vision)
  - Google Veo 3.1 (Video Generation)
- **Data Scraping:** Apify TikTok Scraper  
- **Database:** PostgreSQL (Supabase)
- **Storage:** Google Cloud Storage (GCS)  
- **Tracking:** Google Sheets API  

---

## 🚀 Reliability & Engineering Considerations

### 🔒 Rate Limit Handling
- Built-in throttling for:
  - Apify API
  - LLM API calls

### 📦 Data Validation
- Structured Output Parser enforces strict JSON schema
- Prevents invalid data propagation to:
  - Database layer
  - Veo generation API

---

## 💡 Key Design Principles

- **Trend-driven generation** (not random AI output)
- **Decoupled workflows** (scraper ≠ generator)
- **Event-driven pipeline design**
- **Scalable AI orchestration via n8n**

---