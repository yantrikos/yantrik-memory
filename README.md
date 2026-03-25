# Yantrik Memory

Persistent cognitive memory for AI agents, powered by [YantrikDB](https://github.com/yantrikos/yantrikdb).

## Install

```bash
pip install yantrik-memory
yantrik-memory init
```

## What it does

Gives your AI agent persistent memory that survives across conversations:

- **Remember & Recall** — Store and retrieve memories with hybrid search (semantic + graph + temporal + keyword)
- **Personality Traits** — 9 evolving traits that adapt to each user
- **Bond Evolution** — Relationships grow from stranger to bonded over time
- **Knowledge Graph** — Entity relationships for context-aware retrieval
- **Context Assembly** — One call to get everything an LLM needs

## Quick Start

```python
from yantrik_memory import YantrikMemory

mem = YantrikMemory()

# Single entry point for agents
context = mem.process_turn(
    agent_id="assistant",
    user_id="user123",
    message="I prefer dark mode and concise answers",
)

# Returns: memories, traits, bond state, personality guidance, mood, intent
print(context["traits"])       # {'conciseness': 0.55, 'humor': 0.5, ...}
print(context["bond"]["level"])  # 'acquaintance'
```

## OpenClaw / ClawDBot Plugin

Yantrik Memory is a ClawHub plugin. Install via:

```bash
openclaw plugins install yantrik-memory
```

Or add to your skills directory:

```bash
cd ~/.openclaw/skills
git clone https://github.com/yantrikos/yantrik-memory.git
pip install -e yantrik-memory
```

## Powered by YantrikDB

5 unified indexes on a single SQLite file:

| Index | Purpose |
|-------|---------|
| Vector (HNSW) | Semantic similarity |
| Graph | Entity relationships |
| Temporal | Time-aware retrieval |
| Decay Heap | Memory lifecycle |
| KV | Fast lookups |

<60ms latency. Zero config. No external databases.

## License

MIT
