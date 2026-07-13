---
type: Log
title: Knowledge Base Source Registry and Ingest Log
description: Authoritative registry of ingested sources and chronological history of their archive and vault changes.
tags: [log, source-registry, history, ingest]
timestamp: 2026-07-11T16:00:00Z
---

# Knowledge Base Source Registry and Ingest Log

Each `**Ingest**` entry registers exactly one source. Its source key is the
authoritative duplicate-detection record: `doi:…`, another stable publisher ID
such as `ssrn:…`, `arxiv:…` (without a revision suffix), `url:…` (normalized
canonical URL without the scheme), or `sha256:…` when no stronger identifier
exists. Do not add a second ingest entry for a registered key; append subsequent
maintenance as a non-ingest event.

## 2026-07-11
* **Ingest**: `arxiv:2604.05018` — [PaperOrchestra dossier](/dossiers/paperorchestra.md) — canonical: https://arxiv.org/abs/2604.05018v1
* **Vault**: Created [multi-agent-orchestration](/vault/multi-agent-orchestration.md)
* **Vault**: Created [hybrid-discovery-verification](/vault/hybrid-discovery-verification.md)
* **Vault**: Created [score-gated-refinement](/vault/score-gated-refinement.md)
* **Vault**: Created [closed-loop-vlm-visual-generation](/vault/closed-loop-vlm-visual-generation.md)
* **Vault**: Created [benchmark-reverse-engineering](/vault/benchmark-reverse-engineering.md)
* **Vault**: Created [anti-leakage-evaluation](/vault/anti-leakage-evaluation.md)
* **Vault**: Created [sparse-concept-note-prompt](/vault/sparse-concept-note-prompt.md)
* **Vault**: Created [dense-technical-proposal-prompt](/vault/dense-technical-proposal-prompt.md)
* **Vault**: Created [experimental-log-extraction-prompt](/vault/experimental-log-extraction-prompt.md)
* **Vault**: Created [anti-leakage-system-prompt](/vault/anti-leakage-system-prompt.md)
* **Vault**: Created [citation-f1-metric](/vault/citation-f1-metric.md)
* **Vault**: Created [llm-as-judge-with-anti-inflation](/vault/llm-as-judge-with-anti-inflation.md)
* **Setup**: Initialized knowledge base directory structure and README

## 2026-07-11 (second ingest)
* **Ingest**: `arxiv:2310.14735` — [Prompt Engineering Survey dossier](/dossiers/prompt-engineering-survey.md) — canonical: https://arxiv.org/abs/2310.14735v6
* **Vault**: Created [chain-of-thought-prompting](/vault/chain-of-thought-prompting.md)
* **Vault**: Created [self-consistency-decoding](/vault/self-consistency-decoding.md)
* **Vault**: Created [tree-of-thoughts](/vault/tree-of-thoughts.md)
* **Vault**: Created [react-framework](/vault/react-framework.md)
* **Vault**: Created [decomposed-prompting](/vault/decomposed-prompting.md)
* **Vault**: Created [active-prompt](/vault/active-prompt.md)
* **Vault**: Created [prompt-optimization](/vault/prompt-optimization.md)
* **Vault**: Created [retrieval-augmentation](/vault/retrieval-augmentation.md)
* **Vault**: Created [vlm-prompt-learning](/vault/vlm-prompt-learning.md)
* **Vault**: Created [prompt-security-taxonomy](/vault/prompt-security-taxonomy.md)
* **Vault**: Created [llm-evaluation-methods](/vault/llm-evaluation-methods.md)
* **Vault**: Created [ai-agent-evolution](/vault/ai-agent-evolution.md)

## 2026-07-12
* **Ingest**: `arxiv:2510.04618` — [Agentic Context Engineering dossier](/dossiers/agentic-context-engineering.md) — canonical: https://arxiv.org/abs/2510.04618v3
* **Archive**: Moved source PDF to [/archive/agentic-context-engineering.pdf](/archive/agentic-context-engineering.pdf)
* **Vault**: Created [evolving-context-playbooks](/vault/evolving-context-playbooks.md)
* **Vault**: Created [context-collapse](/vault/context-collapse.md)
* **Vault**: Created [incremental-delta-context-updates](/vault/incremental-delta-context-updates.md)
* **Vault**: Created [feedback-grounded-context-adaptation](/vault/feedback-grounded-context-adaptation.md)

