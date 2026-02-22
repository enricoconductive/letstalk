# RAG Chatbot - Legal/Professional Version

A streamlined RAG chatbot for legal document Q&A with **pre-loaded documents** (no setup required).

## Workshop Scenario

> You are a legal consultant helping clients going through divorce who ran a business together. Wife Lilly invested $50,000 into the business, but it has since gone into difficulties and husband/ex-husband David has been unable to repay Lilly.

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

Documents are automatically downloaded from public Google Drive links:

| Document | Description |
|----------|-------------|
| Affidavit_Template.pdf | Legal affidavit template |
| *(more coming)* | |

### Adding More Documents

In Step 3, add entries to `PDF_DOCUMENTS`:

```python
PDF_DOCUMENTS = [
    ("Affidavit_Template.pdf", "1z6fCNZEQloRI_uS6W_DxGJh6sSbBiJUA"),
    ("Your_Document.pdf", "YOUR_GOOGLE_DRIVE_FILE_ID"),  # Add here
]
```

**To get the FILE_ID:**
1. Share the file on Google Drive ("Anyone with the link can view")
2. Copy the share link: `https://drive.google.com/file/d/FILE_ID_HERE/view?usp=sharing`
3. Extract the FILE_ID from the URL

## HuggingFace Token Setup

1. Go to https://huggingface.co/settings/tokens
2. Click "Create new token"
3. Select **"Fine-grained"**
4. Enable **"Make calls to Inference Providers"**
5. Copy the token (starts with `hf_`)

## Features

- **Pre-loaded documents** - No Google Drive mounting needed
- **Source citations** - See which documents were used
- **Conversation memory** - Follow-up questions work
- **30-second timeout** - Prevents hanging
- **Scenario-specific prompts** - Tailored for divorce/business disputes

## Starter Questions

- "What legal options does Lilly have to recover her $50,000 investment?"
- "How should Lilly document her investment in the business for court?"
- "What should be included in an affidavit for this case?"
- "Can Lilly claim the investment as a marital asset in the divorce?"
- "What evidence would strengthen Lilly's case for repayment?"

## Troubleshooting

| Issue | Solution |
|-------|----------|
| API 503 error | Model loading - wait 30 seconds |
| API 401/403 error | Check token has "Inference Providers" permission |
| Download failed | Ensure Google Drive file is shared publicly |
| Timeout errors | Try shorter/simpler questions |

## License

Same as main project - see root LICENSE file.
