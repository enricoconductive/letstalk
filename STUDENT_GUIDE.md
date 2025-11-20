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

## Using Real-Time Empathy Feedback

The chatbot now shows **live empathy analysis as you type**, helping you improve before sending!

### What You'll See

When you launch the chat interface (Cell 21), you'll see **two panels side-by-side**:

- **Left Panel (2/3 width):** Chat conversation
- **Right Panel (1/3 width):** Real-time empathy feedback

### How It Works

1. **Start typing** in the message box
2. **Feedback updates automatically** after you pause (~300ms)
3. **See your score** change in real-time (0-100 scale)
4. **Get smart suggestions** based on what you're writing
5. **Revise your message** before sending
6. **Send** when you're happy with your score

### Understanding the Live Score

**Score Display:**
- 🌟 **80-100:** Excellent empathy
- ✅ **60-79:** Good empathy
- ⚠️ **40-59:** Moderate empathy
- 💡 **0-39:** Keep trying

**Dimension Breakdown:**
```
💙 Warmth: 15/20
❓ Questions: 10/20
😊 Emotions: 8/20
👁️ Perspective: 5/20
👂 Listening: 12/20
```

### Smart Suggestions

The feedback panel shows **context-aware tips** based on what you're typing:

- **Low warmth:** 💡 "Try: 'I appreciate...' or 'Thank you for...'"
- **Closed question:** 💡 "Better: Ask 'How...' or 'Why...' instead"
- **Weak emotion recognition:** 💡 "Name the feeling: 'frustrated,' 'worried'"
- **Missing perspective:** 💡 "Try: 'From your view...' or 'You might feel...'"
- **Low listening:** 💡 "Show engagement: 'Tell me more' or paraphrase"

### Example: Using Real-Time Feedback

**❌ First Draft (Score: 25/100):**
```
Did you like the speech?
```
**Feedback:** ⚠️ Moderate - 25/100 | Closed question detected

**✅ Revised (Score: 75/100):**
```
How did you feel about the key points in your speech?
I'm curious about what motivated those ideas.
```
**Feedback:** ✅ Good - 75/100 | Open question ✓ | Emotion word ✓

### Tips for Effective Use

**✅ DO:**
- Use feedback to **experiment** with different phrasings
- **Revise before sending** - it's practice, not a test!
- Try to hit **60+ points** consistently

**❌ DON'T:**
- Obsess over perfect scores (80+ is rare!)
- Send immediately without checking feedback
- Ignore suggestions - they're context-specific

### Technical Details

- **Analysis speed:** <10ms (nearly instant)
- **Feedback updates:** ~300ms after you stop typing (debounced)
- **Live feedback:** For practice only, doesn't affect final score
- **Final score:** Calculated when you send the message
- **10-message report:** Uses sent messages, not drafts

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

**Option 1: Quick Test (Cell 5B)**
1. Run Cell 10 (API test) first
2. Run **Cell 5B: Test Conversation Memory**
3. Check output shows message structure
4. Verify it says "✅ PASS - Memory structure is correct"

**Option 2: Live Test with Debug Mode**
1. Set `DEBUG_MEMORY = True` in Cell 8
2. Run all cells through Cell 19 (launch chat)
3. In the console, you'll see message structure for each response
4. Check that history pairs are included

**Option 3: Real Conversation Test**
1. Launch chat (Cell 19)
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
| Cell 5B test fails | Check CONVERSATION_MEMORY value, restart runtime |
| Memory seems too short | Increase CONVERSATION_MEMORY to 5 or 10 |
| Responses too slow | Reduce CONVERSATION_MEMORY to 2 or 3 |

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
