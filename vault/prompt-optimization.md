---
type: Synthesis
title: Prompt Optimization
description: Automated methods for improving prompts and multi-stage LLM programs, including gradient-based, black-box, model-adaptive, agentic, cost-aware, instruction-generation, and compiler-driven approaches.
tags: [synthesis, prompting, optimization, automated, pro-tegi, bpo, mapo, promptagent, ape, opro, dspy]
timestamp: 2026-07-13T00:11:06Z
---

# Prompt Optimization

A family of techniques for automatically refining input prompts or the prompt-bearing components of an LLM program. Some methods operate only at inference time; others also select models, demonstrations, or fine-tuning data.

## Why It Matters

Crafting effective prompts manually requires extensive expertise and trial-and-error. Automated optimization reduces this burden and can discover prompts that humans might not conceive.

## Methods

### ProTeGi (Prompt Optimization with Textual Gradients)

- Inspired by gradient descent, but adapted for discrete text.
- Generates "textual gradients" — natural language descriptions of flaws in a prompt based on its performance on a small batch of data.
- Applies these gradients to modify the prompt in the reverse semantic direction.
- Uses beam search + bandit selection to explore the prompt space efficiently.
- **Result**: Up to 31% improvement over initial prompts.

### BPO (Black-box Prompt Optimization)

- **Model-agnostic**: Works on any LLM, open-source or API-based, without access to internals.
- **Input-centric**: Refines the user's prompt rather than altering model parameters.
- Uses preference pairs (original vs. optimized prompts) to train a sequence-to-sequence prompt rewriter.
- **Result**: Outperforms RLHF and DPO when used independently or in conjunction.

### MAPO (Model-Adaptive Prompt Optimization)

- **Key insight**: Different LLMs respond differently to the same prompt. Optimization should adapt to the model, not just the task.
- Two-phase process:
  1. **Warm-up**: Generate and evaluate candidate prompts for each specific LLM.
  2. **Joint learning**: Combine supervised fine-tuning with reinforcement learning (PPO + RRMF) to refine prompts for the target model.
- **Result**: Significant improvements in QA, classification, and text generation compared to task-specific optimization.

### PromptAgent

- Frames prompt optimization as a **strategic planning problem**.
- Uses **Monte Carlo Tree Search (MCTS)** to navigate the vast space of expert-level prompts.
- Employs trial-and-error inspired by human problem-solving: iteratively refines based on error feedback, simulates future rewards, and prioritizes high-reward paths.
- **Result**: Consistently outperforms human-designed prompts and other automated methods.

### APE (Automatic Prompt Engineer)

- Treats an instruction as a discrete natural-language program: an LLM proposes candidate instructions from input-output demonstrations, and a target model executes and scores them.
- Uses adaptive, multi-stage filtering: cheaply screen all candidates on small subsets, then spend the full evaluation budget only on survivors. The target can be API-only; proposal and scoring models may differ.
- Can resample semantic variants of high-scoring prompts, though the primary paper found this iterative search usually added only marginal gains beyond direct generation and selection.
- **Result**: On 24 Instruction Induction tasks, APE matched or exceeded human instructions on all 24 (IQM 0.810 versus 0.749); on a curated 21-task BIG-Bench subset, it matched or improved human prompts on 17 tasks. These are historical `text-davinci-002` results, not current-model guarantees.

### OPRO (Optimization by Prompting)

- Uses an LLM as the optimizer: the prompt includes the task, previous candidate solutions or prompts, and their scores, then asks the model to propose stronger candidates.
- Applies to both general optimization problems and prompt optimization for benchmark accuracy.
- **Result**: In the cited survey, OPRO-generated prompts outperform human-designed prompts by up to 8% on GSM8K and up to 50% on challenging Big-Bench tasks.

### DSPy-Style Pipeline Compilation

