# AI Pharma Avatar Assistant

## Overview

AI Pharma Avatar Assistant is a multimodal Generative AI project that combines Retrieval-Augmented Generation (RAG), voice interaction, text-to-speech synthesis, and AI avatar video generation into a single conversational pipeline.

The project was built as an exploration into how modern AI systems can move beyond plain chat interfaces and evolve into interactive digital assistants capable of:

- Understanding pharmaceutical and medication-related questions
- Retrieving contextual knowledge from custom documents
- Generating grounded responses using Large Language Models
- Speaking answers naturally using AI voice synthesis
- Creating talking avatar videos with lip-synced responses
- Supporting voice-based interaction workflows

This project demonstrates how multiple AI layers can be orchestrated together into one end-to-end intelligent system.

---

# Project Motivation

The objective behind this project was to explore the practical integration of multiple GenAI technologies into a single pipeline rather than treating them as isolated concepts.

Instead of building:

- Only a chatbot
- Only a RAG application
- Only a text-to-speech demo
- Only an avatar generator

The idea was to engineer a complete AI interaction flow where:

User Voice/Text → RAG Retrieval → LLM Response → AI Speech → Talking Avatar Video

This project focuses heavily on experimentation, orchestration, and understanding the engineering side of multimodal AI systems.

---

# Core Features

## 1. Pharmaceutical Knowledge Assistant

The assistant is specialized for pharmaceutical and medication-related queries.

The system prompt constrains the assistant to:

- Answer only using retrieved context
- Avoid hallucinations where possible
- Recommend consulting professionals for clinical/patient-specific cases
- Keep responses concise and suitable for voice delivery

The assistant supports:

- Drug interaction queries
- Dosage information
- Medication storage guidance
- Regulatory information
- Contraindications
- Adverse effects

---

## 2. Retrieval-Augmented Generation (RAG)

The project implements a complete RAG pipeline using LangChain + FAISS.

### Supported Knowledge Sources

The system dynamically loads documents from a local knowledge base directory.

Supported file types:

- PDF
- TXT
- DOCX
- DOC
- PPTX
- PPT
- XLSX
- XLS

### RAG Flow

1. Documents are loaded from the `knowledge_docs/` directory
2. Text is chunked using `RecursiveCharacterTextSplitter`
3. Embeddings are generated using OpenAI Embeddings
4. Chunks are stored inside a FAISS vector database
5. User queries are embedded and similarity-searched
6. Relevant context is injected into the LLM prompt
7. Grounded response is generated

### Vector Database

The project uses:

- FAISS for semantic similarity search
- OpenAI embeddings for vector generation
- LangChain retrieval chains for orchestration

---

# Architecture

```text
                        ┌────────────────────┐
                        │  User Voice/Input  │
                        └─────────┬──────────┘
                                  │
                                  ▼
                     ┌────────────────────────┐
                     │ Voice Recording Layer  │
                     └─────────┬──────────────┘
                               │
                               ▼
                     ┌────────────────────────┐
                     │ Speech-to-Text Layer   │
                     └─────────┬──────────────┘
                               │
                               ▼
                     ┌────────────────────────┐
                     │   RAG Retrieval Layer  │
                     └─────────┬──────────────┘
                               │
                               ▼
                     ┌────────────────────────┐
                     │     OpenAI LLM Layer   │
                     └─────────┬──────────────┘
                               │
                               ▼
                     ┌────────────────────────┐
                     │   Text-to-Speech Layer │
                     └─────────┬──────────────┘
                               │
                               ▼
                     ┌────────────────────────┐
                     │ D-ID Avatar Generation │
                     └─────────┬──────────────┘
                               │
                               ▼
                     ┌────────────────────────┐
                     │   Talking AI Avatar    │
                     └────────────────────────┘
```

---

# Technology Stack

## Core AI/LLM Stack

- OpenAI API
- GPT-based chat models
- OpenAI Text-to-Speech
- OpenAI Embeddings

## RAG Stack

- LangChain
- FAISS Vector Store
- RecursiveCharacterTextSplitter

## Document Processing

- PyPDF
- Unstructured
- python-docx
- openpyxl
- python-pptx

## Audio Processing

