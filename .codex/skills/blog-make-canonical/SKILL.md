---
name: blog-make-canonical
description: Transform a blog article or draft into the canonical layered blog architecture used by this site. Use when Codex is asked to rewrite, restructure, canonicalize, normalize, or make canonical a blog post, Markdown article, rough notes, essay draft, argument draft, or agent-readable blog record using the Spark, Stakes, Core insight, Path, Argument, Concept map, Evidence ledger, Counterarguments, Implications, and Agent card structure.
---

# Blog Make Canonical

## Purpose

Convert a blog draft into a layered thought object: human-readable essay, explicit argument, evidence ledger, concept map, and agent-readable record.

For the complete architecture, read `references/canonical-architecture.md` when transforming content or when the user asks about the structure.

## Workflow

1. Preserve existing front matter exactly unless the user asks to update metadata.
2. Preserve Markdown/Jekyll details that affect publishing, including Liquid tags, image paths, permalinks, dates, and category arrays.
3. Identify the draft's originating tension, stakes, thesis, claims, objects, evidence, objections, implications, and unknowns.
4. Rewrite the article body into this canonical section order:
   - `# Title`
   - `## Spark`
   - `## Stakes`
   - `## Core insight`
   - `## Path`
   - `## Argument`
   - `## Concept map`
   - `## Evidence ledger`
   - `## Counterarguments`
   - `## Implications`
   - `## Agent card`
5. Keep the visible prose human. Do not make the post feel like a database dump.
6. Make uncertainty explicit. If evidence is inferred from the draft rather than proven, mark confidence conservatively.
7. End with a JSON agent card inside a fenced `json` block.

## Section Guidance

- `Spark`: The concrete irritation, contradiction, puzzle, or observed failure. Do not summarize.
- `Stakes`: Why the problem matters now and what breaks if it remains unsolved.
- `Core insight`: One compressed thesis.
- `Path`: A short guide to how the post will unfold.
- `Argument`: A claim spine with 2-5 claims. Each claim should include statement, reasoning, and example when available.
- `Concept map`: Key objects, relationships, definitions, events, and state changes.
- `Evidence ledger`: A Markdown table with `Claim`, `Evidence`, `Confidence`, and `Unknown`.
- `Counterarguments`: Strong objections and responses.
- `Implications`: What changes if the argument is correct.
- `Agent card`: Structured metadata for retrieval and agent use.

## Output Rules

- Do not invent external facts, citations, or sources.
- Do not remove useful raw ideas just because they are rough; place them into the right layer.
- Do not bury the thesis in the agent card. State it in human prose first.
- Prefer concise claims over broad abstractions.
- Preserve the user's voice where possible, but fix grammar and sequencing when needed.
- If a section cannot be completed from the draft, include a short placeholder such as `Unknown from draft.` rather than fabricating.

## Agent Card Shape

Use this shape unless the user requests different fields:

```json
{
  "title": "",
  "spark": "",
  "core_insight": "",
  "claims": [
    {
      "claim": "",
      "confidence": 0.0,
      "depends_on": []
    }
  ],
  "objects": [],
  "decision_rules": [],
  "counterarguments": [],
  "unknowns": []
}
```
