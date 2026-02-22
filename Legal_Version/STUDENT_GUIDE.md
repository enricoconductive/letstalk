# Student Guide - Legal RAG Chatbot

## Quick Start (5 minutes)

### Step 1: Open the Notebook
Click this link to open in Google Colab:
```
https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/Legal_Version/RAG_Chatbot_Legal.ipynb
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
3. Run **Step 3** (Download) - wait ~30 seconds for 26 documents
4. Run **Step 4** (Config) - **paste your token here first!**
5. Run **Step 5** (Test) - should say "SUCCESS!"
6. Run **Steps 6-8** - wait ~2 minutes total
7. Run **Step 9** (Launch) - copy the `https://xxxxx.gradio.live` link

### Step 4: Use the Chatbot
- Open the Gradio link in a **new browser tab**
- Ask questions about Lilly's case
- Each response includes source citations with relevant quotes
- **Note:** The bot ONLY uses information from the loaded documents. If the answer isn't in the documents, it will tell you.

---

## Workshop Scenario

> Lilly invested $50,000 in a business with her husband David. They are now divorcing, and David cannot repay the investment. Help Lilly find legal remedies.

## Example Questions
- "What legal options does Lilly have to recover her investment?"
- "How should Lilly document her investment for court?"
- "Can Lilly claim the investment as a marital asset?"

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
