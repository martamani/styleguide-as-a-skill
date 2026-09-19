# Marta's Voice — a Claude Skill for my own writing

**Goal:** Build a Claude Skill — a plain-text file that teaches the AI my voice — so it can write pottery-shop content that sounds like me.

**The problem:** My last project checked *translations* against a styleguide — two languages, judging text that already existed. That's a hard problem, and it pulled me into Python, loops, and databases. I don't code.

**The reframe:** A styleguide isn't something you check after the fact — it's something you write *with*. As a writer, I follow a styleguide while drafting, and I add to it as I go; I don't finish a piece and then compare it against the rules. A styleguide also isn't personal — it's how a whole team of writers ends up sounding like one voice. This project mirrors how a styleguide is actually used: one language, written *with* the guide, growing rule by rule, meant to keep everyone — human or AI — writing in the same voice.

**Thesis:** In the old project, verifying the styleguide meant checking two entangled things at once, in every sentence: was the language mapped correctly across Spanish and English, and did it still sound like me — a failure could be either, or both, tangled together in the same line. Writing new text with a styleguide removes that entanglement. There's no cross-language mapping to get right or wrong, so the only thing left to verify is voice, on its own.

**Hypothesis:** A clear, example-based Skill will get closer to my real voice than a generic AI draft — and get better every time I correct it.

---

**Part 1 — Build the Skill**
Using two existing skills as models. **Humanizer** showed the format — numbered rules with real before/after examples. **Grill Me** showed the method — interview me one question at a time to surface voice rules I know but haven't written down.
*Tools: Claude, Markdown.*

**Part 2 — Put it to work**
Wire the finished Skill into a real content system: draft, review, approve, and publish, without copy-paste between tools.
*Tools: Notion (review and approval), GitHub (publishing to the site), Make.com (connecting the two).*

---

**The deeper realization:** the first project structured language as data — rules, JSON, validation — because that's how software is usually built. But this problem doesn't need that. AI's real strength is understanding natural language directly. The styleguide just needed to be written the way a person would explain it to another person, clearly, with examples — not encoded as a schema.

**On scale:** at this size — one voice, one small file — there's no bottleneck. If the guide grew to hundreds of rules or several writers, the limit would be the model reliably reading a long document, not a lack of structure — and the fix would still be organizing the language better, not converting it back into data.

