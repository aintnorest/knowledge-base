# Context Engineering Notes

Source: Transcript of *“Mergeable by default: Building the context engine to save time and tokens”* by Peter Werry, Unblocked, from the attached transcript file.[1]

## Core idea

Context engineering is the practice of giving an agent all the context it needs, and none of the context it does not need, in a highly optimized way so the agent can execute tasks in line with organizational practices and expectations.[1]

The talk argues that model intelligence is improving quickly, but context remains the bottleneck. Better coding agents do not remove the need for organizational understanding; without that understanding, agents still produce wrong or incomplete changes, consume excess tokens, and create long review loops.[1]

## Why context matters

Before modern coding agents, humans were effectively the context engine: they supplied tickets, background knowledge, architectural expectations, and corrections during execution.[1]

In real organizations, useful context is not just source code or documentation. It includes historical decisions, rejected approaches, incidents, outages, team norms, expert judgment, and the reasons systems evolved the way they did.[1]

The speaker frames the desired outcome as AI-generated code that feels like it was written by someone who has been on the team for years, not by a capable outsider operating from raw repository access alone.[1]

## Definition of a context engine

A context engine is presented as the reasoning layer that brings together organizational context and delivers only the information needed for the task at hand.[1]

In the talk’s framing, a good context engine should:

- Understand who is asking, what team they are on, and what they are working on.[1]
- Resolve or surface conflicts across sources instead of assuming a single source is always correct.[1]
- Respect permissions and data governance boundaries, especially across tools like Slack, Teams, repositories, and private channels.[1]
- Deliver the right context at the right time for token efficiency and faster task completion.[1]

## Three myths

### 1. Naive RAG over docs is a context engine

The talk explicitly rejects the idea that vector search over documentation alone is enough.[1]

Naive retrieval fails because large organizations contain conflicting information, irrelevant material, and context that lives outside docs and code. Retrieval also needs personalization, or agents may pull technically relevant but organizationally wrong information from the wrong repos, teams, or projects.[1]

### 2. Wiring up MCP servers is sufficient

Connecting many tools gives access, but access does not equal understanding.[1]

An agent may be able to search code, docs, Slack, or tickets through MCP, yet still fail to understand relationships, history, why older implementations exist, or which source should dominate when sources disagree.[1]

### 3. Bigger context windows solve the problem

Large context windows help with “needle in a haystack” retrieval when the target is already known, but they do not solve reasoning across many data sources or selecting the right truth under ambiguity.[1]

The talk also notes that most organizations exceed even very large context sizes, and that simply fitting more data into a prompt does not solve truth selection, conflict handling, or prioritization.[1]

## Satisfaction of search

One of the strongest concepts in the talk is **satisfaction of search**, borrowed from radiology.[1]

The idea is that once an agent finds something that appears to explain the problem, it may stop searching too early. In engineering work, that means an agent may latch onto code or docs that look sufficient while missing the real signal in past incidents, Slack threads, rejected PRs, or decision history.[1]

This is a useful mental model for context engineering because it explains why “just let the agent search more” often produces waste instead of better outcomes.[1]

## The hidden iceberg

The talk uses an iceberg framing: code that compiles is only the visible top of successful work.[1]

Below the surface are the parts agents often miss:

- Original user intent.[1]
- What the team already tried and rejected.[1]
- What failed in the past and why.[1]
- Why certain code exists for compatibility or operational reasons.[1]
- Deleted history and the sequence of decisions that led to the current system.[1]

This is the practical difference between code retrieval and context engineering. The latter must reconstruct decision-making, not just syntax and APIs.[1]

## Main requirements

The speaker gives a high-level set of requirements for a context engine.[1]

### Unified system context

The system should connect planning tools, docs, conversations, code, PRs, and similar engineering artifacts into a coherent context layer.[1]

Simple linking is not enough. The system also needs to distill repeated patterns from historical PR reviews, comments, and team practices into reusable memories that can be loaded later for similar work.[1]

### Conflict resolution

Conflict handling is treated as central, not optional.[1]

The team first tried simple strategies like recency bias and then biasing toward code on the main branch. Both were insufficient, because newer information may still be wrong, and current code may reflect the past rather than the intended future direction of a task.[1]

A better system should rank evidence, reason about likely truth, and explicitly surface unresolved conflicts to the user or agent when it cannot confidently deconflict them.[1]

### Targeted retrieval and personal relevance

Context should be retrieved according to both task relevance and user relevance.[1]

An example from the talk is repo weighting: infer the repos a person works in most from their PR history, then retrieve more deeply from those repos while doing broader, lighter retrieval elsewhere.[1]

This is an important design pattern for agent systems: retrieval should be biased, not uniform.

### Permissions and governance

A context engine must propagate access controls from underlying systems.[1]

The Slack example is especially concrete: private-channel information can influence answers only for users who have access, and those answers should stay private to that user.[1]

The QA section also highlights a key architectural implication: synthesis itself must often be compartmentalized, because unrestricted summarization across permission boundaries can leak sensitive information.[1]

