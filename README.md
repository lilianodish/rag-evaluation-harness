# RAG Evaluation Harness

![Python](https://img.shields.io/badge/python-3.9+-blue.svg)
![Status](https://img.shields.io/badge/status-active-green.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Tests](https://img.shields.io/badge/tests-10%20cases-blue.svg)

Small, truthful evaluation harness for Retrieval-Augmented Generation (RAG) systems. Measures what matters for enterprise deployment.

## Purpose

Most teams ship RAG to production without knowing:
- If it hallucinates (makes up information)
- If retrieval actually works (gets relevant docs)
- If answers address the actual question

This harness provides quantified confidence through automated evaluation.

## Current Performance

| Metric | Current | Target | Status |
|--------|---------|--------|--------|
| **Faithfulness** | 0.72 | ≥0.85 | 🔴 Improving |
| **Context Precision** | 0.68 | ≥0.80 | 🟡 In Progress |
| **Answer Relevance** | 0.74 | ≥0.85 | 🟡 In Progress |
| **Latency (p50)** | 820ms | ≤800ms | 🟢 Close |

## Architecture

```mermaid
graph LR
    A[Question] --> B[Retriever]
    B --> C[Context Docs]
    C --> D[LLM Generator]
    D --> E[Answer]
    E --> F[RAGAS Eval]
    F --> G[Metrics]
