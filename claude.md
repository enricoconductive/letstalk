# RAG Chatbot Project - Educational

Educational RAG (Retrieval-Augmented Generation) chatbot for empathy training and persona-based conversations.

## Project Overview
- **Purpose**: Educational RAG chatbot with customizable personas
- **Platform**: Google Colab (free tier)
- **Technologies**: ChromaDB, HuggingFace Inference API, Gradio, Sentence Transformers, AsyncIO
- **Cost**: 100% free
- **Geographic Support**: Hong Kong compatible (no VPN required)

## Current Status
✅ **FULLY FUNCTIONAL** - All critical issues resolved!

### Current Notebook: RAG_Chatbot_HuggingFace.ipynb (31 cells)
- Complete end-to-end RAG implementation
- Async Gradio chat interface with 30-second timeout
- Conversation memory (last 3 exchanges, configurable)
- Empathy tracking (5 dimensions, 10-message reports)
- Interactive visualizations (Plotly line/bar charts)
- Source citations (toggle-able PDF references)
- Debug mode (conversation memory inspection)
- Meta-Llama-3.1-8B-Instruct (HuggingFace API)
- Hong Kong compatible (no VPN required)

**Last Updated:** November 20, 2025 (Session 10)

---

## Session History

### Sessions 1-2: Initial Development
Created basic RAG implementation with PDF processing, ChromaDB vector storage, and Gemini API integration.

### Session 3: Configuration & API Setup
Added API key configuration, changed model to `gemini-2.0-flash`, configured 7 PDF document paths, added retry logic and error handling.

### Session 4: First Async Attempt
**Problem**: Gradio interface hung indefinitely despite API test working.
**Attempted Solution**: Tried `generate_content_async()` with `asyncio.wait_for()`.
**Result**: Failed - `generate_content_async()` doesn't return proper awaitable.

### Session 5: Threading Fix - Final Solution
**Problem**: `generate_content_async()` returns response object directly, not a coroutine. Synchronous version has no explicit timeout, causing indefinite hangs.

**Root Cause**: Legacy `google-generativeai` SDK's synchronous API had no timeout override, Gradio would block indefinitely, `debug=False` hid errors, large context increased processing time.

**Solution Implemented**: Created synchronous wrapper `generate_response_sync()`, used `asyncio.to_thread()` to run in thread pool, added explicit 30-second timeout with `asyncio.wait_for()`, made Gradio async-compatible, enabled debug mode, reduced context size (2 chunks × 1500 chars), reduced max tokens to 200.

**Result**: Gradio responds in 5-15 seconds or shows clear timeout/error message. No more hanging!

### Session 6: Empathy Tracking + DeepSeek Migration
**Problem**: Hong Kong students cannot access Google Gemini API without VPN.

**Empathy Implementation**: Added VADER sentiment analysis with 5-dimension scoring (sentiment/warmth, open questions, emotion recognition, perspective-taking, active listening). Changed report trigger from 20 → 10 messages. Added CSV export and one-click conversation reset.

**DeepSeek Migration**: Created DeepSeek version for Hong Kong/China (no VPN needed). Changed from `google-generativeai` → `openai` library. Updated to DeepSeek chat completions API. Preserved all empathy tracking. Updated documentation.

**Result**: Two versions available - Gemini (global) and DeepSeek (Hong Kong/China), both with full empathy tracking.

### Session 7: DeepSeek Error + HuggingFace Migration
**Problem**: DeepSeek API returned "Error 402 - Insufficient Balance" despite claims of "5M tokens/month free tier".

**Root Cause Discovery**: DeepSeek does NOT have monthly recurring free tier - only one-time promotional credits (~500k-1M tokens). Once depleted, users must pay.

**HuggingFace Migration**: Needed truly free alternative for Hong Kong students. Changed from `openai` → `huggingface_hub` library. Updated to use `chat_completion()` instead of `text_generation()` for better conversational AI. Preserved all empathy tracking and async/timeout pattern.

**Result**: HuggingFace version with ~300 requests/hour free, works in Hong Kong, truly free.

### Session 8: HuggingFace API Fix + Meta-Llama Migration
**Problem**: HuggingFace API returning 404 errors.

**Root Cause Discovery**:
1. Token had "Read" permissions only - cannot make inference API calls
2. Using `text_generation()` instead of `chat_completion()`
3. **CRITICAL**: Mistral-7B-Instruct-v0.3 gets routed to "novita" provider → novita doesn't support `/chat/completions` endpoint → 404 error!

**HuggingFace Architecture Discovery**: HuggingFace is a router/marketplace, not a direct API like Google Gemini. Different models hosted by different providers with different API endpoint support. `chat_completion()` availability depends on which provider hosts the model.

**Solution**: Generated new token with "Fine-grained" type + "Make calls to Inference Providers" permission. Switched to `chat_completion()` API method. Changed model to **`meta-llama/Meta-Llama-3.1-8B-Instruct`** (compatible provider, high quality, 8B parameters).

