# Styleguide as a skill — a Claude Skill for my own writing

**Goal:** Build a Claude Skill — a plain-text file that teaches the AI my voice — so it can write pottery-shop content that sounds like me.

**The problem:** My last project [Translation styleguide judge](https://github.com/martamani/translation-styleguide-judge) checked *translations* against a styleguide — two languages, judging text that already existed. That's a hard problem, and it pulled me into Python, loops, and databases. I don't code.

**The reframe:** A styleguide isn't something you check after the fact — it's something you write *with*. As a writer, I follow a styleguide while drafting, and I add to it as I go; I don't finish a piece and then compare it against the rules. A styleguide isn't "personal" — it's how a whole team of writers ends up sounding like one voice. This project mirrors how a styleguide is actually used: one language, written *with* the guide, growing rule by rule, meant to keep everyone — human or AI — writing in the same voice.

**Thesis:** In the old project, verifying the styleguide meant checking two entangled things at once, in every sentence: was the language mapped correctly across Spanish and English, and did it still sound like me — a failure could be tangled together in the same line. Writing new text with a styleguide removes that entanglement. There's **no cross-language mapping**, so the only thing left to verify is voice, on its own.

**Hypothesis:** A clear, example-based Skill will get closer to my real voice than a generic AI draft — and get better every time I correct it.

---

**Part 1 — Build the Skill**
Using two existing skills as models. **Humanizer** showed the format — numbered rules with real before/after examples. **Grill Me** showed the method — interview me one question at a time to surface voice rules I know but haven't written down.
*Tools: Claude, Markdown.*

**Part 2 — Put it to work**
Wire the finished Skill into Claude Code, which acts as an agent. When I give it the concept of a pottery text and the images, it calls the skill and writes the draft in my voice. Then it calls a subagent, the **reviewer**. The reviewer starts fresh: it reads the skill and my facts, checks the draft, fixes only what breaks a rule, and lists each change with the rule behind it.
The agent hands the reviewed text over to me for editing. When I edit it, the agent asks me if the edit is a pattern. If it is, it adds it to the skill as a rule, with my edit as the before/after example. If I reject an idea, it adds it to the **Rejected ideas** section, written as an idea with my reason. Once I approve, the agent converts the images to JPEG and adds the text and the images to the GitHub repo, so the post is published.
*Tools: Claude Code, GitHub.*

**Why "Rejected ideas" exists:** early on, the AI suggested something I had already rejected — reworded, but the same idea. It wasn't a memory problem. My rejection lived in the chat, not in the file, so the AI learned to avoid the wording, not the idea. **The skill is the only memory that lasts.** Anything I decide in the chat has to go back into the file, written as an idea, not as a phrase.

**Why a reviewer, not a loop:** we do not need a loop, we need a second reader. A loop is the same pair of eyes on the same text: it misses what it missed the first time, and each pass tends to over-edit. A reviewer that did not write the draft sees what the writer cannot. The first project needed loops; this one needs a second reader.

**What the reviewer caught:** in the first test — a blog post about drawing the steps for a bowl with curved walls — the reviewer made six changes. Five of them were not about voice. They were details that sounded plausible but that I never gave: a pencil, "a little," "straight down." The skill already said not to invent details, and the writer still did, because an invented detail doesn't look wrong from the inside. So the thesis needs one correction: without cross-language mapping, voice is not the only thing left to verify. There is also **fidelity to what I actually said**. The difference is that the two no longer tangle. Each change comes with its own reason, so I can see which one broke.

---

**The deeper realization:** the first project structured language as data — rules, JSON, validation — because that's how software is built. But this problem doesn't need that. AI's real strength is understanding natural language directly. The styleguide just needed to be written the way a person would explain it to another person: the other person is AI, so it needs a lot of examples. A person should be able to understand it, but it has to be *written for AI*, clearly, with examples — not encoded as a schema.

**On scale:** at this size — one voice, one small file — there's no bottleneck. If the guide grew to hundreds of rules or several writers, the limit would be the model reliably reading a long document, not a lack of structure — and the fix would still be organizing the language better, not converting it back into data.
---

## Further reading

**[When Does Reasoning Help in Machine Translation? A Hierarchical Analysis of LRM Reasoning Traces](https://arxiv.org/abs/2609.21247)**
Liu, Luo, Briakou and Cherry (EMNLP 2026). Longer reasoning does not reliably produce better translations; how the reasoning is guided matters more than how long it is. Related to the first project, which judged translations.

**[Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366)**
Shinn et al. (2023). After a failure, the agent writes a short lesson in plain language, stores it, and reads it before trying again. Memory kept as sentences, not as data.

**[AutoGuide: Automated Generation and Selection of Context-Aware Guidelines for Large Language Model Agents](https://arxiv.org/abs/2403.08978)**
Fu et al. (NeurIPS 2024). Turns an agent's past attempts into short, plain-language guidelines that say when they apply. A different task (web navigation), but a similar idea: rules learned from experience, written in natural language.

**[Contrastive Reflection for Iterative Prompt Optimization](https://arxiv.org/abs/2606.30840)**
Koh et al. (2026, LinkedIn). An automated prompt-tuning method that records rejected edits so the system does not repeat them. A different task, and an iterative loop, but close to the idea behind "Rejected ideas."

**[A Survey on the Memory Mechanism of Large Language Model-based Agents](https://dl.acm.org/doi/10.1145/3748302)**
An overview of how AI agents store and use memory, for readers who want the wider field.


