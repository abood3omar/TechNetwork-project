<div align="center">

# 🌐 [**LIVE WEBSITE — technetworkfront.laravel.cloud**](https://technetworkfront.laravel.cloud/)

# 🚀 TechNetwork | Next-Gen AI Recruitment Ecosystem

![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![n8n](https://img.shields.io/badge/n8n-Workflow_Automation-EA4B71?style=for-the-badge&logo=n8n&logoColor=white)
![Pinecone](https://img.shields.io/badge/Pinecone-Vector_DB-000000?style=for-the-badge&logo=pinecone&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-Agent-412991?style=for-the-badge&logo=openai&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)

> **Where Top Tech Talent Meets Opportunity.** <br>
> *Note: The core source code is maintained in private repositories. This repository serves as a technical showcase and architectural overview of the backend engineering and AI integration.*

</div>

---

## 📌 Executive Summary
**TechNetwork** is an intelligent, evidence-based recruitment platform built exclusively for the tech industry[cite: 1]. It solves the critical issues of fragmented developer data and outdated keyword-based hiring by leveraging **Semantic Search**, **Vector Embeddings**, and **Automated AI Workflows**[cite: 1]. 

The platform allows developers to build verifiable portfolios (linking GitHub, projects, and skills) while providing companies with a smart AI Recruitment Assistant capable of understanding context, calculating ATS scores, and finding the perfect candidate match[cite: 1].

---

## ⚙️ Core Backend Architecture & System Engineering

As the primary Backend Engineer, my objective was to move beyond traditional CRUD applications and architect a highly scalable, decoupled ecosystem capable of handling heavy AI processing asynchronously.

### 1. Decoupled AI Orchestration (n8n Middleware)
To prevent the Laravel monolithic server from blocking during intensive AI tasks (like PDF parsing and LLM API calls), the AI pipelines were completely decoupled using **n8n** as an orchestration engine[cite: 1].

#### 🧠 Pipeline A: Smart CV Analysis Agent
* **Trigger:** Developer uploads a CV (PDF)[cite: 1].
* **Flow:** Validate PDF ➔ Extract & Clean Text ➔ Generate `cv_hash` ➔ Prepare Payload ➔ OpenAI Chat Model ➔ Format JSON Response[cite: 1].
* **Output:** Instantly returns a structured JSON containing an ATS Score, strengths, weaknesses, and actionable improvement suggestions, saved to the `cv_analyses` table[cite: 1].

#### 🧠 Pipeline B: Candidate Vector Indexing
* **Trigger:** Profile updates or new developer registrations[cite: 1].
* **Flow:** Fetch `candidate_profiles` ➔ Normalize Text ➔ Recursive Character Text Splitter ➔ OpenAI Embeddings[cite: 1].
* **Output:** Converts unstructured developer experiences, skills, and projects into high-dimensional vectors stored securely in **Pinecone Vector Database**[cite: 1].

#### 🧠 Pipeline C: Intelligent Recruitment Assistant
* **Trigger:** Company submits a natural language search query (e.g., *"Need a scalable backend dev experienced with Laravel and DDD"*)[cite: 1].
* **Flow:** Normalize Webhook Request ➔ Generate Query Embeddings ➔ Search `Candidate Vector Knowledge Base` (Pinecone) ➔ AI Reranker ➔ Return Ranked Matches[cite: 1].
* **Output:** Context-aware candidate recommendations that match semantic meaning, not just exact keywords[cite: 1].

### 2. Advanced Dynamic RBAC (Role-Based Access Control)
Instead of relying on hardcoded permissions or basic middleware, I engineered a highly dynamic, database-driven authorization engine to manage the 4 user scopes (Admin, Company, Developer, Guest)[cite: 1].
* **Modular Segregation:** The system isolates permissions down to the `Modules`, `Entities`, and `Actions` level[cite: 1].
* **Role Rights Engine:** Permissions are dynamically mapped via the `role_rights` and `entity_actions` tables[cite: 1]. This allows platform administrators to assign granular privileges (e.g., `create`, `edit`, `viewAny`, `ChangePassword`) dynamically from the Admin Dashboard[cite: 1].

### 3. Database Integrity & Domain Isolation
The MySQL database is strictly normalized (3NF) to guarantee Data Integrity, utilizing robust constraints and relationships across distinct logical domains[cite: 1]:
* **User & Security Domain:** Manages sessions, authentication, and the RBAC engine (`users`, `roles`, `role_rights`, `modules`, `actions`)[cite: 1].
* **Developer Domain:** Manages comprehensive portfolios (`developers`, `developer_experiences`, `developer_projects`, `developer_skills`, `developer_certificates`)[cite: 1].
* **Company & Job Board Domain:** Manages the recruitment lifecycle and company data (`companies`, `jobs`, `job_postings`, `job_applications`)[cite: 1].
* **AI & Analytics Domain:** Handles the state of asynchronous AI tasks (`cvs`, `cv_analyses`, `candidate_profiles`, `chat_messages`)[cite: 1].

---

## 🛠️ Technology Stack

### Backend & Architecture
* **Framework:** Laravel (PHP)[cite: 1]
* **Architecture Pattern:** Decoupled Services, Modular RBAC, RESTful APIs
* **Database:** MySQL (Managed via TablePlus & phpMyAdmin)[cite: 1]
* **Authentication:** Token-based Auth / Session Management
* **API Testing:** Postman[cite: 1]

### AI & Data Processing
* **Orchestration Engine:** n8n (Webhooks, Data Parsing, API routing)[cite: 1]
* **Large Language Models (LLM):** OpenAI (Chat Models, Embeddings, AI Agents)[cite: 1]
* **Vector Database:** Pinecone (Semantic Search & Reranking)[cite: 1]

### Frontend Client
* **Framework:** React.js (Single Page Application)[cite: 1]
* **Styling:** Tailwind CSS & Custom CSS[cite: 1]
* **HTTP Client:** Axios[cite: 1]

----

## 👨‍💻 Development Team

TechNetwork was developed as a comprehensive Graduation Project at **Al al-Bayt University**, Faculty of Information Technology (Computer Science Department), under the supervision of **Dr. Suhair Bani Ata**[cite: 1].

* **Backend, System Architecture , FrontEnd :**  
  **Abdalrhman Hamed** | [LinkedIn](https://www.linkedin.com/in/abdalrhman-hamed) | [GitHub](https://github.com/abood3omar)[cite: 1]

* **Frontend & AI Pipelines:**  
  **Mohammad Al Bzoor** | [LinkedIn](https://www.linkedin.com/in/MOHAMMAD-LINKEDIN-URL-HERE) | [GitHub](https://github.com/MOHAMMAD-GITHUB-USERNAME)[cite: 1]

---
*If you are a technical recruiter or engineering manager, I would be happy to walk you through the codebase, the AI pipelines, and the system design decisions over a call.*