## 2026-07-12 (second ingest)
* **Ingest**: `ssrn:5165270` — [Prompt Engineering is Complicated and Contingent dossier](/dossiers/prompt-engineering-complicated-contingent.md) — canonical: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5165270
* **Archive**: Moved source PDF to [/archive/prompt-engineering-complicated-contingent.pdf](/archive/prompt-engineering-complicated-contingent.pdf)
* **Vault**: Created [prompt-contingency](/vault/prompt-contingency.md)
* **Vault**: Updated [llm-evaluation-methods](/vault/llm-evaluation-methods.md)

## 2026-07-12 (third ingest)
* **Ingest**: `arxiv:2607.08716` — [Remember When It Matters dossier](/dossiers/proactive-memory-agent.md) — canonical: https://arxiv.org/abs/2607.08716v1
* **Archive**: Moved source PDF to [/archive/proactive-memory-agent.pdf](/archive/proactive-memory-agent.pdf)
* **Vault**: Created [behavioral-state-decay](/vault/behavioral-state-decay.md)
* **Vault**: Created [proactive-memory-intervention](/vault/proactive-memory-intervention.md)
* **Vault**: Created [structured-execution-memory](/vault/structured-execution-memory.md)

## 2026-07-12 (fourth ingest)
* **Ingest**: `url:youtube.com/watch?v=5ID22ACI7IM` — [Mergeable by Default dossier](/dossiers/context-engineering-talk.md) — canonical: https://www.youtube.com/watch?v=5ID22ACI7IM
* **Archive**: Moved source notes to [/archive/context-engineering-talk.md](/archive/context-engineering-talk.md)
* **Vault**: Created [conflict-aware-context-retrieval](/vault/conflict-aware-context-retrieval.md)
* **Vault**: Created [expert-weighted-retrieval](/vault/expert-weighted-retrieval.md)
* **Vault**: Created [permission-scoped-synthesis](/vault/permission-scoped-synthesis.md)

## 2026-07-12 (fifth ingest)
* **Ingest**: `arxiv:2602.00337` — [Smarter AI Through Prompt Engineering dossier](/dossiers/smarter-ai-through-prompt-engineering.md) — canonical: https://arxiv.org/abs/2602.00337
* **Archive**: Moved source PDF to [/archive/smarter-ai-through-prompt-engineering.pdf](/archive/smarter-ai-through-prompt-engineering.pdf)
* **Vault**: Updated [prompt-optimization](/vault/prompt-optimization.md)

## 2026-07-13 (third ingest)
* **Ingest**: `arxiv:2407.12994` — [A Survey of Prompt Engineering Methods in Large Language Models for Different NLP Tasks dossier](/dossiers/survey-prompt-engineering-methods-nlp-tasks.md) — canonical: https://arxiv.org/abs/2407.12994v2
* **Archive**: Moved source PDF to [/archive/survey-prompt-engineering-methods-nlp-tasks.pdf](/archive/survey-prompt-engineering-methods-nlp-tasks.pdf)
* **Vault**: Updated [application-centric-prompt-taxonomy](/vault/application-centric-prompt-taxonomy.md)

## 2026-07-13 (third ingest)
* **Ingest**: `arxiv:2406.06608` — [The Prompt Report dossier](/dossiers/prompt-report.md) — canonical: https://arxiv.org/abs/2406.06608v6
* **Archive**: Moved source PDF to [/archive/prompt-report.pdf](/archive/prompt-report.pdf)
* **Vault**: Created [answer-engineering](/vault/answer-engineering.md)
* **Vault**: Updated [application-centric-prompt-taxonomy](/vault/application-centric-prompt-taxonomy.md)
* **Vault**: Updated [prompt-contingency](/vault/prompt-contingency.md)
* **Vault**: Updated [llm-evaluation-methods](/vault/llm-evaluation-methods.md)

## 2026-07-12 (sixth ingest)
* **Ingest**: `arxiv:2410.12843` — [Exploring Prompt Engineering dossier](/dossiers/exploring-prompt-engineering-swot.md) — canonical: https://arxiv.org/abs/2410.12843v1
* **Archive**: Moved source PDF to [/archive/exploring-prompt-engineering-swot.pdf](/archive/exploring-prompt-engineering-swot.pdf)
* **Vault**: Created [prompt-technique-swot-analysis](/vault/prompt-technique-swot-analysis.md)
* **Vault**: Updated [llm-evaluation-methods](/vault/llm-evaluation-methods.md)

