---
type: Synthesis
title: Multi-Agent Orchestration
description: Decomposing a complex task into specialized agents that run in a coordinated pipeline, with parallel execution where dependencies allow.
tags: [synthesis, multi-agent, orchestration, pipeline, specialization]
timestamp: 2026-07-11T16:00:00Z
---

# Multi-Agent Orchestration

A design pattern where a complex task is broken into distinct sub-tasks, each handled by a specialized agent. The agents operate in a coordinated pipeline with parallel execution where dependencies allow.

## Core Principles

1. **Specialization over Generalization** — Each agent masters one domain (planning, visual generation, literature search, writing, refinement) rather than a single generalist attempting everything.
2. **Parallel Execution** — Independent sub-tasks run concurrently to minimize wall-clock time.
3. **Decoupled Verification** — High-throughput discovery (e.g., web search with many concurrent workers) is separated from rate-limited verification (e.g., API calls with strict quotas).
4. **Score-Gated Iteration** — Refinement loops accept changes only if objective quality metrics improve, preventing degradation.

## When to Use

- The task has naturally separable sub-domains with minimal cross-cutting concerns.
- Different sub-tasks have different resource constraints (latency, concurrency, API limits).
- Quality can be evaluated by an objective scoring function.
- The output is a structured artifact (document, code, plan) that can be incrementally improved.

## When Not to Use

- The task requires tight feedback loops between sub-domains (e.g., real-time dialogue).
- Sub-tasks are so interdependent that parallel execution creates race conditions.
- Quality is purely subjective with no agreed-upon scoring rubric.

## Variants

| Variant | Description | Example |
|---------|-------------|---------|
| **Sequential Pipeline** | Agents run in strict order; each output feeds the next input | Traditional data engineering pipelines |
| **Parallel Fork-Join** | Independent agents run concurrently; results merged at join point | PaperOrchestra Steps 2 & 3 (plotting + literature review) |
| **Iterative Refinement** | A single agent loops with a critic until quality threshold met | Content Refinement Agent with AgentReview |
| **Hierarchical** | A meta-agent delegates to sub-agents and integrates their outputs | AutoGPT-style task decomposition |

## Sources

- [PaperOrchestra dossier](/dossiers/paperorchestra.md) — 5 specialized agents in a fork-join pipeline; ~60–70 LLM calls; 39.6 min mean latency
