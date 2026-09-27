# AI / LLM QA Evaluation Portfolio

A personal QA portfolio project demonstrating practical testing of an AI-powered Knowledge Assistant using structured QA methodologies.

> **Project Type:** Personal QA Portfolio Project  
> **Application:** Fictional AI Knowledge Assistant  
> **Company:** NovaTech Solutions (Fictional)  
> **Testing Focus:** AI/LLM, RAG, Prompt Testing, Hallucination, Groundedness, Security & Regression

---

## 📌 Project Overview

This project demonstrates how traditional QA practices can be applied to AI-powered applications.

The fictional application is an **AI Knowledge Assistant** designed to answer employee questions using a predefined company knowledge base.

The project focuses on validating whether the AI:

- Provides accurate answers
- Uses only available knowledge
- Avoids hallucinations
- Remains grounded in source documents
- Handles missing information correctly
- Preserves eligibility conditions
- Handles ambiguous questions
- Resists basic prompt-injection attempts
- Maintains consistency across similar questions
- Handles boundary conditions
- Performs correctly during regression testing

---

## 🏗️ Application Flow

```text
User Prompt
     ↓
AI Application
     ↓
Knowledge Retrieval
     ↓
Relevant Context
     ↓
LLM
     ↓
Generated Response
     ↓
QA Evaluation