## 2026-07-12 (sixth ingest)
* **Ingest**: `arxiv:2402.07927` — [A Systematic Survey of Prompt Engineering in Large Language Models dossier](/dossiers/systematic-survey-prompt-engineering-llms.md) — canonical: https://arxiv.org/abs/2402.07927v2
* **Archive**: Moved source PDF to [/archive/systematic-survey-prompt-engineering-llms.pdf](/archive/systematic-survey-prompt-engineering-llms.pdf)
* **Vault**: Created [application-centric-prompt-taxonomy](/vault/application-centric-prompt-taxonomy.md)
* **Vault**: Updated [prompt-optimization](/vault/prompt-optimization.md)
* **Vault**: Updated [retrieval-augmentation](/vault/retrieval-augmentation.md)

## 2026-07-12 (eighth ingest)
* **Ingest**: `arxiv:2005.14165` — [Language Models are Few-Shot Learners dossier](/dossiers/language-models-are-few-shot-learners.md) — canonical: https://arxiv.org/abs/2005.14165v4
* **Archive**: Moved source PDF to [/archive/language-models-are-few-shot-learners.pdf](/archive/language-models-are-few-shot-learners.pdf)
* **Vault**: Created [in-context-learning](/vault/in-context-learning.md)
* **Vault**: Updated [anti-leakage-evaluation](/vault/anti-leakage-evaluation.md)

## 2026-07-12 (ninth ingest)
* **Ingest**: `arxiv:2201.11903` — [Chain-of-Thought Prompting Elicits Reasoning in Large Language Models dossier](/dossiers/chain-of-thought-prompting-elicits-reasoning.md) — canonical: https://arxiv.org/abs/2201.11903v6
* **Archive**: Moved source PDF to [/archive/chain-of-thought-prompting-elicits-reasoning.pdf](/archive/chain-of-thought-prompting-elicits-reasoning.pdf)
* **Vault**: Updated [chain-of-thought-prompting](/vault/chain-of-thought-prompting.md)

## 2026-07-12 (tenth ingest)
* **Ingest**: `arxiv:2205.11916` — [Large Language Models are Zero-Shot Reasoners dossier](/dossiers/large-language-models-are-zero-shot-reasoners.md) — canonical: https://arxiv.org/abs/2205.11916v4
* **Archive**: Moved source PDF to [/archive/large-language-models-are-zero-shot-reasoners.pdf](/archive/large-language-models-are-zero-shot-reasoners.pdf)
* **Vault**: Updated [chain-of-thought-prompting](/vault/chain-of-thought-prompting.md)

## 2026-07-12 (eleventh ingest)
* **Ingest**: `arxiv:2305.10601` — [Tree of Thoughts: Deliberate Problem Solving with Large Language Models dossier](/dossiers/tree-of-thoughts-deliberate-problem-solving.md) — canonical: https://arxiv.org/abs/2305.10601v2
* **Archive**: Moved source PDF to [/archive/tree-of-thoughts-deliberate-problem-solving.pdf](/archive/tree-of-thoughts-deliberate-problem-solving.pdf)
* **Vault**: Updated [tree-of-thoughts](/vault/tree-of-thoughts.md)

## 2026-07-12 (eleventh ingest)
* **Ingest**: `arxiv:2203.11171` — [Self-Consistency Improves Chain of Thought Reasoning in Language Models dossier](/dossiers/self-consistency-improves-chain-of-thought-reasoning.md) — canonical: https://arxiv.org/abs/2203.11171v4
* **Archive**: Moved source PDF to [/archive/self-consistency-improves-chain-of-thought-reasoning.pdf](/archive/self-consistency-improves-chain-of-thought-reasoning.pdf)
* **Vault**: Updated [self-consistency-decoding](/vault/self-consistency-decoding.md)

## 2026-07-12 (twelfth ingest)
* **Ingest**: `arxiv:2210.03629` — [ReAct: Synergizing Reasoning and Acting in Language Models dossier](/dossiers/react-synergizing-reasoning-and-acting.md) — canonical: https://arxiv.org/abs/2210.03629v3
* **Archive**: Moved source PDF to [/archive/react-synergizing-reasoning-and-acting.pdf](/archive/react-synergizing-reasoning-and-acting.pdf)
* **Vault**: Updated [react-framework](/vault/react-framework.md)

## 2026-07-13
* **Ingest**: `arxiv:2205.10625` — [Least-to-Most Prompting Enables Complex Reasoning in Large Language Models dossier](/dossiers/least-to-most-prompting.md) — canonical: https://arxiv.org/abs/2205.10625v3
* **Archive**: Moved source PDF to [/archive/least-to-most-prompting.pdf](/archive/least-to-most-prompting.pdf)
* **Vault**: Created [least-to-most-prompting](/vault/least-to-most-prompting.md)

