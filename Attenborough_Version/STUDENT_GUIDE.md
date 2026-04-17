# Student Guide - RAG Chatbot

## Quick Start (5 minutes)

### Step 1: Open the Notebook
Click this link to open in Google Colab:
```
https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/Empty_Version/RAG_Chatbot_Empty.ipynb
```

### Step 2: Get Your Free API Token
1. Go to https://huggingface.co and sign up (free)
2. Go to https://huggingface.co/settings/tokens
3. Click **"Create new token"**
4. Select **"Fine-grained"** type
5. Enable **"Make calls to Inference Providers"**
6. Copy the token (starts with `hf_`)

### Step 3: Run the Notebook
1. Run **Step 1** (Install) - wait ~30 seconds
2. Run **Step 2** (Load) - instant
3. Run **Step 3** (Download) - downloads your documents
4. Run **Step 4** (Config) - **paste your token here first!**
5. Run **Step 5** (Test) - should say "SUCCESS!"
6. Run **Steps 6-8** - wait ~2 minutes total
7. Run **Step 9** (Launch) - copy the `https://xxxxx.gradio.live` link

### Step 4: Use the Chatbot
- Open the Gradio link in a **new browser tab**
- Ask questions about the loaded documents
- Each response includes source citations with relevant quotes
- **Note:** The bot ONLY uses information from the loaded documents. If the answer isn't in the documents, it will tell you.

---

## Example Questions
- Try the starter questions provided in the chat interface
- Ask about specific topics covered in the documents
- Ask follow-up questions (the bot remembers recent conversation)

## Troubleshooting

| Problem | Solution |
|---------|----------|
| API 503 error | Model loading - wait 30 seconds, retry |
| API 401/403 error | Token needs "Inference Providers" permission |
| Empty responses | Try a different model in Step 4 |
| Timeout | Ask shorter/simpler questions |
| "Cannot find this" response | The answer isn't in the documents - this is expected behavior |

## Need Help?
- Check your token has correct permissions
- Make sure you ran all steps in order
- Try restarting the runtime: Runtime > Restart runtime

---
*Licensed under CC BY-NC-SA 4.0 | Bertelli, E. (2026)*
