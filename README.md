# Let's Talk - RAG Chatbot with Empathy Training

An educational RAG (Retrieval-Augmented Generation) chatbot that teaches empathic communication skills through interactive conversations. Students practice empathy while chatting with customizable AI personas trained on their own PDF documents.

## Features

- **Three Versions Available:**
  - `RAG_Chatbot_Original.ipynb` - Basic RAG chatbot (Google Gemini API)
  - `RAG_Chatbot_Basic.ipynb` - With empathy tracking (Google Gemini API)
  - `RAG_Chatbot_HuggingFace.ipynb` - Hong Kong compatible, no VPN needed (HuggingFace API)

- **Empathy Assessment System:**
  - Real-time analysis of 5 empathy dimensions
  - Automated scoring and feedback reports
  - CSV export for research and progress tracking
  - Based on VADER sentiment analysis + linguistic pattern matching

- **100% Free:**
  - Google Gemini API (free tier, global access with VPN in China/HK)
  - HuggingFace Inference API (free tier, ~300 requests/hour, Hong Kong compatible)
  - Runs on Google Colab (no local setup required)

- **Fully Customizable:**
  - Upload your own PDF documents
  - Create any persona (politicians, historical figures, fictional characters)
  - Adjust response style, creativity, and context depth

## Quick Start

1. **Choose your version:**
   - Need to work in Hong Kong/China without VPN? → Use HuggingFace version
   - Have VPN or outside China? → Use Gemini version (faster, higher quality)

2. **Get API key:**
   - Gemini: [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
   - HuggingFace: [https://huggingface.co/settings/tokens](https://huggingface.co/settings/tokens)

3. **Follow setup guide:**
   - See [STUDENT_GUIDE.md](STUDENT_GUIDE.md) for detailed step-by-step instructions

## How It Works

1. Upload PDF documents about your chosen persona
2. System creates searchable vector database (ChromaDB)
3. Students ask questions in natural language
4. RAG retrieves relevant context from PDFs
5. AI generates response in persona's style
6. Student messages analyzed for empathy markers
7. After 10 messages, receive comprehensive empathy report

## Empathy Dimensions Tracked

1. **Sentiment/Warmth** - Positive emotional tone
2. **Open Questions** - Use of exploratory questions (what/how/why)
3. **Emotion Recognition** - Acknowledging feelings explicitly
4. **Perspective-Taking** - "You feel...", "From your view..."
5. **Active Listening** - "Tell me more", "I understand"

## Use Cases

- Communication skills training courses
- Empathy development workshops
- Healthcare/nursing education (bedside manner)
- Customer service training
- Psychology/counseling practice
- Research on empathic communication

## Requirements

- Google account (for Colab)
- Internet connection
- PDF documents (any topic/persona)
- Free API key (Gemini or HuggingFace)

## Technical Stack

- **RAG Framework:** ChromaDB + Sentence Transformers
- **LLMs:** Google Gemini 2.0 Flash / Meta Llama 3.1 8B
- **Interface:** Gradio (async chat UI)
- **Empathy Analysis:** VADER sentiment + pattern matching
- **Platform:** Google Colab (Python 3.10+)

## License

This project is licensed under **CC BY-NC-SA 4.0** (Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International).

**You are free to:**
- Use for education and research
- Modify and adapt the code
- Share with attribution

**Restrictions:**
- No commercial use
- Modifications must use same license
- Must provide attribution

See [LICENSE](LICENSE) for full terms.

## Documentation

- **[STUDENT_GUIDE.md](STUDENT_GUIDE.md)** - Complete setup tutorial
- **[claude.md](claude.md)** - Technical documentation and development history

## Citation

If you use this project in your research, please cite:

```
Let's Talk - RAG Chatbot with Empathy Training
Bertelli, E. (2025)
https://github.com/enricoconductive/let-s-talk-rag-bot
```

## Support

For issues, questions, or contributions, please open an issue on GitHub.

## Acknowledgments

Built for educational purposes. Developed at Lingnan University for communication and empathy training courses.

---

**Status:** ✅ Fully functional | **Last Updated:** November 2025 | **Version:** Session 8 (HuggingFace compatible)
