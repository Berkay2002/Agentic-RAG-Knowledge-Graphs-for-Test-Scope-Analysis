# Progress Report & Guidelines

## Current Status
**Date:** Tuesday, November 25, 2025
**Project:** Agentic RAG & Knowledge Graphs for Test Scope Analysis

### What We Have Accomplished
1.  **Refined Introduction (`intro.tex`):**
    *   Established academic tone (fewer dashes) and added inline definitions for key terms.
2.  **Completed Theory Chapter (`theory.tex`):**
    *   **Software Development Context:** Grounded the problem in CI/CD (Humble & Farley), Regression Testing (Rothermel & Harrold), and Test Scope Analysis (Yoo & Harman).
    *   **LLMs:** Covered Transformers, MoE (Gemini 3 Pro), Next-Token Prediction logic, and reasoning capabilities (CoT - Wei et al., Tool Use - Shen et al.).
    *   **Embeddings:** Defined vector representations (citing Mikolov et al.) as the prerequisite for RAG.
    *   **RAG:**
        *   Defined **Software-Specific Pipeline**: Code-aware splitting (AST), header-based splitting.
        *   **GraphRAG:** Explicitly defined the Graph-Vector Hybrid approach (citing **Edge et al., 2024**).
        *   Cited **Lewis et al. (2020)** for the foundational RAG concept.
    *   **Context Engineering:**
        *   Incorporated the **ACE Framework (Zhang et al., 2025)**: Generation, Reflection, Curation.
        *   Addressed **"Context Rot"** and strategies like Compaction/Structured Note-Taking (citing **Anthropic, 2025**).
    *   **AI Agents:**
        *   Defined the **ReAct Framework (Yao et al., 2023)** as the foundational thought-action loop.
        *   Presented the **ACE Cycle** (Generate-Reflect-Curate) as the advanced evolutionary step for self-improving agents.
        *   **Guardrails:** Detailed Deterministic (LangChain), Model-based (Llama Guard, Constitutional AI), and Human-in-the-Loop mechanisms.
3.  **Updated References (`references.bib`):**
    *   **Seminal Papers:** Lewis (RAG), Edge (GraphRAG), Yao (ReAct), Brown (GPT-3/Few-Shot), Kaplan (Scaling Laws), Mikolov (Word2Vec), Wei (Chain-of-Thought).
    *   **Software Engineering Foundation:** Humble (CI/CD), Rothermel (Regression Testing), Beyer (SRE/Observability).
    *   **Modern Frameworks:** Zhang (ACE), Anthropic (Context Engineering), Shen (Tool Use Survey).
    *   **Model Cards:** Gemini 3 Pro, Claude 3.5 Sonnet, DeepSeek-R1.

## Remaining Tasks (To-Do)

### 1. Method Chapter (`method.tex`) - **NEXT PRIORITY**
*   **Methodology:** Define "Design Science Research" (DSR) as the overarching approach.
*   **System Architecture:**
    *   **Data Ingestion:** Connectors for VCS (Git) and Trackers (Jira).
    *   **Knowledge Graph Schema:** Define the nodes (Requirement, Code, Test) and edges.
    *   **Retrieval Agents:** Detail the specific agent types (e.g., "Scoping Agent," "Retrieval Agent").
*   **Evaluation Framework:**
    *   Define metrics: Precision@k, Recall@k, MAP (Mean Average Precision).
    *   Define the "Golden Set" (ground truth) creation process.

### 2. Implementation & Results
*   Fill based on actual coding work.
*   Structure: Experimental Setup -> Quantitative Results -> Qualitative Analysis (Case Study).

### 3. Discussion & Conclusion
*   Reflect on limitations (e.g., latency, cost of graph construction).
*   Future work (e.g., multimodal inputs, autonomous test generation).

---

## Writing Guidelines & Philosophy

### 1. The "Intuitive Bridge"
*   **Goal:** Explain complex, niche topics to a general academic audience.
*   **Strategy:** Use inline definitions and metaphors. Avoid "curse of knowledge."

### 2. The "Red Thread" (Coherence)
*   **Flow:** Problem (Complexity) -> Tool (LLM) -> Fix (RAG) -> Structure (KG) -> Orchestrator (Agent).
*   **Justification:** Every technical choice (e.g., GraphRAG vs. Vector) must be justified by the specific problem (Traceability/Dependencies).

### 3. Tone & Style
*   **Academic:** Precise language, IEEE citations.
*   **Specific:** Distinguish between general AI and "Software Engineering AI" (e.g., Code-aware embedding models).
*   **Citations:** Always cite the "Origin" paper (Lewis, Yao) and the "State of the Art" (Zhang, Edge).

### 4. Thinking Process
*   **Infrastructure Reality:** Acknowledge the "Private Cloud / Open Weights" constraint.
*   **Agent Definition:** An agent is not just a chatbot; it is a system with a *curated playbook* (Memory) and a *self-correction loop* (Reflection).