## 2026-07-13 (second ingest)
* **Ingest**: `arxiv:2310.03714` — [DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines dossier](/dossiers/dspy-compiling-declarative-language-model-calls.md) — canonical: https://arxiv.org/abs/2310.03714v1
* **Archive**: Moved source PDF to [/archive/dspy-compiling-declarative-language-model-calls.pdf](/archive/dspy-compiling-declarative-language-model-calls.pdf)
* **Vault**: Created [declarative-lm-pipeline-compilation](/vault/declarative-lm-pipeline-compilation.md)
* **Vault**: Created [metric-gated-trace-bootstrapping](/vault/metric-gated-trace-bootstrapping.md)
* **Vault**: Updated [prompt-optimization](/vault/prompt-optimization.md)

## 2026-07-13 (second ingest)
* **Ingest**: `arxiv:2211.01910` — [Large Language Models Are Human-Level Prompt Engineers dossier](/dossiers/automatic-prompt-engineer.md) — canonical: https://arxiv.org/abs/2211.01910v2
* **Archive**: Moved source PDF to [/archive/automatic-prompt-engineer.pdf](/archive/automatic-prompt-engineer.pdf)
* **Vault**: Updated [prompt-optimization](/vault/prompt-optimization.md)

## 2026-07-13 (SSRN 5285532)
* **Ingest**: `ssrn:5285532` — [Prompting Science Report 2 dossier](/dossiers/decreasing-value-chain-of-thought-prompting.md) — canonical: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5285532
* **Archive**: Moved source PDF to [/archive/decreasing-value-chain-of-thought-prompting.pdf](/archive/decreasing-value-chain-of-thought-prompting.pdf)
* **Vault**: Updated [chain-of-thought-prompting](/vault/chain-of-thought-prompting.md)
* **Vault**: Updated [llm-evaluation-methods](/vault/llm-evaluation-methods.md)

