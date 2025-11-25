# Progress Report & Guidelines

## Current Status
**Date:** Tuesday, November 25, 2025
**Project:** Agentic RAG & Knowledge Graphs for Test Scope Analysis

### What We Have Accomplished
1.  **Refined Introduction (`intro.tex`):**
    *   Removed excessive m-dashes for a more academic tone.
    *   Added gentle, inline definitions for key terms (LLMs, RAG, Knowledge Graphs, Agentic Architecture) to improve accessibility for non-experts.
2.  **Structured Theory Chapter (`theory.tex`):**
    *   Established a "Problem -> Solution" narrative arc: Software Testing -> LLMs -> RAG -> Agents.
    *   Implemented the **LLM Section** with a focus on:
        *   Foundational Principles (Transformers).
        *   Evolution to **Mixture-of-Experts (MoE)** (explicitly citing DeepSeek-R1, Gemini 3 Pro).
        *   Clarifying the **"Next-Token Prediction"** objective as the root of emergent behavior (with citations to Brown et al., 2020 and Kaplan et al., 2020).
3.  **Updated References (`references.bib`):**
    *   Added Model Cards for **Gemini 3 Pro** and **Claude 3.5 Sonnet** (correcting the earlier "4.5" designation based on available data).
    *   Added seminal papers on Scaling Laws and Few-Shot Learning.
    *   Configured bibliography style to **IEEE** (numeric).

## Remaining Tasks (To-Do)

### 1. Complete Theory Chapter (`theory.tex`)
*   **RAG Section:**
    *   Deep dive into the pipeline: Document Loaders, Text Splitters (chunking), Embedding Models, Vector Stores.
    *   Explain **Context Engineering** and the importance of data quality.
*   **Knowledge Graph Section:**
    *   Explain Nodes/Edges in the context of testing (e.g., Requirement -> Verifies -> Test Case).
    *   Contrast GraphRAG with Vector-only RAG.
*   **Agentic Systems Section:**
    *   Detail the components: Memory (Short/Long term), Tools, Planning, and Guardrails.
    *   Explain Observability and Evaluation within the Agent context.

### 2. Method Chapter (`method.tex`)
*   Draft the Design Science Research methodology.
*   Detail the System Architecture (Data Ingestion, Graph Schema, Retrieval Agents).
*   Define Evaluation Metrics (Precision@k, Recall@k, MAP, nDCG).

### 3. Implementation & Results
*   These sections likely need to be filled based on your actual coding work, but we can draft the structure.

### 4. Review & Refine
*   Ensure the "Red Thread" connects the Introduction's "Motivation" through the Theory's "Solution Components" to the Method's "Implementation."

---

## Writing Guidelines & Philosophy

### 1. The "Intuitive Bridge"
*   **Goal:** Explain complex, niche topics (Agentic RAG) to a general academic audience without "dumbing it down."
*   **Strategy:**
    *   Use **Inline Definitions** for the first mention of heavy terms.
    *   Avoid assuming prior knowledge of specific AI acronyms.
    *   Use metaphors where helpful (e.g., RAG as an "open-book exam").

### 2. The "Red Thread" (Coherence)
*   **Every concept must earn its place.**
    *   *Why mention Next-Token Prediction?* To explain why Hallucinations happen and why RAG is needed.
    *   *Why mention Traceability?* To explain why test scoping is hard and why Knowledge Graphs are the solution.
*   **Flow:** The text should move logically from **Problem** (Testing is slow/hard) -> **Tool** (LLMs are smart but hallucinate) -> **Fix** (RAG gives them facts) -> **Structure** (Knowledge Graphs give them context) -> **Orchestrator** (Agents put it all together).

### 3. Tone & Style
*   **Academic yet Clear:** Avoid conversational filler. Use precise language.
*   **Formatting:** Use commas instead of excessive m-dashes.
*   **Citations:** Use **IEEE** style. Cite seminal papers for foundational claims (e.g., scaling laws) and Model Cards for specific model capabilities (e.g., Gemini 3 Pro).
*   **Accuracy:** Be precise about architectures (e.g., distinguishing MoE from standard Transformers).

### 4. Thinking Process for Future Writing
*   **Anticipate Reader Confusion:** "If I say 'Vector Database,' will they know what a vector is?" -> *Briefly explain embeddings first.*
*   **Avoid Tunnel Vision:** Don't get lost in the implementation details (code libraries) unless it serves the *concept*. Focus on the *architectural role* of the component.
