# Explanatory Guidance for Thesis Writing Depth

## Audience and Baseline Assumptions
- **Target reader:** CS/SE master’s-level audience with working familiarity in ML/IR, but not necessarily specialists in agentic RAG or test-scope analysis. This justifies concise refreshers on common concepts and fuller explanations on niche design choices.
- **Assumed knowledge (no deep re-teaching):** CI/CD basics, regression testing purpose, standard IR primitives (TF-IDF/BM25 intuition, cosine similarity), high-level transformer attention, and the general idea of Knowledge Graphs. Rationale: saves space for the novel parts while keeping readers oriented.
- **Explain once, then use:** Test scope analysis vs. RTS, GraphRAG vs. flat RAG, agentic orchestration (ReAct + tools). Rationale: establish shared vocabulary early so later sections can stay focused on results and design trade-offs.

## Chapter-by-Chapter Depth
- **Introduction (intro.tex):** Stay at motivation/problem framing. Define stakes and gap; avoid textbook IR/ML. Rationale: readers need the “why this matters” without being overloaded before theory.
- **Theory (theory.tex):** Give succinct mechanics only when they justify a design choice. Aim for 2–3 sentences per major concept on why it matters for test scope analysis. Use equations sparingly—only where they defend a choice (e.g., RRF because scores are incomparable). Rationale: keeps theory actionable and tied to your later methods.
- **Method (method.tex):** Be concrete and implementation-focused. Assume awareness of HNSW/BM25; emphasize why you chose them (latency, accuracy, constraints). Present tense for system truths; past tense for what you evaluated. Rationale: readers care how the built system works and why those choices make sense under your constraints.

## What to Trim or Condense
- **LLM architecture subsection:** Remove most vendor/model name lists; keep the essential point (transformers + MoE trend → efficiency and long-context/tool competence). Rationale: names date quickly and distract from the capability you rely on.
- **Embeddings section:** Avoid repeating the “semantic gap” narrative. State it once, then move to implications for your pipeline. Rationale: avoids redundancy and frees space for downstream effects (chunking, tool choice).
- **Tooling brand lists:** Collapse proprietary/open-weight model roll calls into “proprietary vs. open-weight, one example each.” Rationale: reduces noise and keeps focus on decision criteria (privacy, deployment).

## Where to Be Explicit
- **Agentic orchestration:** Keep a crisp description of ReAct + tool calls and one concrete example (structural vs. semantic query). Rationale: this is your novelty; clarity here improves credibility of results.
- **Hybrid vs. single-mode retrieval:** Explain why dynamic selection beats static pipelines for heterogeneous queries (semantic-only, structural-only, hybrid). Rationale: connects theory to the evaluation design.
- **Evaluation setup:** When describing metrics and baselines, emphasize why each baseline matters (e.g., vector-only tests semantic strength; graph-only tests structural upper bound). Rationale: shows that metrics tie back to research questions.
- **HITL/guardrails:** Briefly justify interrupt/approval flow (risk, cost control). Rationale: aligns system design with deployment constraints in industry.

## Rules of Thumb for Exposition
- **Standard curriculum item?** One-sentence refresher + citation. Example: BM25 → brief intuition + cite, no derivation unless used to justify a parameter choice.
- **System-specific or niche?** A full paragraph with an example. Example: TGF schema and how it seeds graph links; tool-selection prompt strategy.
- **Implementation detail affecting results?** Explain the why/trade-off, not just the what. Example: HNSW for sub-second latency to keep ReAct loops responsive.

## Equation and Algorithm Use
- Include formulas only when they defend a design choice (e.g., RRF’s rank-based fusion because scores are not comparable). Otherwise, rely on citations plus verbal intuition. Rationale: maintains readability and focuses math where it earns its keep.

## Tone and Tense
- **Method chapter:** Descriptive-of-completed-artifact: past tense for what you did/evaluated; present tense for system capabilities. Rationale: matches academic convention and clarifies status.

## Example Applications
- **GraphRAG vs. flat RAG paragraph:** Keep the contrast; drop long brand lists. Focus on how structure + semantics improves recall without sacrificing precision.
- **Tool selection strategy:** Present the 4-query typology (identifier/conceptual/structural/complex) once, then reference it. Rationale: readers can map results back to intent classes.

## If Space is Tight
- Prioritize: (1) problem motivation, (2) your agentic hybrid design, (3) evaluation design/results. Defer deep background (e.g., full MoE history) to citations.

## Optional Next Edits
1) Trim vendor/model name lists in theory.tex and merge duplicate “semantic gap” explanations. 2) Add a concise ReAct + tool example (one structural, one hybrid) to anchor the agent description. 3) In method.tex, add one-sentence justifications for key components (HNSW for latency; RRF for incomparable scores; AST splitting for coherence). Rationale: these tweaks increase clarity without adding bulk.