- sounddevice
- scipy
- pygame

## Avatar Generation

- D-ID API

## Environment & Utilities

- Python
- Jupyter Notebook
- dotenv
- requests
- numpy

---

# Notebook Structure

## 1. Environment Setup

The initial cells:

- Install required dependencies
- Pin LangChain-compatible versions
- Create `.env` automatically if missing
- Configure `.gitignore`

This makes the notebook more portable and reproducible.

---

## 2. RAG Configuration

This section:

- Defines pharmaceutical system prompts
- Configures retrieval prompts
- Initializes vector databases
- Loads and indexes documents
- Creates retrieval chains

Key implementation areas:

- Document ingestion
- Embedding generation
- Similarity retrieval
- Context-grounded response generation

---

## 3. Question Answering Layer

The function:

```python
ask_pharma_question()
```

Handles:

- Query execution
- Retrieval invocation
- LLM generation
- Source tracking
- Verbose debugging output

---

## 4. Text-to-Speech Layer

The function:

```python
text_to_speech()
```

Uses OpenAI TTS APIs to:

- Convert generated answers into speech
- Save audio responses as MP3
- Optionally auto-play generated audio

---

## 5. Voice Input Layer

The notebook supports microphone-based interaction.

Features include:

- Audio recording
- WAV generation
- Voice input fallback handling
- Device detection

---

## 6. D-ID Avatar Video Layer

The project integrates D-ID APIs to generate talking avatar videos.

Two implementation approaches are explored:

### Custom Avatar Image

Generate videos using a user-provided avatar image.

### Built-in D-ID Presenters

Use professionally designed presenters from the D-ID platform.

---

## 7. Full Pipeline Orchestration

The function:

```python
run_avatar_pipeline()
```

Combines all layers together into one workflow.

Pipeline execution:

1. Accept input
2. Retrieve context
3. Generate response
4. Convert to speech
5. Generate avatar video
6. Save session artifacts

---

# Project Directory Structure

```text
AI-Pharma-Avatar/
│
├── Avatar_demo.ipynb
├── knowledge_docs/
├── pharma_vectorstore/
├── sessions/
├── avatar.jpg
├── .env
├── .gitignore
└── README.md
```

---

# Setup Instructions

## 1. Clone Repository

```bash
git clone <your_repo_url>
cd AI-Pharma-Avatar
```

## 2. Create Virtual Environment

```bash
python -m venv venv
```

### Windows

```bash
venv\Scripts\activate
```

### Linux / Mac

```bash
source venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 4. Configure Environment Variables

Create `.env`

```env
OPENAI_API_KEY=your_openai_key
DID_API_KEY=your_did_key
```

---

## 5. Add Knowledge Documents

Place documents inside:

```text
knowledge_docs/
```

---

## 6. Run Notebook

```bash
jupyter notebook
```

Open:

```text
Avatar_demo.ipynb
```

---

# Example Use Cases

- AI pharmaceutical information assistant
- Interactive knowledge avatar
- Voice-enabled RAG assistant
- Medical information prototype
- Digital human experimentation
- Multimodal AI learning project

---

# Future Improvements

Potential future enhancements include:

- Streaming responses
- Real-time conversational avatars
- Web application deployment
- Memory-enabled conversations
- Agentic workflows
- Better speech recognition
- Multi-language support
- Authentication & access control
- Advanced vector databases
- Real-time webcam avatars

---

# Learning Outcomes

This project provided hands-on exposure to:

- GenAI engineering
- RAG architecture
- Vector databases
- Prompt engineering
- AI orchestration
- Voice AI
- Avatar systems
- API integrations
- Multimodal workflows
- End-to-end AI application design

---

# Disclaimer

This project is intended for educational and experimental purposes.

The assistant is not a replacement for professional medical advice, diagnosis, or treatment.

Always consult qualified healthcare professionals for clinical decisions.

---

# Author Note

This project was built primarily out of curiosity, experimentation, and the desire to understand how modern AI systems can be stitched together into something interactive and human-like.

The goal was not only to use AI models, but to deeply understand the orchestration behind production-style AI workflows.

In a rapidly evolving tech landscape, continuous learning is no longer optional — it is survival.
