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
- **CSV Export:** Run Cell 22
- **Visualizations:** Run Cell 25 (line graph), Cell 27 (bar chart) - requires 3+ messages
- **Reset:** Run Cell 24 (new conversation)

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

## Viewing Empathy Visualizations

After chatting for **at least 3 messages**, you can view interactive graphs showing your empathy progress.

### Available Visualizations

**Cell 25: Line Graph** - Shows empathy trend across all messages
- Overall score progression
- Interactive hover to see exact scores
- HTML export available

**Cell 27: Multi-Dimension Bar Chart** - Breakdown of 5 dimensions
- Compare warmth, questions, emotions, perspective, listening
- See which areas are strongest/weakest
- Helps identify specific skills to improve

### How to View
1. Send at least 3 messages in the chat
2. Run **Cell 25** for line graph
3. Run **Cell 27** for bar chart
4. Graphs appear below the cell with interactive features

**💡 Tip:** After 10 messages (when report generates), visualizations become more meaningful!

---

## Source Citations

The chatbot can **show which PDFs** were used to answer your question.

### How to Enable/Disable

In **Cell 8**, find this setting:
```python
SHOW_SOURCES = True  # Set to False to hide sources
```

- **True:** Shows source documents below each answer (helpful for verification)
- **False:** Clean answers only (better for conversational flow)

**Default:** `True` (sources shown)

---

## Testing Conversation Memory

The chatbot can **remember previous messages** in your conversation, making follow-up questions work naturally.

### What is Conversation Memory?

When enabled, the bot remembers recent exchanges:
- **"What are your beliefs?" → Bot answers**
- **"Tell me more"** ← Bot remembers you asked about beliefs

### Default Setting
- **CONVERSATION_MEMORY = 3** (remembers last 3 exchanges)
- Stored in Cell 8
- Change to 0 to disable, or 5-10 for longer memory

### How to Test If Memory Works

**Option 1: Live Test with Debug Mode**
1. Set `DEBUG_MEMORY = True` in Cell 8
2. Run all cells through Cell 20 (launch chat)
3. In the console, you'll see message structure for each response
4. Check that history pairs are included

**Option 2: Real Conversation Test**
1. Launch chat (Cell 20)
2. Ask: **"What are your main beliefs?"**
3. Bot answers
4. Ask: **"Tell me more"** or **"Why is that important?"**
5. ✅ If bot references your first question → Memory working!
6. ❌ If bot doesn't understand context → Check CONVERSATION_MEMORY setting

### Example Debug Output

When `DEBUG_MEMORY = True`, you'll see:

```
================================================================================
🧠 DEBUG: CONVERSATION MEMORY
================================================================================
📊 Sending 7 messages to HuggingFace API:
   • System message: 1
   • History pairs: 2 (from last 3 exchanges)
   • Current question: 1

📋 Message structure:
   [0] 🖥️ system     | You are [persona]...
   [1] 👤 user       | What are your beliefs?
   [2] 🤖 assistant  | I believe in...
   [3] 👤 user       | Tell me more
   [4] 🤖 assistant  | Science requires...
   [5] 👤 user       | Why is that important?
================================================================================
```

### Troubleshooting Memory

| Issue | Solution |
|-------|----------|
| Bot doesn't remember context | Check `CONVERSATION_MEMORY > 0` in Cell 8 |
| Debug output not showing | Set `DEBUG_MEMORY = True` in Cell 8 |
| Memory too short/long | Adjust CONVERSATION_MEMORY (2-10) in Cell 8 |

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
After 10 messages → Run Cell 22 (export CSV) + Cell 25/27 (visualizations)
Modify settings → Edit Cell 8 → Re-run from Cell 8 onwards
New conversation → Run Cell 24 (reset)
```

### Key Settings (Cell 8)

```python
MODEL_NAME = "meta-llama/Meta-Llama-3.1-8B-Instruct"  # ✅ Verified working
TEMPERATURE = 0.7  # 0.3=focused, 1.0=creative
CONVERSATION_MEMORY = 3  # Remember last 3 exchanges (0=off, 10=long)
DEBUG_MEMORY = False  # True=show message structure in console
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
