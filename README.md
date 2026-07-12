# Agentic Voice-to-Voice AI Assistant for Product Discovery

GenAI II (UChicago MS-ADS) final project — a voice-to-voice, multi-agent e-commerce assistant.
**Team:** Shane Dunkle · Clark Everson · Victoria L. · Alison Chiu — **Due: Aug 14, 2026**

📊 **[Live task tracker](https://chicagoshane.github.io/genai-project-tracker/)** · 📁 [Team Google Drive](https://drive.google.com/drive/folders/1l-Hr9PKd9C9-CAlo-6vV8qSM0Fs8DIMh?usp=sharing)

## What it does

Spoken query in → Whisper ASR → LangGraph multi-agent pipeline (Router → Planner → MCP tools → Answerer/Critic) → grounded, cited recommendation → TTS voice reply + on-screen comparison table.

- **Private RAG:** Amazon Product Dataset 2020 (Household Cleaning slice), FAISS/Chroma hybrid retrieval
- **MCP server with two tools:** `rag.search` (private catalog) and `web.search` (live price/availability)
- **UI:** Streamlit — mic capture, transcript, agent step log, comparison table, TTS playback

## Repo structure

```
graph/        LangGraph nodes and state (Router, Planner, Answerer/Critic)
mcp_server/   MCP server exposing rag.search + web.search
ui/           Streamlit app
data/         Dataset slice, parquet files, index build scripts (large files gitignored)
prompts/      All system/node prompts, few-shot examples (graded deliverable)
docs/         Project docs, architecture diagram, safety notes + live tracker page
```

## Setup

1. Clone the repo and create a virtual environment (Python 3.11+)
2. `pip install -r requirements.txt` (coming with first code commit)
3. Copy `.env.example` to `.env` and fill in your keys — **never commit `.env`**
4. Build the index: `python data/build_index.py` (coming)
5. Start the MCP server, then `streamlit run ui/app.py` (coming)

## Team ownership

| Area | Owner | Cross-training |
|---|---|---|
| Agentic RAG, eval, prompts/ | Shane | rag.search MCP tool, step-log UI |
| MCP server & infrastructure | Clark | retrieval eval, reconciliation |
| LangGraph orchestration | Victoria | caching/rate limits, TTS |
| Voice (ASR/TTS), UI, demo | Alison | Router node, data wrangling |