## Architectural patterns

The talk describes a layered architecture rather than a single retrieval primitive.[1]

Key elements include:

- Procedural relationship building, such as knowledge-graph style linkage across entities.[1]
- Vectorized retrieval for semantic access to code and other artifacts.[1]
- Distillation at ingestion time, where repeated patterns and relationships are summarized into memories or higher-value structures.[1]
- Runtime judging, where retrieved evidence is deconflicted again against task-specific criteria.[1]

A useful takeaway here is that context engineering is not “RAG versus graph versus memory.” It is a layered system that combines them, with different mechanisms at ingestion and at runtime.[1]

## Expert modeling and social graphs

A recurring idea is that context engines should model experts, not just documents.[1]

The workshop demo builds a social graph from pull requests and reviews to identify who works with whom, which teams exist, and which contributors are experts in different parts of the codebase.[1]

This expert graph is not just for display. In the talk, it acts as a pivot point for retrieval and memory weighting: the system can “bottle the expert” by distilling a person’s decisions, review patterns, comments, and prior work into reusable context for future tasks in that code area.[1]

This is a strong concept for context engineering more broadly: expert priors can guide both what gets retrieved and how retrieved evidence is weighted.

## Lessons learned

The speaker gives several concrete implementation lessons.[1]

### Access was optimized before understanding

Early designs focused on wiring up many tools plus a knowledge graph, assuming traversal would be enough. That approach did not work, because agents still lacked the semantic and organizational understanding needed to use the data correctly.[1]

### Hidden conflicts caused failures

The team initially tried to silently resolve conflicts with naive heuristics. A better approach is to surface unresolved conflicts and let humans provide corrective feedback when the system cannot infer the right answer confidently.[1]

### Caching answers is a bad shortcut

The talk strongly warns against caching complete answers and reusing them for similar questions.[1]

Code, docs, and rationale change too frequently. Reusing prior answers also causes systems to regress toward stale or polluted context, especially if earlier answers contained errors.[1]

## Human feedback loop

Human feedback is treated as an important correction channel, especially when deconfliction fails.[1]

The system surfaces references to both humans and agents, allowing users to say an answer is wrong and explain why. Over time, repeated feedback helps construct task memory and adjust weighting, with expert feedback carrying more weight than feedback from less-trusted or less-established contributors.[1]

This suggests a practical design principle: feedback should not just grade the final answer; it should become structured memory that improves future retrieval and ranking.

## Planning and review use cases

The talk says the biggest return comes during planning, where better context lets an agent frame the task correctly before implementation starts.[1]

Other high-value uses include:

- Review, where organizational context explains why code should look a certain way, not just whether it compiles or passes checks.[1]
- Ticket enrichment, where context fills in missing implementation detail for new feature work.[1]
- Triage and incident response, where current signals can be linked to prior incidents, code paths, and discussions.[1]
- Engineering support channels, where common questions can be answered automatically using org-specific knowledge.[1]

For an ML/agent-systems audience, this maps well to a broader principle: context engineering is most valuable where task framing and decision rationale dominate raw generation quality.

## Performance claims

The talk includes an example where a larger implementation task took about two and a half hours and 21 million tokens without the context engine, versus about 25 minutes and 10 million tokens with it.[1]

The speaker cautions that some benchmark numbers were rough, but the directional claim is that correct context reduces both doom-loop iterations and total token spend by helping the agent avoid wrong turns early.[1]

This is an important distinction: savings do not come only from smaller prompts. They also come from fewer retries, fewer corrections, and fewer wasted output loops.[1]

## Useful mental models

Several mental models from the talk are worth keeping:

- Humans used to be the context engine; now the goal is to externalize that role for agents.[1]
- The bottleneck is shifting from model intelligence to context quality.[1]
- Access is not understanding.[1]
- Retrieval quality depends on personalization, conflict handling, and governance, not just recall.[1]
- Expert identity can be a retrieval primitive.[1]
- Output-token waste often reflects poor context shaping upstream.[1]

## Practical takeaways

For building context-aware agent systems, the talk points toward a few concrete patterns:[1]

1. Treat context engineering as a system design problem, not a prompt trick.[1]
2. Combine retrieval methods: semantic search, procedural graphing, memory distillation, and runtime judging.[1]
3. Build around decisions and rationale, not just artifacts.[1]
4. Personalize retrieval by user, repo, task, and likely expert ownership.[1]
5. Surface uncertainty and unresolved conflicts instead of burying them behind naive heuristics.[1]
6. Enforce permissions inside both retrieval and synthesis layers.[1]
7. Use feedback as structured memory, especially when expert users correct the system.[1]
8. Optimize for fewer wrong loops, not just fewer input tokens.[1]

## One-sentence summary

The talk’s central argument is that high-performing engineering agents need a context engine that can merge organizational memory, permissions, expert judgment, and task-specific retrieval into a conflict-aware reasoning layer; otherwise, better models mostly generate faster mistakes.[1]

https://www.youtube.com/watch?v=5ID22ACI7IM
Premiered May 3, 2026