**Quality Improvements**: After user feedback ("too long, too generic"), increased context (2→3 chunks, 1500→2000 chars), reduced output length (200→75 tokens), enhanced prompt engineering for stronger grounding in document facts. Later reverted to 200 tokens for better persona expression.

**Result**: API calls work reliably, Meta-Llama-3.1-8B routes to compatible provider, high quality responses, works in Hong Kong.

### Session 9: Conversation Memory Testing Tools
**Discovery**: Conversation memory was already fully implemented in the HuggingFace notebook (Cell 8 configuration, Cell 16 implementation, Cell 19 integration).

**User Request**: Verify functionality works in practice.

**Solution**: Added transparency and testing tools without changing core functionality. Added `DEBUG_MEMORY` toggle in Cell 8, standalone test cell, debug logging in Cell 16, updated STUDENT_GUIDE.md with testing section.

**Result**: Students can now verify memory works, see live message structure, troubleshoot issues, and learn about conversation API architecture. Zero performance impact (debug disabled by default).

### Session 10: Empathy Visualizations + Critical Fixes
**Part 1 - Visualizations**: Added interactive Plotly graphs. Cell 25: Line graph showing overall empathy score progression. Cell 27: Multi-dimension bar chart breaking down 5 dimensions.

**Part 2 - CRITICAL FIX**: Cell 16 (vector database creation) was **COMPLETELY MISSING** from notebook! No embedding model, no ChromaDB collection, no chunks loaded. Bot couldn't find ANY information from PDFs. Created new Cell 16 with complete 5-step database creation process (load embedding model, create embeddings, initialize ChromaDB, create collection, add documents in batches).

**Part 3 - Improved Persona Expression**: Rewrote system prompt to prioritize persona expression over restrictive grounding. Changed "Answer using ONLY" → "Present the facts in your authentic voice and style". Increased max_tokens (75→200), increased context (2000→3000 chars), increased chunks (2→3).

**Part 4 - Duplicate Cell Cleanup**: Cell 17 and Cell 19 both contained identical retrieve/generate functions. Cell 17 had DEBUG_MEMORY feature, Cell 19 didn't. Copied complete code from Cell 17 → Cell 19, deleted Cell 17. Total cells reduced: 32 → 31.

**Result**: Database creation visible, persona personality restored, retrieval working correctly, visualizations merged. Notebook now has 31 cells with complete RAG pipeline.

### Session 11: Progressive Numbering + Export HTML Fix
**Problem**: Confusing step numbering (9, 9, 9A, 9B, 10, 10). Missing export code for Step 14 (HTML graphs). "Run All" gets stuck on reset cell.

**Changes Made**:
1. **Renumbered all steps progressively (1-16)**: Eliminated confusing lettered steps (5B→6, 8B→10, 9A→13, 9B→14).
2. **Restored missing Step 14 code**: Added complete HTML export functionality (3 Plotly graphs with timestamps).
3. **Commented out Step 15**: Reset conversation code now commented out to prevent "Run All" hanging.
4. **Removed duplicate cell**: Deleted duplicate "Step 10" markdown (cell 29).
5. **Updated cross-references**: Changed cell numbers to step numbers in documentation.

**Result**: Clean progressive numbering (Steps 1-16), restored export functionality, "Run All" works smoothly. Total cells: 30 (down from 31).

---

## Key Technical Decisions

### Threading + Async Pattern (Session 5)
**Why**: Gemini SDK's `generate_content_async()` doesn't return a proper awaitable. Synchronous version has no timeout override.

**Solution**: Run synchronous API call in thread pool using `asyncio.to_thread()`, enforce hard timeout with `asyncio.wait_for()`, make Gradio async-compatible, enable debug mode for visible errors.

**Impact**: Eliminated indefinite hanging, 30-second hard timeout, clear error messages.

### HuggingFace Provider Routing (Session 8)
**Why**: Different models hosted by different providers (novita, AWS, together.ai) with different API endpoint support.

**Key Learning**: Must choose models carefully based on provider compatibility. Mistral-7B routes to novita (no chat_completion support). Meta-Llama-3.1-8B routes to compatible provider.

**Recommended Model**: `meta-llama/Meta-Llama-3.1-8B-Instruct` - verified compatible with `chat_completion()` API on HF free tier, high quality for RAG, reliable provider routing, 8B parameters (optimal balance).

### API Requirements
- Token must have "Make calls to Inference Providers" permission
- Use "Fine-grained" token type (NOT "Read" only)
- Use `chat_completion()` method (NOT `text_generation()`)
- Extract response from `response.choices[0].message.content`

### Conversation Memory (Session 9)
Converts Gradio chat history to HuggingFace message format. Sends system message + last N user/assistant pairs + current question. Configurable in Cell 8 (`CONVERSATION_MEMORY = 3`). Debug mode shows exact message structure sent to API.