- Treats a multi-stage LM application—not one prompt string—as the unit of optimization.
- Declares each component's input-output signature, then records traces from program executions that satisfy an end-to-end metric.
- Uses accepted traces as candidate demonstrations for every component, and can search demonstrations, instructions, model choices, or fine-tuning configurations.
- **Use with care**: final-answer success does not prove that intermediate retrieval, reasoning, or tool actions were safe or grounded. Include component-level constraints in the metric and evaluate on held-out cases.

### PO2G (Prompt Optimization with Two Gradients)

- Uses two gradient signals to refine classification prompts more efficiently.
- Treats prompt improvement as an iterative optimization loop rather than a manual writing task.
- **Result**: In the cited review, PO2G reached roughly 89% accuracy in three iterations, while a ProTeGi baseline needed six iterations for similar performance.

### PromptWizard

- Uses an agent-driven loop to mutate both instructions and examples.
- Combines candidate generation with critic-based evaluation.
- **Result**: Reported consistent improvements across 35 evaluation tasks in the cited study.

### Cost-Aware and Multi-Objective Optimization

- Cost-aware methods make API budget part of the optimization problem instead of an afterthought.
- Multi-objective methods optimize several dimensions at once, such as accuracy, efficiency, and interpretability.
- These methods are useful when a prompt is a production artifact with latency, spend, auditability, and reliability constraints.

### RL-based Optimization

- Defines a reward function to evaluate prompt effectiveness.
- Iteratively adjusts prompts based on model output feedback.
- Example: In VQA, the reward function favors prompts that lead to correct answers.

## Comparison

| Method | Access Required | Approach | Best For |
|--------|-----------------|----------|----------|
| ProTeGi | Model outputs + batches | Gradient-like textual descent | When you have evaluation data |
| BPO | API only | Preference-based rewriting | Closed-source models |
| MAPO | Model access | Model-specific adaptation | When you know which model you'll use |
| PromptAgent | Model outputs | Strategic planning / MCTS | Complex, domain-specific tasks |
| APE | Candidate prompts + task feedback | LLM proposal, target-model scoring, successive filtering | Instruction induction and task-specific prompt discovery |
| OPRO | Scored prompt or solution history | LLM-as-optimizer iterative proposal | Prompt search when examples and metrics are available |
| DSPy-style compilation | Traceable program + end-to-end metric | Optimize per-module prompts and demonstrations from accepted execution traces | Multi-stage pipelines with sparse intermediate labels |
| PO2G | Evaluation data | Two-gradient iterative refinement | Classification prompts with iteration cost constraints |
| PromptWizard | Model outputs + critic | Agentic mutation of instructions/examples | Broad task suites where manual prompt design is brittle |
| Multi-objective optimization | Metrics for several objectives | Search over tradeoff frontier | Production prompts with accuracy, cost, efficiency, or interpretability constraints |

## Sources

- [Prompt Engineering Survey dossier](/dossiers/prompt-engineering-survey.md) — Pryzant et al. (2023), Cheng et al. (2024), Chen et al. (2023), Wang et al. (2023)
- [Smarter AI Through Prompt Engineering dossier](/dossiers/smarter-ai-through-prompt-engineering.md) - surveys PO2G, PromptWizard, MAPO, evolutionary search, cost-aware schema matching, and multi-objective prompt optimization.
- [A Systematic Survey of Prompt Engineering in Large Language Models dossier](/dossiers/systematic-survey-prompt-engineering-llms.md) - covers APE and OPRO as automatic instruction-generation and LLM-as-optimizer approaches.
- [DSPy: Compiling Declarative Language Model Calls into Self-Improving Pipelines dossier](/dossiers/dspy-compiling-declarative-language-model-calls.md) - introduces metric-driven compilation for declarative multi-stage LM programs.
- [Large Language Models Are Human-Level Prompt Engineers dossier](/dossiers/automatic-prompt-engineer.md) — defines APE’s proposal/scoring loop, adaptive evaluation, results, and metric-gaming limitations.
