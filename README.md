# Let's Talk - RAG Chatbot with Empathy Training

An educational RAG (Retrieval-Augmented Generation) chatbot that teaches empathic communication skills through interactive conversations. Students practice empathy while chatting with customizable AI personas trained on their own PDF documents.

## 🌏 Hong Kong Compatible

Works without VPN using HuggingFace API (~300 requests/hour, 100% free)

## ✨ Features

**Core Capabilities:**
- Custom persona chatbot trained on your PDF documents
- Semantic search with ChromaDB vector database
- Async interface with 30-second timeout protection
- Meta-Llama-3.1-8B model (8B parameters, high quality)

**Empathy Training:**
- Real-time analysis of 5 empathy dimensions (warmth, questions, emotions, perspective, listening)
- Automated scoring and feedback reports after 10 messages
- Interactive Plotly visualizations showing progress
- CSV export for research and progress tracking

**Conversation Features:**
- Conversation memory (remembers last 3 exchanges by default)
- Source citations (shows which PDFs were used)
- Debug mode for testing and troubleshooting
- Customizable starter questions

## 🚀 Quick Start

1. **Open in Google Colab**: https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/RAG_Chatbot_HuggingFace.ipynb

2. **Get API Token**: https://huggingface.co/settings/tokens
   - Create "Fine-grained" token with "Inference" permissions enabled

3. **Setup** (5 minutes):
   - Upload notebook to Colab
   - Paste token in Cell 8
   - Upload PDFs to Google Drive
   - Click "Runtime → Run All"
   - Copy public link and open in new tab

4. **Start Chatting!**
   - Ask questions empathically
   - Receive feedback after 10 messages
   - View interactive graphs (Cell 25)
   - Export data as CSV (Cell 23)

## 📊 Empathy Dimensions Tracked

1. **Sentiment/Warmth** - Positive emotional tone (VADER sentiment analysis)
2. **Open Questions** - Exploratory questions (what/how/why vs yes/no)
3. **Emotion Recognition** - Acknowledging feelings explicitly (27 emotion words)
4. **Perspective-Taking** - "You feel...", "From your view..." (14 key phrases)
5. **Active Listening** - "Tell me more", "I understand" (13 engagement markers)

**Score:** 0-100 scale | **Report:** After 10 messages | **Export:** CSV + HTML graphs

## 🎓 Use Cases

- Communication skills training courses
- Empathy development workshops
- Healthcare/nursing education (bedside manner)
- Customer service training
- Psychology/counseling practice
- Research on empathic communication

## 📚 Documentation

- **[STUDENT_GUIDE.md](STUDENT_GUIDE.md)** - Step-by-step setup tutorial (5 minutes)
- **[claude.md](claude.md)** - Complete technical documentation & development history

## 🛠️ Technical Stack

- **RAG Framework**: ChromaDB + Sentence Transformers (all-MiniLM-L6-v2)
- **LLM**: Meta-Llama-3.1-8B-Instruct (HuggingFace Inference API)
- **Interface**: Gradio (async chat UI with public link sharing)
- **Empathy Analysis**: VADER sentiment + linguistic pattern matching
- **Visualizations**: Plotly (interactive graphs with HTML export)
- **Platform**: Google Colab (Python 3.10+, no local setup)

## ⚙️ Key Configuration Options

```python
# Cell 8 - Main Settings
CONVERSATION_MEMORY = 3      # Remember last 3 exchanges (0 = disabled, 10 = long memory)
DEBUG_MEMORY = False         # Show message structure in console
SHOW_SOURCES = True          # Display which PDFs were used
TEMPERATURE = 0.7            # 0.0 = focused, 1.0 = creative
CHUNK_SIZE = 1000            # Characters per chunk (500-2000 recommended)
MODEL_NAME = "meta-llama/Meta-Llama-3.1-8B-Instruct"  # Verified compatible
```

## 🆓 100% Free

- **API**: HuggingFace free tier (~300 requests/hour per account)
- **Platform**: Google Colab (no local GPU needed)
- **For Classes**: Each student creates their own free account

## 📋 Requirements

- Google account (for Colab)
- Internet connection
- PDF documents (any topic/persona)
- Free HuggingFace token (2-minute signup)

## 📄 License

**CC BY-NC-SA 4.0** (Creative Commons Attribution-NonCommercial-ShareAlike 4.0)

✅ Use for education and research
✅ Modify and adapt the code
✅ Share with attribution
❌ No commercial use
⚠️ Modifications must use same license

## 📖 Citation

If you use this project in your research:

```
Let's Talk - RAG Chatbot with Empathy Training
Bertelli, E. (2025)
https://github.com/enricoconductive/letstalk
```

## 💬 Support

- **Issues**: Open an issue on GitHub
- **Questions**: See STUDENT_GUIDE.md troubleshooting section
- **HuggingFace Status**: https://status.huggingface.co/

## 🙏 Acknowledgments

Built for educational purposes at Lingnan University for communication and empathy training courses.

---

**Status:** ✅ Fully functional
**Version:** November 2025 (30 cells, conversation memory + visualizations)
**Notebook:** `RAG_Chatbot_HuggingFace.ipynb`
