---
type: Synthesis
title: Code-Context Minification
description: Reducing the repair-context cost of code agents through semantics-preserving lexical transformations, validated against task success and patch quality.
tags: [synthesis, code-agents, context-management, code-minification, token-efficiency, program-repair]
timestamp: 2026-07-14T16:07:15Z
---

# Code-Context Minification

Code-context minification reduces the token footprint of source files supplied to an agent without intentionally changing their runtime behavior. It removes or shortens textual material such as comments, docstrings, blank lines, operator whitespace, imports, and sometimes identifiers. Unlike retrieval, this operates after a code region has already been selected: it tries to make the same repair evidence cheaper to read.

## Operating Pattern

1. Profile prompt tokens by agent stage and by source element; optimize the component that actually dominates repeated cost.
2. Start with transformations that are executable-semantic preserving and easy to validate, such as blank-line, comment, or docstring removal.
3. Treat identifier renaming, import removal, and indentation changes as higher-risk transformations with explicit mappings and ordering constraints.
4. Evaluate each transformation and useful combinations on task success, syntax/patch validity, input and output tokens, retries, and total cost.
5. Promote a configuration only for workloads where its quality loss is within an explicit budget; retain an unminified fallback for difficult or low-confidence cases.

## Practical Use

This pattern is useful for repository repair or code review agents whose repair prompt is dominated by raw source rather than instructions or tool traces. Minify only the model-facing representation; preserve the original files and instrument the handoff back to them. Removing comments or docstrings can save substantial input, but they can also contain intent, conventions, or edge-case rationale that matters for a particular task.

## Limitations

Runtime equivalence is not reasoning equivalence. A model can lose useful semantic cues when identifiers or documentation are removed, and a smaller context may still contain irrelevant code. Transformations can also make generated patches incompatible with original formatting or syntax. Token savings, test success, retries, and exact-patch failures must therefore be measured on the deployed agent and language rather than inferred from source size alone.

## Sources

- [Reducing Token Usage of Software Engineering Agents dossier](/dossiers/reducing-token-usage-software-engineering-agents.md) — evaluates code minification in a state-in-context SWE agent; its full GPT-5-mini run reduces repair input 42% with a 12-point resolution-rate decrease.
