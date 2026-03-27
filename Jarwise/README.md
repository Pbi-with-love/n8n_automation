# JarWise – Financial Chatbot (Demo Template)

## 📌 Overview
JarWise is a **financial assistant chatbot** built to demonstrate how AI, automation workflows, and open data can be integrated to support **personal finance management**. 

## 🚀 Key Features

- 🤖 AI-powered chatbot (Facebook Messenger style)
- 🧠 Retrieval-Augmented Generation (RAG) using Vector Database
- 📊 Financial guidance based on the **Six Jars Method**
- 🧾 Invoice processing via image OCR
- 🔄 Automated workflow orchestration with n8n
- 💬 Chat history tracking with PostgreSQL
- ⚡ Redis-style caching concept (extendable)

---

## 🏗️ System Architecture

### Core Components

- **n8n Workflow Engine**
  - Handles chatbot logic, routing, and automation
- **AI Agent (Gemini / LLM)**
  - Processes user input
  - Retrieves knowledge from vector database
- **Vector Database (Supabase)**
  - Stores:
    - Jarwise_Knowledge
    - Jarwise_Interaction_Flow
- **PostgreSQL**
  - Stores:
    - User data
    - Chat history
    - OCR results
- **OCR Service (Mistral AI)**
  - Extracts text from invoice images
- **Facebook Messenger API**
  - Interface between user and chatbot

---

## 🔄 Main Workflow

### 1. User Interaction
- User sends message via Messenger
- Webhook receives event
- Message is stored in PostgreSQL

### 2. AI Processing
- AI Agent retrieves:
  - Interaction flow rules
  - Financial knowledge
- Generates response based on RAG

### 3. Invoice Flow

#### Step 1: Permission Check
- System checks chat history:
  - `"I want to send invoice"` → PERMIT
  - Otherwise → DENY

#### Step 2: OCR Processing
- Image → OCR → Structured JSON
- Extract:
  - item_name
  - amount
  - jar_type
  - date

#### Step 3: Financial Analysis
- Calculate:
  - Total spending per jar
  - Percentage distribution
  - Compare with ideal ratios

---

## 🧠 Six Jars Method (Concept)

JarWise is based on the **Six Jars Method**:

| Jar Type              | Purpose                          |
|----------------------|----------------------------------|
| Necessities          | Living expenses                  |
| Financial Freedom    | Investments                      |
| Education            | Learning & self-development      |
| Play                 | Entertainment                   |
| Long-term Savings    | Big future goals                |
| Giving               | Charity & contribution          |

---

## 🛠️ Technologies Used
- **Backend Workflow**: n8n
- **AI Models**: Google Gemini, Mistral OCR
- **Database**: PostgreSQL
- **Vector DB**: Supabase
- **Authentication**: (Extendable - JWT)
- **API Integration**: Facebook Graph API

---

## ⚙️ Setup (For Demo Only)
> This project is not intended to run fully without proper credentials.

### Requirements:
- n8n installed
- PostgreSQL database
- Supabase project
- Facebook Developer App
- API keys:
  - Gemini
  - Mistral OCR

### Steps:
1. Import the workflow JSON into n8n
2. Configure credentials:
   - PostgreSQL
   - Supabase
   - Facebook API (Meta developer)
   - Mistral OCR
   - Google API
3. Deploy webhook endpoint
4. Connect to Messenger webhook

---

## 📂 Project Purpose

This project is designed to demonstrate:

- AI Agent architecture (RAG-based chatbot)
- Workflow automation using n8n
- Real-world system design thinking
- Integration of multiple services (OCR, DB, APIs)

---