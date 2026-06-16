# A multi agent system for Pediatric Oncology Patient Care

> A multi-agent AI platform designed to assist caregivers and children navigating pediatric cancer — through intelligent data extraction, risk prediction, symptom guidance, and empathetic conversational support.


## 📌 Overview
 
A final-year undergraduate project built to address a critical gap in pediatric oncology care: **the lack of AI-powered, child and caregiver-friendly support tools**. The platform combines a fine-tuned Large Language Model, a Machine Learning risk stratification model, and a multi-agent Swarm architecture to deliver end-to-end support — from reading a patient report to answering sensitive medical questions in a safe, empathetic way.
 
---

## 🧠 Proposed Methodology
 
The system is fundamentally built on the **OpenAI Swarm framework**, where multiple specialized agents collaborate to handle distinct tasks:
 
```
Patient Report
     │
     ▼
┌─────────────────────┐
│  Data Collection    │  ← Extracts & preprocesses patient data from reports
│      Agent          │
└────────┬────────────┘
         │
   ┌─────┴──────┐──────────────────────┐
   ▼            ▼                      ▼
┌──────────┐ ┌───────────────┐  ┌─────────────────┐
│   Risk   │ │  Symptoms &   │  │  Conversational  │
│Stratifi- │ │  Side-Effects │  │     Agent        │
│cation    │ │  Agent        │  │  (OpenAI API)    │
│  Agent   │ │ (CancerLLM)   │  └─────────────────┘
└──────────┘ └───────────────┘
     │               │
     ▼               ▼
RandomForest   Mistral-7B (Fine-tuned)
  Regressor     via HuggingFace
```

### Agent Breakdown
 
#### 1. 📋 Data Collection Agent
- Parses and preprocesses patient medical reports
- Extracts key clinical details (demographics, diagnosis, treatment history)
- Stores structured data as text for downstream agents to consume
#### 2. 📊 Risk Stratification Agent
- Uses a **RandomForestRegressor** model trained on synthetic pediatric cancer data
- Predicts treatment success probability considering:
  - Demographics
  - Subsequent malignancies & recurrences
  - Cardiac and pulmonary causes
- Synthetic training data sourced from pediatric oncology journals and research papers
- Model serialized with **Pickle** for efficient inference
- Output is presented in a child/caregiver-friendly, non-technical format

#### 3. 💊 Symptoms & Side-Effects Agent (CancerLLM)
- Powered by **Mistral-7B fine-tuned** on a custom pediatric oncology dataset
- Training data combines: case studies, caregiver reports, symptom logs, publicly available medical literature
- Model loaded from **HuggingFace** in a quantised, memory-efficient format
- Evaluation metrics: **ROUGE** and **BLEU**
- Provides clear explanations of cancer symptoms, drug effects, and treatment side-effects

#### 4. 💬 Conversational Agent
- Shares patient context with the chatbot as a functional parameter (via OpenAI Swarm tools)
- Governed by a system prompt enforcing:
  - Always-positive, practical responses
  - Safe deflection of sensitive end-of-life questions (e.g. *"Will I die?"*)
- Supports both children and caregivers through the treatment journey
---

## 🛠️ Tech Stack
 
### Hardware & Software Requirements
 
| Category | Tools / Platforms |
|---|---|
| **LLM Serving** | GPT 4.o, Ollama, HuggingFace |
| **Compute** | GPU (for fine-tuning & inference) |
| **Development** | Visual Studio Code, Google Colab |
| **AI Frameworks** | OpenAI Swarm, HuggingFace Transformers |
| **Backend / ML** | Python, scikit-learn (RandomForest), Pickle |
| **Frontend** | Streamlit |
| **APIs** | OpenAI API |
 
---

## 🔒 Safety & Ethics
 
- The conversational agent is explicitly restricted from providing responses to questions about mortality (e.g. *"Will I die?"*, *"When will I die?"*) — these are deflected with empathetic, positive guidance.
- All synthetic training data was prepared from published pediatric oncology literature and does not include real patient records.
- The system is designed as a **support tool**, not a diagnostic or clinical decision-making system. Always consult a qualified medical professional.
---
