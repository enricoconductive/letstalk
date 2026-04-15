# RAG Chatbot - Template Version

A blank template RAG chatbot that instructors can clone and customize with their own topic, documents, and persona.

## What Is This?

This is an **empty template** version of the RAG (Retrieval-Augmented Generation) chatbot. It contains all the code infrastructure but no pre-loaded documents or topic-specific content. Fill in the placeholders with your own:

- **Documents** (PDF, DOCX, or Google Docs)
- **Persona** (chatbot personality and instructions)
- **Starter questions** (example prompts for students)

## Quick Start

**Direct Colab Link:**
```
https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/Empty_Version/RAG_Chatbot_Empty.ipynb
```

**Setup Time:** ~5 minutes (after adding your documents)

**You need to configure:**
1. Your HuggingFace API token
2. Your document links (Step 3)
3. Your persona description (Step 4)
4. Your starter questions (Step 4)

## Steps

| Step | Description | Time |
|------|-------------|------|
| 1 | Install Libraries | ~30 sec |
| 2 | Load Libraries | ~5 sec |
| 3 | **Download Documents** (add your links) | ~10 sec |
| 4 | **Configuration** (token + persona + questions) | - |
| 5 | Test API Connection | ~5 sec |
| 6 | Read Documents | ~30 sec |
| 7 | Create Search Database | ~1 min |
| 8 | Setup Question Answering | ~5 sec |
| 9 | Launch Chat Interface | ~10 sec |

## How to Add Documents

In Step 3, add your documents to the `DOCUMENTS` list:

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

**Important:** Files must be shared as "Anyone with the link can view."

## HuggingFace Token Setup

1. Go to https://huggingface.co/settings/tokens
2. Click "Create new token"
3. Select **"Fine-grained"**
4. Enable **"Make calls to Inference Providers"**
5. Copy the token (starts with `hf_`)

## Features

- **Customizable persona** - Define your chatbot's personality, context, and tasks
- **Multi-format documents** - PDF, DOCX, and Google Docs
- **Document grounding** - Bot only uses information from your documents
- **Source citations** - See which documents were used with relevant quote snippets
- **Conversation memory** - Follow-up questions work
- **30-second timeout** - Prevents hanging
- **Concise responses** - ~200 words max

## Troubleshooting

| Issue | Solution |
|-------|----------|
| API 503 error | Model loading - wait 30 seconds |
| API 401/403 error | Check token has "Inference Providers" permission |
| Download failed | Ensure Google Drive file is shared publicly |
| Timeout errors | Try shorter/simpler questions |
| No documents found | Add your document links in Step 3 |

## License

Same as main project - see root LICENSE file.
