# locmind-CLI

A cost-effective, modular, and powerful CLI AI assistant for developers — powered by MCP protocol and Anthropic API

## Overview

locmind-CLI began as an exploration into the MCP protocol (Message Control Protocol), aiming to build intelligent, context-aware software assistants that prioritize privacy and local-first operation.

This tool brings AI-powered help to your terminal, streamlining coding workflows by allowing you to:

- Load and analyze entire project directories
- Chat naturally with AI about your codebase
- Break down feature requests into actionable tasks
- Fetch official documentation snippets on demand
- Maintain contextual memory using local vector databases
- Generate technical documentation automatically
- Cache session data, project metadata, and documentation locally with SQLite

## Why locmind-CLI?

Software developers juggle many tools—IDEs, docs, task managers, chat apps. locMind-CLI consolidates these into a single CLI experience, powered by cutting-edge AI, local context storage (vector DB + SQLite), and the modular MCP protocol.

## Core Features

| Feature              | Description                                               | Why it Matters                                      |
|---------------------|-----------------------------------------------------------|-----------------------------------------------------|
| /load-project        | Load project directories to extract metadata and main files | Enables claude to understand your codebase context |
| Freeform AI Chat     | Natural language AI chat about your loaded project        | Provides intuitive, conversational AI assistance    |
| /plan-feature        | Break feature requests down into organized tasks          | Organizes your work and saves valuable time         |
| /fetch-docs          | Retrieve snippets from official docs (Flutter, Node, etc.)| Supports quick tech discovery and reminders         |
| Contextual Memory    | Store file embeddings locally for smarter AI responses    | Keeps long-term context for relevant assistance     |
| /generate-docs       | Auto-generate documentation from your code or tasks       | Boosts maintainability and reduces manual effort    |
| Data Persistence   | Caches fetched docs, metadata, and CLI history            | Enables fast retrieval and offline use              |

## Technical Highlights

- MCP Protocol: Manages intelligent message exchanges between CLI and AI backend, enabling modular and scalable communication.
- Local Vector Store: Uses embeddings for semantic search of your project context locally—no cloud needed.
- SQLite Persistence: Lightweight local database for session history, doc caching, and metadata storage.
- Python & Typer: Built with Python and the Typer CLI framework for simplicity and extensibility.
- Anthropic API Integration: Powers advanced natural language understanding and generation.

## Getting Started

### Prerequisites

- Python 3.8 or higher
- MCP-compatible backend server (setup instructions coming soon)
- Anthropic API access credentials (see below)

### How to Get Your Anthropic API Key

**Create an Anthropic Developer Account:**  
Visit Anthropic Console and sign up using your email or third-party login. Anthropic uses a magic link sent via email for authentication.

**Generate an API Key:**  
After logging in, go to the API Keys section in the dashboard. Click Create Key, name it (e.g., "locMind-CLI"), and generate your API key.  
Important: Copy and securely save your API key immediately — it will not be shown again.

**Set Up Billing (if required):**  
Complete any billing setup to enable API usage beyond the free tier.

**Use the API Key in locMind-CLI:**  
Configure locMind-CLI with your Anthropic API key to enable AI-powered features.

## Installation

```bash
git clone https://github.com/Y4NN777/locmind-cli.git
cd locMind-CLI
pip install -r requirements.txt
```

### (Optional) Install SQLite tools:
```bash
sudo apt install sqlite3  # or use your system's package manager
```

## Basic Usage

```bash
locmind-cli /load-project /path/to/your/project
locmind-cli chat
locmind-cli /plan-feature "Add user authentication"
locmind-cli /fetch-docs flutter Navigator
locmind-cli /generate-docs
```

## Roadmap & Contribution

This project is evolving quickly as part of the MCP exploration. Contributions and feedback are highly encouraged!

- Improve MCP protocol implementation
- Add support for more programming languages and frameworks
- Enhance contextual memory management
- Enhance SQLite-based persistence layer
- Build UI integrations (future)

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contact

Questions, suggestions, or want to contribute? Reach out at axeldaboworkplace@gmail.com or open an issue on GitHub.

locMind-CLI empowers developers to harness AI intelligently and privately — all from the command line.
````
