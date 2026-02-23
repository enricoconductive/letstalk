# RAG Chatbot - Legal/Professional Version

A streamlined RAG chatbot for legal document Q&A with **pre-loaded documents** (no setup required).

## Workshop Scenario

> You are facilitating a legal workshop focused on the landmark contract law case **Merritt v. Merritt**. Students are learning to draft legal petitions using the IRAC method, guided by petition best practices and the case materials.

## Quick Start

**Direct Colab Link:**
```
https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/Legal_Version/RAG_Chatbot_Legal.ipynb
```

**Setup Time:** ~5 minutes

**Only 1 thing to configure:** Your HuggingFace API token

## Steps

| Step | Description | Time |
|------|-------------|------|
| 1 | Install Libraries | ~30 sec |
| 2 | Load Libraries | ~5 sec |
| 3 | **Download Documents** (automatic) | ~10 sec |
| 4 | Configuration (API token only) | - |
| 5 | Test API Connection | ~5 sec |
| 6 | Read PDF Files | ~30 sec |
| 7 | Create Search Database | ~1 min |
| 8 | Setup Question Answering | ~5 sec |
| 9 | Launch Chat Interface | ~10 sec |

## Pre-loaded Documents

28 legal documents are automatically downloaded, covering:
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

### Adding More Documents

In Step 3, add entries to `DOCUMENTS` (supports PDF, DOCX, and Google Docs):

```python
DOCUMENTS = [
    # PDF/DOCX: ("filename", "GOOGLE_DRIVE_FILE_ID", "pdf" or "docx")
    ("Your_Document.pdf", "YOUR_GOOGLE_DRIVE_FILE_ID", "pdf"),

    # Google Docs: ("filename.txt", "GOOGLE_DOC_ID", "gdoc")
    ("Your_Doc.txt", "YOUR_GOOGLE_DOC_ID", "gdoc"),
]
```

**To get IDs:**
- **PDF/DOCX:** Share link `https://drive.google.com/file/d/FILE_ID/view` -> extract FILE_ID
- **Google Doc:** Doc URL `https://docs.google.com/document/d/DOC_ID/edit` -> extract DOC_ID

## HuggingFace Token Setup

1. Go to https://huggingface.co/settings/tokens
2. Click "Create new token"
3. Select **"Fine-grained"**
4. Enable **"Make calls to Inference Providers"**
5. Copy the token (starts with `hf_`)

## Features

- **Pre-loaded documents** - 28 legal documents, no Google Drive mounting needed
- **Legal Drafting Educator persona** - Professional tone, IRAC-focused guidance
- **Anti-hallucination mode** - Strict document grounding; bot says "I cannot find this" if not in documents
- **Document routing** - Uses Petition Best Practices for drafting, Merritt case for facts
- **Source citations** - See which documents were used with relevant quote snippets
- **Conversation memory** - Follow-up questions work
- **30-second timeout** - Prevents hanging
- **Concise responses** - ~200 words max for clear, actionable advice

## Starter Questions

- "How do I apply the IRAC method to the Merritt v. Merritt case?"
- "What are the key best practices for drafting a legal petition?"
- "Can you review my argument about the intention to create legal relations in Merritt?"
- "What should be included in the 'Application' section for this specific case?"
- "How can I structure a two-paragraph petition to convince the judge the agreement is binding?"

## Troubleshooting

| Issue | Solution |
|-------|----------|
| API 503 error | Model loading - wait 30 seconds |
| API 401/403 error | Check token has "Inference Providers" permission |
| Download failed | Ensure Google Drive file is shared publicly |
| Timeout errors | Try shorter/simpler questions |

## License

Same as main project - see root LICENSE file.
