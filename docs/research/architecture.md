# System Architecture and Methodology

> [!NOTE]
> **This document has been superseded.** For comprehensive documentation, please refer to the [**Technical Research Report**](/research/technical-report).

This document details the technical architecture and methodology for our offline-first AI productivity system.

## 1. System Overview

Sanrachna operates on a hybrid computing model where a desktop computer functions as the primary "host" for AI tasks, while mobile devices function as lightweight clients that sync data for portability.

```text
[ Mobile Client (Kotlin/Compose) ]
       | (Thin Client)
       | SQLite Local Store
       |
       v
[ Synchronization Server (Rust/Axum/Postgres) ]
       ^ (Event-Sourced Sync)
       |
       |
[ Desktop Host (Primary "AI Brain") ]
       |-- Frontend: React, Vite, TailwindCSS (Dynamic UI Renderer)
       |-- IPC Bridge: Tauri
       |-- Core Engine: Rust (Tasks, Notes, Events, Settings)
       |-- Local Data: SQLite
       |-- AI Engine: Ollama (Llama 3, Mistral) / Whisper.cpp
```

## 2. Dynamic UI Generation

One of the central systems in this architecture is the generation pipeline for dynamic user interfaces.

1. **User Input:** "Create a daily habit tracker with water intake and exercise."
2. **Local AI Processing:** The local LLM processes the request through a strictly defined template, outputting a structured JSON schema.
3. **Schema Validation:** The Rust engine validates the output against a pre-defined meta-schema.
4. **Data Persistence:** The schema is stored in the `user_apps` table, and a corresponding data structure is initialized.
5. **UI Rendering:** The React frontend parses the schema and maps data types—such as text, numbers, or booleans—to specific components like text inputs or toggles.

### Security Boundaries
To maintain system integrity, the AI model operates under strict limitations:
* It cannot execute arbitrary code.
* It cannot directly modify the database (all interactions are routed through Rust validation layers).
* It has no file system write access.

## 3. Decentralized Sync Protocol

For the system to remain offline-first, synchronization relies on an event-sourcing model rather than standard CRUD operations.

* All state transitions (task creation, note edits, app generation) are logged as atomic `events` with a timestamp and payload.
* During synchronization, the client transmits its `last_event_id`.
* The server resolves conflicts using Lamport Timestamps or Vector Clocks and returns the delta of missing events.
* Mobile devices submit AI requests as events, which the desktop AI host then processes, syncing the results back to the mobile device.

## 4. Isolated Internet Search

As an optional, opt-in module, the system includes isolated search capabilities using `reqwest` and `scraper` in Rust.
The research goal here is to determine how well an AI can fetch and summarize raw HTML locally, without sending user queries to commercial cloud APIs.
