# Student Guide - Legal Drafting Chatbot

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
3. Run **Step 3** (Download) - wait ~30 seconds for 28 documents
4. Run **Step 4** (Config) - **paste your token here first!**
5. Run **Step 5** (Test) - should say "SUCCESS!"
6. Run **Steps 6-8** - wait ~2 minutes total
7. Run **Step 9** (Launch) - copy the `https://xxxxx.gradio.live` link

### Step 4: Use the Chatbot
- Open the Gradio link in a **new browser tab**
- Ask questions about the Merritt v. Merritt case or petition drafting
- Each response includes source citations with relevant quotes
- **Note:** The bot ONLY uses information from the loaded documents. If the answer isn't in the documents, it will tell you.

---

## Workshop Scenario

> You are learning to draft a legally sound petition based on the landmark contract law case **Merritt v. Merritt**, using the IRAC method (Issue, Rule, Application, Conclusion). The chatbot will guide you through drafting best practices and the case facts.

## Example Questions
- "How do I apply the IRAC method to the Merritt v. Merritt case?"
- "What are the key best practices for drafting a legal petition?"
- "Can you review my argument about the intention to create legal relations in Merritt?"
- "What should be included in the 'Application' section for this specific case?"
- "How can I structure a two-paragraph petition to convince the judge the agreement is binding?"

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
