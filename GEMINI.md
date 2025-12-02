# Gemini Context: Agentic RAG & Knowledge Graphs Thesis

This `GEMINI.md` file provides context for the Gemini agent to understand the current project environment, structure, and workflow.

## Project Overview

**Title:** Agentic RAG & Knowledge Graphs for Test Scope Analysis
**Type:** Master's Thesis (Linköping University / Ericsson)
**Author:** Berkay Orhan
**Primary Language:** LaTeX (for thesis), Markdown (for notes/agents)

This project is a Master's thesis investigating the use of **Agentic Retrieval-Augmented Generation (RAG)** and **Knowledge Graphs** to improve **Test Scope Analysis** in large-scale software development (specifically within Ericsson's CI/CD environment).

## Directory Structure

The project is organized as a standard LaTeX document using the `liuthesis` class, integrated with a research/notes structure.

### Key Files & Directories

*   **`student_thesis.tex`**: The **Main Entry Point** for the LaTeX document. It imports all chapters and settings.
*   **`liuthesis.cls`**: The custom LaTeX class file for Linköping University theses.
*   **`Makefile`**: The build script. Use this to compile the PDF.
*   **`intro.tex`, `theory.tex`, `method.tex`, etc.**: Individual chapter files. **Edit these files** to change thesis content.
*   **`rag/`**: Directory containing Markdown notes on RAG components (e.g., embeddings, vector stores).
*   **`.claude/agents/`**: Contains agent definitions (e.g., `thesis-critique-specialist.md`) used for simulating feedback loops during writing.
*   **`figures/`**: Directory for storing images and diagrams included in the thesis.

## Building & Running

The project uses `make` to orchestrate the build process via `latexmk`.

| Command | Description |
| :--- | :--- |
| `make` | Compiles the thesis (`student_thesis.tex`) into a PDF. |
| `make clean` | Removes all auxiliary files (logs, aux, toc, etc.). |
| `make watch` | Watches for file changes and recompiles automatically in the background. |
| `make demos` | Compiles the demo files provided by the template. |

**Build Artifact:** `student_thesis.pdf` (or defined `PDFNAME` in Makefile).

## Development Workflow

1.  **Editing Content:**
    *   Locate the relevant chapter file (e.g., `intro.tex`).
    *   Make edits using standard LaTeX syntax.
    *   Avoid hard-coding layout; rely on `liuthesis.cls` macros.

2.  **Compiling:**
    *   Run `make` to ensure the document compiles without errors.
    *   Check logs if build fails (`latexmk` output).

3.  **Agentic Feedback:**
    *   The user employs AI agents (defined in `.claude/agents`) to critique sections.
    *   When acting as an agent, adopt the persona defined in these files if requested (e.g., "Thesis Critique Specialist").

## Research Context (The "What")

The thesis explores:
*   **Test Scope Analysis:** Identifying relevant tests for code changes.
*   **The Problem:** Keyword search is brittle; standard RAG lacks structural awareness.
*   **The Solution:** An **Agentic GraphRAG** approach that combines vector search (semantics) with knowledge graph traversal (structure), orchestrated by an LLM agent.

## Technical Conventions

*   **Bibliography:** Managed via `biblatex`. Ensure `references.bib` is updated when adding citations.
*   **Graphics:** Store in `figures/`. Use `\input{figures/filename.tikz}` for TikZ or `\includegraphics` for standard images.
*   **Style:** Follows LiU academic standards (defined in `liuthesis.cls`).
