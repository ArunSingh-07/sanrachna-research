# Sanrachna: Research & Architecture Documentation

This repository contains the research documentation for **Sanrachna**, a privacy-first, offline-capable AI productivity platform.

### [🚀 View the Live Research Site](https://arunsingh-07.github.io/sanrachna-research/)

## Project Overview
Sanrachna is an architectural study on moving AI inference from the cloud to local edge devices.

```text
       [ Mobile App ]        [ Desktop App ]
             |                      |
             v                      v
      +-----------------------------------------+
      |      Decentralized Sync Protocol        |
      |   (Event Logs & Lamport Timestamps)     |
      +--------------------+--------------------+
                           |
                           v
      +-----------------------------------------+
      |           LOCAL AI INFERENCE            |
      |      (Llama 3 / Mistral via Ollama)     |
      +-----------------------------------------+
```

The project focuses on several key research areas:
*   **Privacy-First:** User data remains local, removing the need for cloud-based storage.
*   **Local Inference:** Using Large Language Models (LLMs) to perform complex reasoning on standard consumer hardware.
*   **UI Synthesis:** Dynamically generating user interfaces through a schema-driven approach.
*   **Offline-First:** Event-sourced synchronization that works without a constant internet connection.

## Documentation Contents
This repository is organized as a **VitePress** documentation site:
*   **[Technical Research Report](docs/research/technical-report.md):** The primary 10-section research document detailing the system architecture, evaluation, and future work.
*   **[Research Proposal](docs/research/proposal.md):** Abstract, objectives, and research methodology.
*   **[Architecture Details](docs/research/architecture.md):** A technical deep-dive into the core engine, AI pipeline, and sync protocols.

## Repository Structure
```text
.
├── .github/workflows/    # Automated CI/CD for GitHub Pages
├── docs/                 # Documentation source content
│   ├── .vitepress/       # VitePress configuration & theme
│   ├── research/         # Research-heavy documentation files
│   └── index.md          # Documentation landing page
├── package.json          # Site dependencies and scripts
└── README.md             # This file
```

---
*Sanrachna is a research project focused on data privacy and local-first AI.*
