<h1 align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=28&duration=4000&pause=1000&color=6366F1&center=true&vCenter=true&width=600&lines=Hi%2C+I'm+Shubham+Badola+%F0%9F%91%8B;Co-founder+%26+CTO+%40+Wallt;Building+India's+Legacy+Platform" alt="Typing SVG" />
</h1>

<p align="center">
  <a href="https://wallt.in"><img src="https://img.shields.io/badge/🚀_Wallt-Visit_Website-6366F1?style=for-the-badge" /></a>
  <a href="https://www.linkedin.com/in/shubham-badola-07120b119/"><img src="https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <img src="https://komarev.com/ghpvc/?username=shubhambadola&style=for-the-badge&color=6366F1" alt="Profile Views" />
</p>

---

## 🚀 Current Mission: Wallt

**[Wallt](https://wallt.in)** is India's most comprehensive **legacy planning and digital vault platform**.

As Co-founder & CTO, I'm addressing a critical gap in the financial ecosystem: the fragmentation of digital wealth and the complexity of inheritance.

### 🎯 The Problem

- 📱 **Digital Asset Fragmentation** — Assets scattered across 50+ platforms with no unified view
- 🔐 **Inaccessible Credentials** — Families lose access to millions because credentials die with the owner
- ⏰ **Delayed Wealth Transfer** — Inheritance in India is archaic, often taking months of legal battles

### 💡 Our Solution

| Feature | Description |
|---------|-------------|
| **🏦 Digital Vault** | Bank-grade encrypted repository for documents, credentials, and financial assets |
| **🤝 Smart Handover** | A proprietary "dead man's switch" ensuring information reaches nominees *only* when exigency criteria are met |
| **🔒 Zero-Knowledge Security** | Architected with AWS Nitro Enclaves + KMS — even we cannot access user data |
| **👥 Smart Nominees** | Granular access control — designate specific assets to specific people |

---

## 🏗️ Technical Architecture

I architect Wallt as a secure, event-driven platform with **hardware-level encryption isolation**:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                          Wallt Platform                                 │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌───────────┐  │
│   │  Web App     │  │  Mobile App  │  │  Admin CRM   │  │  Website  │  │
│   │  Next.js 13  │  │  Expo / RN   │  │  React+Vite  │  │ Chakra UI │  │
│   └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └─────┬─────┘  │
│          └─────────────────┼─────────────────┘               │         │
│                            ▼                                 │         │
│   ┌──────────────────────────────────────────────────────────┘         │
│   │                                                                    │
│   ▼                         API Layer                                  │
│   ┌────────────────────────────────────────────────────────────────┐   │
│   │               Hapi.js API + JWT Auth + Socket.io               │   │
│   │   ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────────┐ │   │
│   │   │   Auth   │ │  Vault   │ │ Nominees │ │    Payments      │ │   │
│   │   │ Service  │ │ Service  │ │ Service  │ │   (Razorpay)     │ │   │
│   │   └──────────┘ └──────────┘ └──────────┘ └──────────────────┘ │   │
│   └────────────────────────────────────────────────────────────────┘   │
│                            │                                           │
│              ┌─────────────┼──────────────┐                            │
│              ▼             ▼              ▼                             │
│   ┌──────────────┐ ┌────────────┐ ┌────────────┐                      │
│   │    MySQL     │ │   Agenda   │ │  Google    │                      │
│   │  (Sequelize) │ │  (Jobs)    │ │  Pub/Sub   │                      │
│   └──────────────┘ └────────────┘ └────────────┘                      │
│                                                                        │
│   ╔════════════════════════════════════════════════════════════════╗   │
│   ║              🔐 Zero-Knowledge Enclave (Go)                    ║   │
│   ║                                                                ║   │
│   ║   AWS Nitro Enclaves  ←→  KMS Attestation  ←→  TimeLock       ║   │
│   ║   Encrypted key recovery that even Wallt cannot access         ║   │
│   ╚════════════════════════════════════════════════════════════════╝   │
│                                                                        │
│   ┌────────────────────────────────────────────────────────────────┐   │
│   │                  AWS Cloud Infrastructure                      │   │
│   │      ECS • S3 • CloudFront • Route53 • SES • Nitro Enclaves   │   │
│   └────────────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## 🤖 KIRA — AI Developer Agent

I built **KIRA** (Kode Intelligence & Review Agent), an autonomous AI developer that handles tickets end-to-end:

```
   Jira Ticket Assigned to KIRA
            │
            ▼
   ┌─────────────────┐     ┌──────────────────────────┐
   │  Clarity Check  │────▶│  Semantic Codebase Search │
   │  (Claude AI)    │     │  Qdrant + Ollama Embeds   │
   └────────┬────────┘     └──────────────────────────┘
            │
     confidence ≥ 60?
      ╱          ╲
    YES           NO → Post questions to Jira, pause
     │
     ▼
   ┌─────────────────┐
   │  Code Generation │─── Patch Mode (93% fewer tokens)
   │  (Claude Sonnet) │─── AST-aware file selection
   └────────┬────────┘    Learned patterns from past PRs
            │
            ▼
   ┌─────────────────┐
   │   Verification   │─── Auto-fixes flagged issues
   │   Pass           │─── Re-generates if needed
   └────────┬────────┘
            │
            ▼
   Branch → Commit → PR → Reviewer assigned
            │
            ▼
   CodeRabbit reviews → KIRA auto-fixes → Merge-ready
```

**Key engineering decisions:**
- **SQLite crash recovery** — checkpoints at every stage, resumes from where it left off
- **Patch-mode output** — surgical hunks instead of full files, reducing output tokens by 93%
- **AST-aware code chunking** — Babel parser extracts function/class/route-level chunks for semantic search
- **Semantic reranking** — Claude reranks vector search results for precision file selection

---

## 🧠 Engineering Leadership Philosophy

- **Product-Centric Architecture** — Every line of code should solve a user problem or unlock a business opportunity
- **Scalability with Simplicity** — Complexity is the enemy of execution. Systems should be robust enough to scale but simple enough to maintain
- **Data-Driven Decisions** — From infrastructure capacity to feature prioritisation, metrics and observability guide strategy
- **Empowering Teams** — Cultures of ownership where engineers understand the "why" behind the "what"

---

## 👨‍💻 Professional Experience

### 🎯 Current Role

<table>
<tr>
<td width="100"><img src="https://img.shields.io/badge/2024-Present-6366F1?style=flat-square" /></td>
<td>
<strong>Co-founder & CTO @ <a href="https://wallt.in">Wallt</a></strong><br/>
Building India's most comprehensive legacy planning and digital vault platform from the ground up.
</td>
</tr>
</table>

### 🚀 Career Journey

<details>
<summary><strong>🏗️ Head of Engineering (Contractual) — Connextra.io, Delhi</strong> <em>(Jan 2025 - Jun 2025)</em></summary>
<br/>

- **Strategic Leadership**: Architected a scalable SaaS platform delivering end-to-end workflow automation
- **Integration Mastery**: Led integration of **40+ third-party services** as configurable triggers
- **Cloud Architecture**: Microservices on **GCP (Cloud Run, Cloud Tasks, Pub/Sub)** with high availability
- **AI Implementation**: Custom AI models to auto-generate workflow automations from user prompts

</details>

<details>
<summary><strong>👔 Engineering Manager — Zen Admin, Singapore</strong> <em>(Sep 2022 - Dec 2024)</em></summary>
<br/>

- **Product Development**: Built two enterprise products from scratch: B2B eCommerce procurement platform + HR management system
- **AI & Innovation**: Built a conversational chatbot using **Amazon Bedrock** that configured procurement ecosystems via natural language
- **Infrastructure Migration**: Migrated core infra from Singapore to EU (EC2, RDS, S3, MongoDB) with encryption and compliance controls
- **Impact**: HRIS module boosted HR efficiency by **65%** through automated notifications and custom configurations

</details>

<details>
<summary><strong>🎖️ Tech Lead — Stack, Bangalore</strong> <em>(Oct 2020 - Sep 2022)</em></summary>
<br/>

- **Scale**: Led 10-member team developing a system processing **50,000+ requests per second**
- **Architecture**: Designed backends using Node.js, Go, Kafka, and Redis with advanced DB techniques (partitioning, function-based indexes)
- **Enterprise Readiness**: Delivered platforms enabling corporate cloud migrations with security analysis and performance tuning

</details>

<details>
<summary><strong>💼 Software Engineer — BYJU'S (via Wyzebulb acquisition)</strong> <em>(Oct 2019 - Oct 2020)</em></summary>
<br/>

- Redesigned BYJU's monolithic architecture into a scalable **microservices system**
- Implemented **event-driven architecture** using the choreography saga pattern
- Dockerized and deployed on **AWS ECS** for scalable orchestration

</details>

<details>
<summary><strong>🔧 Software Engineer — Wyzebulb, Bangalore</strong> <em>(Nov 2018 - Oct 2019)</em></summary>
<br/>

- Architected the flagship automation service connecting data across thousands of third-party apps
- Built comprehensive error monitoring, alerting systems, and real-time internal dashboards

</details>

<details>
<summary><strong>🏥 Software Engineer — Medibox, Bangalore</strong> <em>(Jan 2016 - Oct 2018)</em></summary>
<br/>

- Developed a unified notification system impacting **55,000+ customers**
- Built order management system for real-time inventory updates

</details>

---

## 🛠️ Technical Arsenal

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=go,python,js,ts,nodejs,express,react,nextjs&perline=8" />
  </a>
</p>

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=aws,gcp,docker,kubernetes,kafka,elasticsearch,mongodb,mysql&perline=8" />
  </a>
</p>

<p align="center">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev/icons?i=postgres,redis,linux,git,nginx,jenkins,github,vscode&perline=8" />
  </a>
</p>

| Domain | Technologies |
|--------|--------------|
| **Leadership** | Team Building, Agile/Scrum, System Design, Mentorship |
| **Languages** | Go, JavaScript, TypeScript, Python |
| **Backend** | Hapi.js, Express.js, Node.js, Microservices |
| **Frontend** | React, Next.js, React Native (Expo), Chakra UI |
| **AI/ML** | Claude AI (Anthropic), Ollama, Qdrant Vector DB, Amazon Bedrock |
| **Databases** | MySQL, PostgreSQL, Redis, MongoDB, SQLite |
| **Infrastructure** | AWS (ECS, S3, Nitro Enclaves, KMS), GCP, Docker, Kubernetes |
| **Events & Jobs** | Google Pub/Sub, Kafka, Agenda, Socket.io |
| **Payments & Comms** | Razorpay, SendGrid, Twilio, FCM |

---

## 🎓 Education

**Bachelor of Engineering**  
Andhra University • *2011 - 2015*

---

## 📊 GitHub Stats

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=shubhambadola&theme=tokyonight&hide_border=true" alt="GitHub Streak" />
</p>

---

## 🌐 Connect With Me

<p align="center">
  <a href="mailto:shubhambadola87@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" />
  </a>
  <a href="https://www.linkedin.com/in/shubham-badola-07120b119/">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  <a href="https://twitter.com/">
    <img src="https://img.shields.io/badge/Twitter-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white" />
  </a>
  <a href="https://wallt.in">
    <img src="https://img.shields.io/badge/Wallt-6366F1?style=for-the-badge&logo=safari&logoColor=white" />
  </a>
</p>

---

<p align="center">
  <em>"Legacy is not what you leave for people. It's what you leave in people."</em>
</p>
