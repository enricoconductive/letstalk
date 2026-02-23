# Legal Version - RAG Chatbot

## Overview

A streamlined RAG (Retrieval-Augmented Generation) chatbot for legal document Q&A, designed as a legal drafting educator for the Merritt v. Merritt case study workshop.

## Workshop Scenario

> You are facilitating a legal workshop focused on the landmark contract law case Merritt v. Merritt. Students are learning to draft legal petitions using the IRAC method, guided by petition best practices and the case materials.

## Features

- **Pre-loaded documents** - 28 legal documents automatically downloaded (no Google Drive mounting)
- **Multi-format support** - PDF, DOCX, and Google Docs
- **Anti-hallucination mode** - Strict document grounding; bot says "I cannot find this" if not in documents
- **Source citations** - Shows document name, section number, and relevant query-matched snippets
- **Conversation memory** - Remembers last 3 exchanges for follow-up questions
- **Concise responses** - ~200 words max (MAX_OUTPUT_TOKENS=300)
- **30-second timeout** - Prevents hanging
- **Document routing** - Uses Petition Best Practices for drafting guidance, Merritt v. Merritt for case facts

## Technical Stack

| Component | Technology |
|-----------|------------|
| LLM | Qwen/Qwen2.5-72B-Instruct (HuggingFace API) |
| Embeddings | all-MiniLM-L6-v2 (Sentence Transformers) |
| Vector DB | ChromaDB |
| Interface | Gradio |
| Platform | Google Colab (free tier) |

## Document Library

28 legal documents covering:
- Financial dispute resolution
- Divorce grounds and procedures (Hong Kong)
- Asset division in divorce
- Maintenance/alimony assessment
- Matrimonial property division
- Personal injury awards in divorce
- Affidavit templates
- Marriage ordinance and registration
- Cross-border divorce issues
- **Petition drafting best practices** (workshop-specific)
- **Merritt v. Merritt case materials** (workshop-specific)

## Configuration

All settings in Step 4 (Cell 8):

```python
# API
HUGGINGFACE_TOKEN = "hf_..."

# Model
MODEL_NAME = "Qwen/Qwen2.5-72B-Instruct"
MAX_OUTPUT_TOKENS = 300  # ~200 words max

# Retrieval
NUM_RETRIEVED_DOCS = 7
CHUNK_SIZE = 1000
OVERLAP = 200

# Memory
CONVERSATION_MEMORY = 3
SHOW_SOURCES = True
```

## Persona

The bot operates as a **Legal Drafting Educator** with a structured persona:

- **[PERSONA]** - Professional Legal Practitioner and Educator. Direct, objective, no filler or praise.
- **[CONTEXT]** - Facilitating a Merritt v. Merritt workshop. Knowledge base relies on Petition_Best_Practices.txt and Merritt_v_Merritt.txt.
- **[TASK]** - Review student arguments, guide IRAC-method petition drafting, correct grammar, route answers to the correct source document.

## Anti-Hallucination Design

The bot uses strict document grounding to prevent hallucination:

1. **System prompt** instructs the model to ONLY use provided context
2. **Explicit fallback**: "I cannot find this in the provided documents"
3. **No outside knowledge**: Model is told not to use pre-trained legal knowledge
4. **Quote requirement**: Model should quote directly from documents
5. **Document routing**: Petition Best Practices for structure/drafting, Merritt case for facts/legal grounds
6. **Concise responses**: MAX_OUTPUT_TOKENS=300 (~200 words) keeps answers focused

**Citation improvements:**
- `extract_relevant_snippet()` finds query-relevant sentences instead of first 150 chars
- Snippets are selected based on keyword overlap with the user's question

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
| Focus | Empathy training | Legal drafting (IRAC) |

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
