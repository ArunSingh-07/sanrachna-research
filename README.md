# Sanrachna: Research & Architecture Documentation

This repository contains the comprehensive research documentation for **Sanrachna**, a privacy-first, offline-capable AI productivity platform.

### [🚀 View the Live Research Site](https://arunsingh-07.github.io/sanrachna-research/)

## Project Overview
Sanrachna is an architecture transition from cloud-dependent AI to edge-based local inference. It focuses on several key research areas:
*   **Privacy-First:** All user data remains local, eliminating the need for cloud-based storage.
*   **Local AI Brain:** Using locally hosted Large Language Models (LLMs) to perform complex reasoning tasks on consumer hardware.
*   **Generative UI Architecture:** Dynamically generating user interfaces from AI-defined JSON schemas.
*   **Offline-First:** Event-sourced synchronization that functions without a persistent internet connection.

## Documentation Contents
This repository is organized as a **VitePress** documentation site:
*   **[Research Proposal](docs/research/proposal.md):** An overview of the abstract, motivation, and research objectives.
*   **[Architecture & Methodology](docs/research/architecture.md):** A technical deep-dive into the core engine, local AI pipeline, and synchronization protocol.

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
*Sanrachna is an open-source research initiative focused on data sovereignty and local-first AI.*
