# Empty/Template Version - RAG Chatbot

## Overview

A blank template RAG (Retrieval-Augmented Generation) chatbot that instructors can clone and customize with their own topic, documents, and persona. Contains all the code infrastructure with placeholder content.

## Purpose

This is a **template version** - no documents, persona, or starter questions are pre-configured. Instructors fill in:
- Document links (Step 3)
- Persona name and description (Step 4)
- Starter questions (Step 4)

## Features

- **Blank template** - No pre-loaded content; add your own documents and persona
- **Multi-format support** - PDF, DOCX, and Google Docs
- **Document grounding** - Bot only uses information from provided documents
- **Source citations** - Shows document name, section number, and relevant query-matched snippets
- **Conversation memory** - Remembers last 3 exchanges for follow-up questions
- **Concise responses** - ~200 words max (MAX_OUTPUT_TOKENS=300)
- **30-second timeout** - Prevents hanging

## Technical Stack

| Component | Technology |
|-----------|------------|
| LLM | Qwen/Qwen2.5-72B-Instruct (HuggingFace API) |
| Embeddings | all-MiniLM-L6-v2 (Sentence Transformers) |
| Vector DB | ChromaDB |
| Interface | Gradio |
| Platform | Google Colab (free tier) |

## Configuration

All settings in Step 4 (Cell 8):

```python
# API
HUGGINGFACE_TOKEN = "hf_..."

# Model
MODEL_NAME = "Qwen/Qwen2.5-72B-Instruct"
MAX_OUTPUT_TOKENS = 300  # ~200 words max

# Persona (customize these)
PERSONA_NAME = "Your Persona Name"
PERSONA_DESCRIPTION = "..."  # [PERSONA], [CONTEXT], [TASK] structure

# Retrieval
NUM_RETRIEVED_DOCS = 7
CHUNK_SIZE = 1000
OVERLAP = 200

# Memory
CONVERSATION_MEMORY = 3
SHOW_SOURCES = True
```

## Persona Template

The persona uses a structured format:

- **[PERSONA]** - Chatbot personality and tone
- **[CONTEXT]** - Workshop scenario and key documents
- **[TASK]** - Specific tasks and instructions for the chatbot

## Structure

| Step | Description |
|------|-------------|
| 1 | Install libraries |
| 2 | Load libraries |
| 3 | Download documents (add your links) |
| 4 | Configuration (token + persona + questions) |
| 5 | Test API connection |
| 6 | Read documents |
| 7 | Create search database |
| 8 | Setup question answering |
| 9 | Launch chat interface |

## Cost

**100% FREE**
- HuggingFace API: ~300 requests/hour
- Google Colab: Free tier
- No VPN required (Hong Kong compatible)

## Quick Start

1. Open: `https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/Empty_Version/RAG_Chatbot_Empty.ipynb`
2. Add your documents in Step 3
3. Get HuggingFace token (free): https://huggingface.co/settings/tokens
4. Configure persona and starter questions in Step 4
5. Run all cells
6. Open the Gradio link in a new tab

---

**Last Updated:** April 2026
