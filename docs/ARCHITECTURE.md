#  locmind-CLI — System Architecture

## Overview

`locMind-CLI` is a modular, local-first command-line AI assistant built around the **MCP protocol**. Its architecture emphasizes **developer productivity**, **privacy-conscious context awareness**, and **semantic memory**, using a combination of:
- Claude (via Anthropic API)
- Local vector storage (e.g., FAISS)
- MCP messaging backbone
- Project context extraction (via static code analysis)
- Web doc fetching layer (modular web retriever engine)
- Local persistence (SQLite) for caching, history, and metadata

---

##  Architecture Type
**Layered Modular Architecture + MCP-Based Messaging Bus**
- Clean separation of concerns
- Modular CLI commands
- Decoupled communication via internal service bus (MCP)

---

##  High-Level Components (Mermaid Diagram)

```mermaid
graph TD
    A[User Terminal (Typer)] --> B[CLI Interface Layer]
    B --> C[Task Dispatcher Layer]
    C --> D[MCP Communication Bus]

    D --> E[Claude Integration (Anthropic API)]
    D --> F[Local Vector Store (FAISS / LlamaIndex)]
    D --> G[Project Analyzer (Code/Docs Parser)]
    D --> H[Web Retrieval Layer (Web Crawler & Doc Extractor)]
    D --> K[Persistence Layer (SQLite)]

    F --> I[Contextual Memory Engine]
    G --> I

    E --> J[Intelligent Response Composer]
    I --> J
    H --> J
    K --> J

    J --> A
```

---

##  Core Data Flow

1. **User triggers a CLI command**\
   Example: `/plan-feature "Add login with OTP"`

2. **Task Dispatcher interprets intent**\
   Routes command through the internal MCP bus

3. **MCP decides handling module**

   - Claude API → AI reply
   - Local vector DB → search project memory
   - Project analyzer → extract metadata or plan tasks
   - Contextual Memory Engine → enrich query and response with file/document embeddings
   - Web Retrieval Layer → scrapes and parses web-based official documentation
   - Persistence Layer (SQLite) → retrieves cached docs, logs, or project metadata

4. **Response returns to CLI**\
   Formatted, human-readable output is displayed

---

## Key Architectural Patterns

| Component                 | Pattern Used                 | Justification                                     |
| ------------------------ | ---------------------------- | ------------------------------------------------- |
| CLI (Typer)              | Presentation Layer           | User interface, command parsing                   |
| Task Dispatcher          | Application Controller       | Routes requests to appropriate handlers           |
| MCP Layer                | Service Bus / Message Router | Decouples command handling & AI/memory logic      |
| Claude Adapter           | External API Adapter         | Handles Claude-specific communication             |
| Vector Store             | Context Cache / Repository   | For fast local semantic search                    |
| Code Analyzer            | Interactor / Use Case Logic  | Extracts insights, plans tasks, formats responses |
| Contextual Memory Engine | Memory-augmented Retrieval   | Combines context from vector DB and code analysis |
| Web Retrieval Layer      | Web Extractor / External Fetch| Retrieves snippets and specs from online docs     |
| Persistence Layer (SQLite) | Local Data Store           | Caches docs, stores session data and metadata     |

---

##  Security & Privacy

- Local-first storage (no vector data sent to cloud)
-  **Secrets.toml** for secure Anthropic API key storage
-  Future support for **offline mode** (Claude stubbing)

---

## Extensibility Points

- Add new commands: `cli/new_command.py`
- Swap Claude: override `ClaudeAdapter` in `integrations`
- Replace FAISS: swap backend in `vector_store.py`
- Add plugins: define MCP hooks in `mcp_router.py`
- Extend memory engine: add multi-project memory or tagging
- Enhance Web Retrieval: support multiple sources, advanced crawling, fallback engines
- Enhance SQLite Persistence: Add audit logs, project snapshots, user annotations

---

## Summary

`locmind-CLI` is not just a CLI utility. It's an intelligent development companion built with:

- Clean modularity
- Powerful AI interaction
- Semantic awareness
- Project context understanding
- Live documentation retrieval (via dedicated Web layer)
- Local caching and session state via SQLite
- Privacy and extensibility at its core

This system design makes it ideal for evolving into a full-fledged local AI development agent.

