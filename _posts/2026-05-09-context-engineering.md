---
layout: post
title: "How I Think About Context Engineering"
subtitle: "The invisible layer that determines whether your AI actually works"
date: 2026-05-09
tags: [ai-engineering, prompt-engineering, context-engineering, llms]
---

Most conversations about AI quality focus on the model. Better model, better outputs. That framing misses where the real leverage is.

The model is fixed. The context is yours.

Context engineering is the practice of deliberately designing everything the model receives: the system prompt, the memory strategy, the tool descriptions, the conversation structure, the retrieval layer, the skill routing logic. Get this right and a smaller model outperforms a larger one. Get it wrong and no model size saves you.

I've been building agentic systems long enough to have a strong opinion: **the context layer is the product**. The model is infrastructure.

### What context engineering actually covers

- **System prompt architecture** — not just "write a good system prompt" but designing the full instruction hierarchy, priority ordering, and failure modes
- **Memory strategy** — what persists, what gets summarized, what gets dropped, and when each decision fires
- **Skill/tool design** — how you describe tools shapes how (and whether) the model uses them; description quality matters as much as implementation quality
- **Retrieval integration** — chunking strategy, embedding choices, reranking, and when to skip RAG entirely
- **Conversation compaction** — keeping long sessions coherent without blowing context limits

### Why it's an engineering discipline, not a writing one

The mistake is treating prompt engineering as copywriting. It's not. It's systems design with probabilistic outputs. You need to reason about failure modes, test systematically, version your prompts like code, and understand how small wording changes cascade through a multi-agent pipeline.

My current work: building a portable `.agent/` folder ([agentic-stack](https://github.com/AgenticJennifer/agentic-stack)) that carries memory, skills, and protocols across eight different AI harnesses. The context layer travels with you. That's the point.

If you're building AI products and the outputs aren't reliable enough — before you swap the model, look at the context.
