# Thesis Theory Chapter Expansion Plan (Final Green Light Version)

This document outlines the definitive plan for expanding the "Theoretical Framework" chapter (`theory.tex`). It explicitly addresses the need for empirical motivation and mechanistic detail in the Integration Architecture, ensuring the thesis contribution is both theoretically grounded and practically justified.

**Core Architectural Decisions:**
1.  **Retrieval Strategy:** Dynamic Agentic Orchestration justified by **Information Foraging Theory**.
2.  **Re-ranking:** Single-stage retrieval (no Cross-Encoders).
3.  **Evaluation:** Binary Relevance (Relevant/Not Relevant).

---

## 1. Integration Architecture (New Section 3.4) - **THE LINCHPIN**

### Subsection 3.4.1: Static vs. Dynamic Retrieval Architectures
*   **Goal:** Contrast "Fixed RAG" with "Agentic RAG" and justify the latter.
*   **Theoretical Basis:** Cite **Information Foraging Theory (Pirolli & Card, 1999)**: adaptive strategies (following "information scent") outperform fixed heuristics.
*   **Empirical Motivation (Critical Gap #1):**
    *   Demonstrate query heterogeneity with 3 concrete examples:
        1.  **Semantic-Only:** "Tests related to authentication failures" $\to$ Best served by **Vector Search**. A graph walk might miss relevant tests if they aren't explicitly linked to "Auth" nodes.
        2.  **Structural-Only:** "All tests calling `updateUser()`" $\to$ Best served by **Graph Traversal**. Vector search might miss tests that call wrappers of this function but don't mention the name explicitly.
        3.  **Hybrid:** "Tests for user login with database timeouts" $\to$ Requires **Hybrid Search**.
    *   **Failure Modes of Static Pipelines:**
        *   *Always-Both Strategy:* Inefficient (latency) and noisy (irrelevant graph nodes dilute vector results).
        *   *Choose-One Strategy:* Catastrophic failure on queries requiring the other mode.
    *   **Conclusion:** Dynamic selection is a practical necessity for coverage and precision.

### Subsection 3.4.2: Query Analysis for Strategy Selection
*   **Goal:** Explain the *mechanism* of choice.
*   **Classification Mechanism (Critical Gap #2):**
    *   **Chain-of-Thought (CoT):** The agent performs intent recognition in the "Thought" step of the ReAct loop.
    *   **Prompt Patterns (Emergent Classifier):**
        *   "all tests calling X" $\to$ structural signal $\to$ `graph_traverse()`
        *   "tests related to Y" $\to$ semantic signal $\to$ `vector_search()`
        *   "tests for X with Y" $\to$ hybrid signal $\to$ `hybrid_search()`
    *   **Note:** This is *not* a separate classifier model, but emergent behavior defined by the System Prompt and Tool Descriptions.

### Subsection 3.4.3: Tool-Mediated Integration
*   **Goal:** Define the interface contract.
*   **Tool Signatures (Quality Improvement #3):**
    *   `vector_search(query: str, k: int) -> List[Document]`
    *   `graph_traverse(start_node: str, relation: str, depth: int) -> List[Node]`
    *   `hybrid_search(query: str) -> List[Result]`
*   **Justification:** These signatures hide algorithmic complexity (HNSW layers, BM25 tuning) from the agent, allowing it to reason at a high level of abstraction.

---

## 2. Retrieval-Augmented Generation (RAG) - Section 3

### Embeddings and Semantic Search (Section 3.1)
*   **New Subsection:** **Code vs. Natural Language Embeddings**.
    *   **Content:** Explain "Semantic Gap" failure modes (e.g., `camelCase` tokenization issues). Justify **CodeBERT/Qwen** usage.
    *   **Connection to Integration:** *Because* semantic search has these specific blind spots, the agent must have the autonomy (Section 3.4) to bypass it for structural queries.

### Sparse Retrieval (Keyword Search) (Section 3.2.2)
*   **Expansion:** **BM25 Formula**.
    *   **Content:** Math for term saturation ($k_1$) and length normalization ($b$).
    *   **Connection to Integration:** BM25 provides the `keyword_search()` tool, offering the lexical precision required when the agent detects specific error codes (Section 3.4.2).

### Knowledge Stores (Section 3.3.3)
*   **Expansion:** **Vector Search (HNSW)**.
    *   **Content:** HNSW hierarchical graph for $O(\log N)$ search.
    *   **Connection to Integration:** Enables the `vector_search()` tool to return sub-second results, a hard constraint for the interactive agent loop.

---

## 3. Knowledge Graphs in Software Engineering (Section 4)

### Graph Data Models (Section 4.1)
*   **Expansion:** **LPG Mechanics**.
    *   **Content:** Index-Free Adjacency (constant time traversal).
    *   **Connection to Integration:** Makes `graph_traverse()` computationally feasible for multi-hop reasoning.

---

## 4. AI Agents - Section 5

### Reasoning and Planning (Section 5.1 - ReAct)
*   **Deepening:** **Prompt Engineering for Tool Use**.
    *   **Content:** Detail System Prompt structure and tool definitions.
    *   **Connection to Integration:** Explicitly link to Section 3.4.2—this section details the *mechanism* (prompting) that implements the *strategy* (query analysis).

---

## 5. Large Language Models (LLMs) - Section 2

### Foundational Principles (Section 2.1)
*   **Expansion:** **Attention Mechanism**.
    *   **Content:** Self-Attention mechanics.
    *   **Connection to Integration:** The "engine" allowing the agent to hold conversation history and tool outputs in context.

---

## 6. Evaluation Metrics - Section 6

### Metrics Justification (Section 6.1)
*   **Refinement:** **Binary Relevance**.
    *   **Content:** Justify Recall@k/Precision@k over NDCG.
    *   **Connection to Integration:** Metrics evaluate the *final* output of the orchestration, independent of the path taken.

---

## 6. Evaluation Metrics - Section 6

### Metrics Justification (Section 6.1)
*   **Refinement:** **Binary Relevance**.
    *   **Content:** Justify Recall@k/Precision@k over NDCG.
    *   **Connection to Integration:** Metrics evaluate the *final* output of the orchestration, independent of the path taken.

---

**Implementation Sequence Rationale:**
1.  **Integration Architecture (Section 3.4):** Establishes the core thesis contribution upfront.
2.  **ReAct & Tool Use (Section 5.1):** Provides the mechanism that implements #1.
3.  **Code Embeddings (Section 3.1):** Motivates *why* integration is needed (semantic gaps).
4.  **BM25 & HNSW (Section 3):** Details the algorithmic engines encapsulated by the tools.
5.  **LPG & Attention:** Provides the theoretical bedrock.
*This flow moves from Contribution $\to$ Mechanism $\to$ Motivation $\to$ Implementation $\to$ Foundation.*
