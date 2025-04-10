# 💸 Loan Origination System (LOS)

A scalable and modular platform designed to handle end-to-end digital loan journeys — from lead intake and KYC to eligibility checks, underwriting, and disbursal. Built for high flexibility across NBFC partners and data sources.

---

## 📌 Problem Statement

Lending workflows are complex and vary by lender. Manual processes, rigid logic, and inconsistent integrations lead to delays and data errors.

We needed to build:
- A fully API-driven loan journey
- Real-time integrations with NBFCs
- EMI previews with eligibility mapping
- Fast-track KYC + disbursal updates

---

## ⚙️ Tech Stack

- **Backend:** Django, Django REST Framework  
- **Databases:** MongoDB (for dynamic application schema), MySQL (for relational workflows)  
- **Queue & Async:** Celery, Redis  
- **Authentication:** JWT-based Role Access (RBAC)  
- **Infra:** Docker, Nginx  
- **Storage & Security:** AWS S3 for document storage, IAM for credential-based config  

---

## 🚀 Key Features

### 🔐 Smart KYC & CKYC Flow
- Capture Aadhaar, PAN, CKYC number
- Smart matching logic with retry mechanism
- Match scoring and fuzzy matching (Mongo-powered flexibility)

### 🏦 Dynamic NBFC Integration Layer
- Connected to **4 NBFC APIs** (live)
- Mapped partner-specific payloads via pluggable serializers
- Handles success/failure fallbacks and SLA tracking

### 💳 EMI Calculator & Offer Engine
- Configurable logic for interest rate, tenure, partner rules
- EMI preview and offer breakdown per NBFC
- Rule engine backed by MySQL for auditability

### ✅ Underwriting Flow
- Credit score-based approval logic
- Rule-based evaluation mapped via Mongo-based decision tables
- Trigger-based updates via Celery jobs

### 💸 Disbursal Lifecycle Tracker
- NBFC webhook listeners and response parsing
- Disbursal status updates pushed via Celery
- Failure reconciler and retry manager

---

## 📈 Impact & Performance

| Metric | Result |
|--------|--------|
| 🔁 Applications Handled | 2K+ per month |
| 🏦 NBFCs Integrated | 4 |
| 🧠 KYC Match Accuracy | ↑ 25% |
| ⏱️ Avg. Time-to-Approval | <2 Hours |
| 🔐 Document Security | IAM + Pre-signed S3 URLs |

---

## 🗂️ Why Mongo + MySQL?

- MongoDB was used to handle **dynamic application schemas** — every NBFC had slightly different lead formats and data points  
- MySQL powered the **relational flows** — approvals, status logs, partner configs, and audit events  
- The combo allowed fast prototyping and structured reporting

---

## 📂 Architecture Flow
User / Partner Portal
↓
Loan Application API (Django DRF)
↓
KYC Engine → Mongo (store raw data + match score)
↓
Eligibility Evaluator → NBFC Partner Mapper (MySQL Rules)
↓
Underwriting Engine (Score-based logic)
↓
Disbursal Manager ← NBFC Webhooks + Async Tasks (Celery)
↓
Status Update API + Notification Trigger


---

## 🧠 Takeaways

- Mongo + MySQL hybrid design improved dev speed + reporting clarity  
- Designing async workflows (Celery) was key for real-time feedback + retries  
- Mapping NBFC variations with pluggable components = easy partner expansion  
- Learned how to track and enforce SLA timelines in real projects  
- Improved user transparency via webhook-based disbursal updates

---

## 📌 Note

This case study is based on a real production system. Codebase is confidential, but logic, structure, and scale reflect actual implementation experience.