### Empathy Analysis (Session 6, 10)
5-dimension scoring using VADER sentiment analysis and linguistic pattern matching:
1. Sentiment/Warmth (0-20 pts)
2. Open Questions (0-20 pts)
3. Emotion Recognition (0-20 pts)
4. Perspective-Taking (0-20 pts)
5. Active Listening (0-20 pts)

Total score: 0-100. Report generated after 10 messages. Interactive Plotly visualizations (line graph, bar chart).

---

## Repository Structure

**Current Version**: `RAG_Chatbot_HuggingFace.ipynb` (30 cells, Steps 1-16)

**Critical Steps**:
- Step 1-3: Setup (install, load, mount drive)
- Step 4: Configuration (token, PDFs, persona, memory)
- Step 5: API test
- Step 6: Memory test (optional)
- Step 7-8: PDF processing + vector database ⭐ CRITICAL
- Step 9: Retrieval + generation + memory ⭐ CRITICAL
- Step 10: EmpathyAnalyzer initialization
- Step 11: Gradio chat interface (main cell)
- Step 12-14: Export (CSV, visualizations, HTML)
- Step 15: Reset conversation (commented out)
- Step 16: Troubleshooting

**Archived Versions**:
- `RAG_Chatbot_Trump_Original.ipynb` (Gemini API, basic)
- `RAG_Chatbot_Trump_Student_Basic.ipynb` (Gemini API, empathy)

**Documentation**:
- `README.md` - Project overview + quick start
- `STUDENT_GUIDE.md` - Student tutorial (~280 lines)
- `claude.md` - This file (technical documentation)
- `LICENSE` - CC BY-NC-SA 4.0

---

## Known Limitations

- **Rate Limits**: HuggingFace free tier ~300 requests/hour (manageable with individual student accounts)
- **Timeout**: 30-second timeout per query
- **First Call**: Takes 20-30 seconds (model "wake up"), then 5-10 seconds
- **Internet Required**: Colab + API
- **Google Drive**: Required for PDF access
- **Hong Kong**: Works without VPN (HuggingFace)
- **Mainland China**: Blocked (use VPN or Gemini version)
- **Token Permissions**: Must have "Inference" permissions (NOT just "Read")
- **Provider Routing**: Not all models support all API methods - must verify compatibility

---

## Performance Expectations

### Normal Operation
- API Test (Cell 10): 2-5 seconds (20-30s first time)
- PDF Processing (Cell 12): 1-2 minutes for 7 PDFs
- Vector DB Creation (Cell 16): 1-2 minutes
- Gradio Response: 5-15 seconds per query
- Maximum Wait: 30 seconds (then timeout error)

### Configuration Settings
- **Context**: 3 chunks × 3000 chars max
- **Timeout**: 30 seconds hard limit
- **Max Tokens**: 200 tokens output (~150 words)
- **Temperature**: 0.7 (balanced creativity)
- **Conversation Memory**: 3 exchanges (configurable)

---

## Essential Resources

### API & Tools
- **HuggingFace Tokens**: https://huggingface.co/settings/tokens
- **HuggingFace Docs**: https://huggingface.co/docs/api-inference/
- **HuggingFace Status**: https://status.huggingface.co/
- **Google Colab**: https://colab.research.google.com/

### Technologies
- **ChromaDB**: https://docs.trychroma.com/
- **Gradio**: https://www.gradio.app/docs/
- **Sentence Transformers**: https://www.sbert.net/
- **AsyncIO**: https://docs.python.org/3/library/asyncio.html

---

## Security: .gitignore Configuration

Personal credentials (API keys, PDF paths) stored in `config_personal.py` - excluded from Git via `.gitignore`.

Student notebooks have placeholders. Instructor uses `config_personal.py` locally (never uploaded to GitHub).

**Verification**:
```bash
git check-ignore -v config_personal.py
# Should output: .gitignore:2:config_personal.py
```

---

## Final Status

**Status**: ✅ FULLY FUNCTIONAL + ENHANCED + HONG KONG COMPATIBLE

**Last Updated**: November 24, 2025 (Session 11)

**Current Version**: RAG_Chatbot_HuggingFace.ipynb (30 cells, Steps 1-16)
- Progressive step numbering (1-16, no confusing letters)
- Empathy tracking (5 dimensions, VADER sentiment)
- Conversation memory (configurable, 3 exchanges default)
- Interactive visualizations (Plotly line/bar charts + HTML export)
- Source citations (toggle-able)
- Debug mode (memory inspection)
- HuggingFace API (Meta-Llama-3.1-8B-Instruct)
- Hong Kong compatible (no VPN)
- 100% free (~300 req/hr)
- "Run All" compatible (reset cell commented out)

**Ready for**: Global student deployment, Hong Kong classrooms, empathy training courses, research studies

---

**Built for education. 100% free. Fully customizable.**
