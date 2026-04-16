# 🔬 Phase 3: AI Research Assistant
### Advanced LangChain Concepts — Agents, Tools & Memory

> **Powered by:** Groq API (LLaMA 3 70B) + LangChain ReAct Agent + DuckDuckGo + SQLite

---

## 📁 Project Structure

```
Langchain_roadmap_3/
├── app.py              # Main CLI Research Assistant (run this!)
├── agents.py           # ReAct, Zero-shot & Self-ask Agent demos
├── memory.py           # Buffer, Entity & Vector Memory demos
├── tools.py            # Web search, Wikipedia, Calculator, Datetime tools
├── requirements.txt    # Python dependencies
├── .env.example        # Environment config template
├── research_history.db # SQLite history (auto-created on first run)
└── notebooks/
    ├── 01_agents.ipynb # Learn: What are agents? ReAct pattern
    ├── 02_tools.ipynb  # Learn: Tools, APIs, DB integration
    └── 03_memory.ipynb # Learn: Memory types and implementation
```

---

## Quick Start

### 1. Install dependencies
```bash
cd /home/bakar/Desktop/Langchain_roadmap_3
pip install -r requirements.txt
```

### 2. Set your Groq API key
```bash
cp .env.example .env
# Edit .env and paste your key from https://console.groq.com
```

### 3. Run the Research Assistant
```bash
python app.py
```

---

## App Commands

| Command | Description |
|---|---|
| `/history` | View last 10 Q&A pairs from SQLite |
| `/memory` | Show current conversation memory |
| `/clear` | Clear memory (fresh conversation) |
| `/verbose` | Toggle agent reasoning trace |
| `/quit` | Exit |

---

## Learning Path

| File | Topic | Key Concepts |
|---|---|---|
| `notebooks/01_agents.ipynb` | Agents | ReAct, Zero-shot, Self-ask patterns |
| `notebooks/02_tools.ipynb` | Tools | Web search, APIs, SQL, custom tools |
| `notebooks/03_memory.ipynb` | Memory | Buffer, Entity, Vector memory types |
| `tools.py` | Tools code | 4 production-quality tool implementations |
| `memory.py` | Memory code | 3 memory type demos with runnable examples |
| `agents.py` | Agent code | ReAct agent builder + conceptual demos |
| `app.py` | Full app | Agent + Memory + SQLite integrated |

---

## How It Works

```
User Question
     │
     ▼
ConversationBufferMemory  ──►  Injects past conversation context
     │
     ▼
ReAct Agent (LLaMA 3 70B via Groq)
     │
     ├── Thought: "I need to search for X"
     ├── Action: web_search("X")
     ├── Observation: [search results]
     ├── Thought: "Now I have enough info"
     └── Final Answer: "..."
     │
     ▼
Save to SQLite (research_history.db)
Save to In-Memory Buffer (for context)
```

---

## Tools Available to the Agent

| Tool | Source | Use Case |
|---|---|---|
| `web_search` | DuckDuckGo (free) | Current events, news |
| `wikipedia` | Wikipedia API (free) | Factual/encyclopedic info |
| `calculator` | Custom Python | Math expressions |
| `current_datetime` | Custom Python | Date/time awareness |

---

## Demo: Running individual modules

```bash
# Test tools independently
python tools.py

# Demo all memory types
python memory.py

# Demo agents with tool use
python agents.py
```

---

## Phase 3 Topics Covered

### LangChain Agents
- What are Agents? How do they differ from plain LLM chains?
- Agent Types: ReAct, Zero-shot, Self-ask (conceptual + code)
- Creating agents with `create_react_agent` + `AgentExecutor`
- Tool description engineering (the key to agent performance)

### Integrating External Tools
- DuckDuckGo Search (no API key needed)
- Wikipedia integration
- Custom Python tool creation
- SQLite database integration
- REST API integration (CoinGecko example in notebook)

### LangChain Memory
- `ConversationBufferMemory` — full verbatim history
- `ConversationEntityMemory` — structured entity extraction
- `VectorStoreRetrieverMemory` — semantic long-term memory
- How memory integrates with ReAct agents

---

## Dependencies

```
langchain + langchain-groq + langchain-community  # Core
groq                                               # Groq API client
duckduckgo-search                                  # Free web search
wikipedia                                          # Wikipedia API
chromadb + langchain-chroma                        # Vector store
sentence-transformers                              # Free embeddings
sqlalchemy                                         # SQLite ORM
python-dotenv                                      # .env support
```
