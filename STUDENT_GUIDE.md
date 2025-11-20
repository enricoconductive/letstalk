# Student Guide: RAG Chatbot for Empathy Training

**Welcome!** This guide helps you set up the RAG chatbot for practicing empathic communication.

---

## Quick Start (5 Minutes)

### What Is This?
An AI chatbot that:
- Answers questions based on your PDF documents
- Analyzes YOUR empathy in conversations
- Generates feedback reports after 10 messages
- Works in Hong Kong without VPN (HuggingFace API, 100% free)

### Notebook to Use
📓 **`RAG_Chatbot_HuggingFace.ipynb`** - This is the current version

### Setup Steps

1. **Open** https://colab.research.google.com/
2. **Upload** `RAG_Chatbot_HuggingFace.ipynb`
3. **Get HuggingFace token** (see below) → Paste in Cell 8
4. **Click** "Runtime → Run All"
5. **Authorize** Google Drive when prompted
6. **If Cell 10 shows "Model loading":** Wait 30s, re-run Cell 10
7. **Copy** public link: `https://xxxxx.gradio.live`
8. **⚠️ Open link in NEW browser tab** (not in Colab)
9. **Start chatting!**

---

## Getting Your HuggingFace Token

### Quick Steps:

1. Sign up at https://huggingface.co/ (free)
2. Go to https://huggingface.co/settings/tokens
3. Click **"New token"**
4. **Name:** "Empathy Chatbot"
5. **Type:** **"Fine-grained"** ⚠️ (NOT "Read")
6. **Enable:** ✅ "Make calls to Inference Providers" (under "Inference" section)
7. **Copy** token (starts with `hf_`)
8. **Paste** into Cell 8: `HUGGINGFACE_TOKEN = "hf_your_token"`

### ⚠️ Critical Requirements
- **Token type MUST be "Fine-grained"** with "Inference" permission
- ❌ "Read" tokens WILL NOT work (cannot make API calls)
- ✅ Free tier: ~300 requests/hour
- ✅ Works in Hong Kong (blocked in mainland China)

---

## Finding PDF Paths in Google Drive

### Format
`/content/drive/MyDrive/folder_name/file.pdf`

### Example
- **In Drive:** `My Drive/School/AI/speech.pdf`
- **Path to use:** `/content/drive/MyDrive/School/AI/speech.pdf`

### Easy Method (in Colab)
1. Click folder icon (left sidebar)
2. Navigate to your PDF
3. Right-click → "Copy path"
4. Paste into Cell 8 `PDF_PATHS` list

---

## Understanding Empathy Scoring

### 5 Dimensions (0-20 points each)

1. **Sentiment/Warmth** - Positive, supportive tone
2. **Open Questions** - "How/why/what" vs "yes/no"
3. **Emotion Recognition** - Using emotion words
4. **Perspective-Taking** - "From your view..."
5. **Active Listening** - "Tell me more", paraphrasing

**Total Score:** 0-100 points
- 80-100: Excellent empathy
- 60-79: Good empathy
- 40-59: Moderate empathy
- 20-39: Developing
- 0-19: Needs practice

### Report & Export
- **Report:** Generated after 10 messages
- **CSV Export:** Run Cell 21
- **Reset:** Run Cell 23 (new conversation)

### Tips to Improve Score

✅ **DO:**
- Ask "how" and "why" questions
- Use emotion words ("frustrated," "worried," "excited")
- Say "From your perspective..." or "You feel..."
- Say "Tell me more" or paraphrase

❌ **AVOID:**
- Closed questions ("Did you?")
- Judging ("You shouldn't feel...")
- Dismissing ("It's not a big deal")

---

## Troubleshooting

### API Errors

| Error | Cause | Fix |
|-------|-------|-----|
| **401/403 Invalid token** | Token lacks "Inference" permission | Create NEW "Fine-grained" token with "Inference" enabled |
| **503 Model loading** | ✅ Normal on first call! | Wait 30s, re-run Cell 10. Subsequent: 5-10s |
| **404 Not Found** | Model incompatible with API | Use `meta-llama/Meta-Llama-3.1-8B-Instruct` (Cell 8) |
| **Rate limit** | Too many requests | Wait 10-15 minutes (free tier: 300/hour) |
| **Timeout (30s)** | Slow connection or complex query | Try simpler question, check internet |

### PDF Errors

| Error | Fix |
|-------|-----|
| **File not found** | Verify Drive mounted (Cell 6), path starts with `/content/drive/MyDrive/` |
| **No text extracted** | PDF is scanned image (not searchable) or password-protected |

### Gradio Issues

| Issue | Fix |
|-------|-----|
| **Interface restarts** | ✅ Use PUBLIC link (`https://xxxxx.gradio.live`) in NEW tab, not in Colab |
| **No empathy report** | Must send exactly 10 messages, check for error messages |
| **Responses don't match persona** | Make `PERSONA_DESCRIPTION` more detailed (Cell 8), verify PDFs |

---

## Quick Reference

### Workflow

```
First Setup → Run All → Authorize Drive → Wait for "Model loading" (30s)
           → Copy public link → Open in NEW tab → Start chatting
After 10 messages → Run Cell 21 (export CSV)
New conversation → Run Cell 23 (reset)
```

### Key Settings (Cell 8)

```python
MODEL_NAME = "meta-llama/Meta-Llama-3.1-8B-Instruct"  # ✅ Verified working
TEMPERATURE = 0.7  # 0.3=focused, 1.0=creative
SHOW_SOURCES = True  # Show which PDFs used
```

**⭐ Important:** Use Meta-Llama-3.1-8B - verified compatible with `chat_completion()` API on HuggingFace free tier.

---

## Need Help?

- **HuggingFace Docs:** https://huggingface.co/docs/api-inference/
- **Token Settings:** https://huggingface.co/settings/tokens
- **Colab Help:** https://research.google.com/colaboratory/faq.html

---

**Happy Learning! 🤖💙**

*Practice empathy through AI conversations. 100% free.*