## 2026-07-13 (GitHub Blog)
* **Ingest**: `url:github.blog/ai-and-ml/generative-ai/validating-agentic-behavior-when-correct-isnt-deterministic/` — [Validating Agentic Behavior When Correct Isn't Deterministic dossier](/dossiers/validating-agentic-behavior.md) — canonical: https://github.blog/ai-and-ml/generative-ai/validating-agentic-behavior-when-correct-isnt-deterministic/
* **Vault**: Created [dominator-based-agent-validation](/vault/dominator-based-agent-validation.md)

## 2026-07-13 (web ingest)
* **Ingest**: `url:memory.cobanov.dev/` — [How AI Agent Memory Works dossier](/dossiers/how-ai-agent-memory-works.md) — canonical: https://memory.cobanov.dev/
* **Vault**: Created [memory-lifecycle-governance](/vault/memory-lifecycle-governance.md)
* **Vault**: Created [hybrid-memory-retrieval-pipeline](/vault/hybrid-memory-retrieval-pipeline.md)

## 2026-07-13 (Cursor Blog)
* **Ingest**: `url:cursor.com/blog/continually-improving-agent-harness` — [Continually Improving Our Agent Harness dossier](/dossiers/continually-improving-agent-harness.md) — canonical: https://cursor.com/blog/continually-improving-agent-harness
* **Vault**: Created [outcome-grounded-agent-evaluation](/vault/outcome-grounded-agent-evaluation.md)
* **Vault**: Created [model-aware-harness-design](/vault/model-aware-harness-design.md)

## 2026-07-13 (Turing Post)
* **Ingest**: `url:www.turingpost.com/p/guest-post-ai-inference-is-breaking-unit-economics` — [Guest post: AI Inference Is Breaking Unit Economics dossier](/dossiers/ai-inference-unit-economics.md) — canonical: https://www.turingpost.com/p/guest-post-ai-inference-is-breaking-unit-economics
* **Vault**: Created [cost-aware-inference-control](/vault/cost-aware-inference-control.md)

## 2026-07-13 (Perplexity Research)
* **Ingest**: `url:research.perplexity.ai/articles/designing-refining-and-maintaining-agent-skills-at-perplexity` — [Designing, Refining, and Maintaining Agent Skills at Perplexity dossier](/dossiers/designing-refining-maintaining-agent-skills-perplexity.md) — canonical: https://research.perplexity.ai/articles/designing-refining-and-maintaining-agent-skills-at-perplexity
* **Vault**: Created [evaluated-skill-routing](/vault/evaluated-skill-routing.md)
* **Vault**: Created [progressive-skill-disclosure](/vault/progressive-skill-disclosure.md)

## 2026-07-13 (INTERNALS.md)
* **Ingest**: `url:internals.laxmena.com/p/what-youre-actually-writing-when` — [What You're Actually Writing When You Write a SKILL.md dossier](/dossiers/skill-md-loader-specification.md) — canonical: https://internals.laxmena.com/p/what-youre-actually-writing-when
* **Vault**: Created [progressive-skill-disclosure](/vault/progressive-skill-disclosure.md)

## 2026-07-13 (Red Hat Developer)
* **Ingest**: `url:developers.redhat.com/articles/2025/09/30/vllm-or-llamacpp-choosing-right-llm-inference-engine-your-use-case` — [vLLM or llama.cpp: Choosing the right LLM inference engine for your use case dossier](/dossiers/vllm-or-llamacpp-inference-engine-selection.md) — canonical: https://developers.redhat.com/articles/2025/09/30/vllm-or-llamacpp-choosing-right-llm-inference-engine-your-use-case
* **Vault**: Created [workload-aligned-inference-engine-selection](/vault/workload-aligned-inference-engine-selection.md)

## 2026-07-13 (AXI)
* **Ingest**: `url:axi.md/` — [AXI: Agent eXperience Interface dossier](/dossiers/axi-agent-experience-interface.md) — canonical: https://axi.md/
* **Vault**: Created [agent-ergonomic-interface-design](/vault/agent-ergonomic-interface-design.md)
* **Vault**: Created [action-observation-fusion](/vault/action-observation-fusion.md)
* **Vault**: Created [bounded-tool-observations](/vault/bounded-tool-observations.md)

## 2026-07-13 (Medium)
* **Ingest**: `url:robert-mcdermott.medium.com/performance-vs-practicality-a-comparison-of-vllm-and-ollama-104acad250fd` — [Performance vs Practicality: A Comparison of vLLM and Ollama dossier](/dossiers/vllm-ollama-performance-practicality.md) — canonical: https://robert-mcdermott.medium.com/performance-vs-practicality-a-comparison-of-vllm-and-ollama-104acad250fd
* **Vault**: Updated [workload-aligned-inference-engine-selection](/vault/workload-aligned-inference-engine-selection.md)

## 2026-07-13 (Prompt Coach)
* **Ingest**: `arxiv:2607.06074` — [Prompt Coach dossier](/dossiers/prompt-coach-agentic-tutor.md) — canonical: https://arxiv.org/abs/2607.06074v1
* **Archive**: Moved source PDF to [/archive/prompt-coach-agentic-tutor.pdf](/archive/prompt-coach-agentic-tutor.pdf)
* **Vault**: Created [in-flow-socratic-prompt-coaching](/vault/in-flow-socratic-prompt-coaching.md)

## 2026-07-13 (MASTE)
* **Ingest**: `arxiv:2607.08080` — `MASTE: A Multi-Agent Pipeline for Zero-Shot Aspect Sentiment Triplet Extraction dossier` at `/dossiers/maste-zero-shot-aspect-sentiment-triplet-extraction.md` — canonical: https://arxiv.org/abs/2607.08080v1
* **Archive**: Moved source PDF to [/archive/maste-zero-shot-aspect-sentiment-triplet-extraction.pdf](/archive/maste-zero-shot-aspect-sentiment-triplet-extraction.pdf)
* **Vault**: Created [grounded-structured-extraction](/vault/grounded-structured-extraction.md)
* **Vault**: Updated [multi-agent-orchestration](/vault/multi-agent-orchestration.md)

## 2026-07-13 (Memory Compaction Survey)
* **Ingest**: `arxiv:2607.08032` — What to Keep, What to Forget: A Rate–Distortion View of Memory Compaction in LLMs and Agents dossier at `/dossiers/rate-distortion-memory-compaction.md` — canonical: https://arxiv.org/abs/2607.08032v1
* **Archive**: Moved source PDF to [/archive/rate-distortion-memory-compaction.pdf](/archive/rate-distortion-memory-compaction.pdf)
* **Vault**: Created [rate-distortion-memory-compaction](/vault/rate-distortion-memory-compaction.md), [reversible-query-conditioned-compaction](/vault/reversible-query-conditioned-compaction.md), [repeated-compaction-evaluation](/vault/repeated-compaction-evaluation.md)
