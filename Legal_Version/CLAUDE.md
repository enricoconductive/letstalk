# Legal Version - RAG Chatbot

## Overview

A streamlined RAG (Retrieval-Augmented Generation) chatbot for legal document Q&A, specifically designed for divorce and business dispute scenarios.

## Workshop Scenario

> You are a legal consultant helping clients going through divorce who ran a business together. Wife Lilly invested $50,000 into the business, but it has since gone into difficulties and husband/ex-husband David has been unable to repay Lilly.

## Features

- **Pre-loaded documents** - 26 legal documents automatically downloaded (no Google Drive mounting)
- **Multi-format support** - PDF, DOCX, and Google Docs
- **Source citations** - Shows document name, section number, and quoted text snippet
- **Conversation memory** - Remembers last 3 exchanges for follow-up questions
- **Concise responses** - ~100 words max for clear, actionable advice
- **30-second timeout** - Prevents hanging

## Technical Stack

| Component | Technology |
|-----------|------------|
| LLM | Qwen/Qwen2.5-72B-Instruct (HuggingFace API) |
| Embeddings | all-MiniLM-L6-v2 (Sentence Transformers) |
| Vector DB | ChromaDB |
| Interface | Gradio |
| Platform | Google Colab (free tier) |

## Document Library

26 legal documents covering:
- Financial dispute resolution
- Divorce grounds and procedures (Hong Kong)
- Asset division in divorce
- Maintenance/alimony assessment
- Matrimonial property division
- Personal injury awards in divorce
- Affidavit templates
- Marriage ordinance and registration
- Cross-border divorce issues

## Configuration

All settings in Step 4 (Cell 8):

```python
# API
HUGGINGFACE_TOKEN = "hf_..."

# Model
MODEL_NAME = "Qwen/Qwen2.5-72B-Instruct"
MAX_OUTPUT_TOKENS = 125  # ~100 words

# Retrieval
NUM_RETRIEVED_DOCS = 7
CHUNK_SIZE = 1000
OVERLAP = 200

# Memory
CONVERSATION_MEMORY = 3
SHOW_SOURCES = True
```

## Structure

| Step | Description |
|------|-------------|
| 1 | Install libraries |
| 2 | Load libraries |
| 3 | Download documents (automatic) |
| 4 | Configuration (API token only) |
| 5 | Test API connection |
| 6 | Read documents |
| 7 | Create search database |
| 8 | Setup question answering |
| 9 | Launch chat interface |

## Differences from Main Version

| Feature | Main Version | Legal Version |
|---------|--------------|---------------|
| Empathy tracking | Yes (5 dimensions) | No |
| Visualizations | Plotly charts | No |
| CSV export | Yes | No |
| Document source | Google Drive mount | Public URL download |
| Steps | 16 | 9 |
| Cells | 30 | 19 |
| Focus | Empathy training | Legal Q&A |

## Cost

**100% FREE**
- HuggingFace API: ~300 requests/hour
- Google Colab: Free tier
- No VPN required (Hong Kong compatible)

## Quick Start

1. Open: `https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/Legal_Version/RAG_Chatbot_Legal.ipynb`
2. Get HuggingFace token (free): https://huggingface.co/settings/tokens
3. Paste token in Step 4
4. Run all cells
5. Open the Gradio link in a new tab

---

**Last Updated:** February 2026
