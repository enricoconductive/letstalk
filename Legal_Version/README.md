# RAG Chatbot - Legal/Professional Version

A streamlined RAG (Retrieval-Augmented Generation) chatbot for professional document Q&A.

## Overview

This is a simplified version of the main RAG chatbot, designed for:
- Legal document analysis
- Professional knowledge bases
- Research document Q&A
- Any document-based question answering

**Key Differences from Main Version:**
- No empathy tracking features
- All configuration consolidated in one cell (Step 4)
- Streamlined 9-step workflow (vs 16 steps)
- 19 cells total (vs 30 cells)

## Quick Start

1. Open `RAG_Chatbot_Legal.ipynb` in Google Colab
2. Run Steps 1-3 (Install, Load, Connect Drive)
3. Configure Step 4 (API token, persona, PDF paths)
4. Run Steps 5-9 (Test, Process, Database, QA, Launch)

## Structure

| Step | Description | Time |
|------|-------------|------|
| 1 | Install Libraries | ~30 sec |
| 2 | Load Libraries | ~5 sec |
| 3 | Connect Google Drive | ~10 sec |
| 4 | **Configuration** (all settings) | - |
| 5 | Test API Connection | ~5 sec |
| 6 | Read PDF Files | 1-2 min |
| 7 | Create Search Database | 1-2 min |
| 8 | Setup Question Answering | ~5 sec |
| 9 | Launch Chat Interface | ~10 sec |

## Configuration (Step 4)

All settings are organized into sections:

```python
# SECTION 1: API CREDENTIALS (REQUIRED)
HUGGINGFACE_TOKEN = "hf_..."

# SECTION 2: MODEL SETTINGS
MODEL_NAME = "meta-llama/Meta-Llama-3.1-8B-Instruct"
TEMPERATURE = 0.7
MAX_OUTPUT_TOKENS = 300

# SECTION 3: PERSONA CONFIGURATION (REQUIRED)
PERSONA_NAME = "Legal Expert"
PERSONA_DESCRIPTION = "..."

# SECTION 4: PDF DOCUMENTS (REQUIRED)
PDF_PATHS = [...]

# SECTION 5: RETRIEVAL SETTINGS
NUM_RETRIEVED_DOCS = 7
CHUNK_SIZE = 1000
OVERLAP = 200

# SECTION 6: CONVERSATION SETTINGS
CONVERSATION_MEMORY = 3
SHOW_SOURCES = True
DEBUG_MEMORY = False

# SECTION 7: STARTER QUESTIONS (OPTIONAL)
STARTER_QUESTIONS = [...]
```

## Features

- **Source Citations**: See which PDFs were used for each answer
- **Conversation Memory**: Follow-up questions work naturally
- **30-Second Timeout**: Prevents indefinite hanging
- **Debug Mode**: See exactly what's sent to the API

## Requirements

- Google Colab (free tier)
- HuggingFace account (free, ~300 requests/hour)
- PDF files in Google Drive

## API Token Setup

1. Go to https://huggingface.co/settings/tokens
2. Click "Create new token"
3. Select "Fine-grained"
4. Enable "Make calls to Inference Providers"
5. Copy the token (starts with `hf_`)

## Troubleshooting

| Issue | Solution |
|-------|----------|
| API 503 error | Model loading - wait 30 seconds |
| API 401/403 error | Check token permissions |
| No text from PDFs | Check file paths, ensure not password-protected |
| Timeout errors | Try shorter questions |
| Rate limit | Wait 10-15 minutes |

## License

Same as main project - see root LICENSE file.
