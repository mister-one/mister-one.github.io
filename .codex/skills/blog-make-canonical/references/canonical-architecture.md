# Canonical Blog Architecture

A blog post should be a layered thought object:

- one part essay
- one part argument
- one part evidence ledger
- one part concept map
- one part agent-readable record

The final structure:

1. Spark
2. Stakes
3. Core insight
4. Reader path
5. Claim spine
6. Concept/object map
7. Evidence ledger
8. Counterarguments
9. Implications
10. Agent card

## 1. Spark

Purpose: make the reader care.

This is not a summary. It is the originating tension.

Bad:

> This post explains why local service data is fragmented.

Better:

> Agents can already search the web, but they still cannot reliably find someone to install seven windows in Bologna.

The spark should contain the puzzle, contradiction, irritation, observed failure, or reason the post exists.

## 2. Stakes

Purpose: explain why the problem matters.

If this remains unsolved, agents will stay good at information tasks but weak at real-world coordination.

Stakes prevent the post from becoming abstract.

## 3. Core insight

Purpose: give the compressed idea.

Example:

> The problem is not missing information. The problem is missing operational context.

This is the L0 equivalent, but written as an insight, not a neutral summary.

## 4. Reader path

Purpose: tell the reader how the post will move.

Example:

> First, I’ll separate search from coordination. Then I’ll show why ordinary business listings fail. Finally, I’ll propose a structure agents can actually use.

This helps humans and agents classify the post.

## 5. Claim spine

Purpose: expose the argument.

Example:

- Claim 1: Search results are not operational records.
- Claim 2: Local services require context fields that websites rarely expose.
- Claim 3: Agent-readable supplier records need freshness, scope, contactability, and confidence.
- Claim 4: The winning structure is not a directory, but a living context layer.

Each claim should later connect to evidence, examples, or reasoning.

## 6. Concept / object map

Purpose: define the world of the post.

For a system post, this is essential.

Objects:

- customer request
- supplier
- installer
- quote
- availability signal
- confidence score

Relationships:

- request matches supplier
- supplier may require installer
- reply updates confidence
- stale signal reduces routing priority

This is where the post becomes agent-friendly.

## 7. Evidence ledger

Purpose: separate belief from proof.

| Claim | Evidence | Confidence | Unknown |
|---|---|---:|---|
| Listings are insufficient for quote routing | Supplier pages rarely expose lead time or installation capacity | 0.80 | Needs larger sample |
| Contactability is a key routing field | No reply makes a supplier operationally weaker | 0.90 | Depends on channel |

This should be collapsible in UI, but present in the canonical post.

## 8. Counterarguments

Purpose: prevent shallow certainty.

Counterargument:

> Maybe agents do not need structured local records. They can just call businesses or scrape websites.

Response:

> That works for one-off tasks, but not for scalable matching, ranking, freshness, or trust.

This is where the post gains intellectual honesty.

## 9. Implications

Purpose: turn insight into consequences.

If this is true:

- directories should become operational context systems
- supplier pages should expose agent-readable fields
- demand forms should create structured requests
- every reply/no-reply becomes a signal

## 10. Agent card

Purpose: make the post machine-readable without forcing humans to parse the prose.

```json
{
  "title": "Why local services are hard for agents",
  "spark": "Agents can search the web but still struggle to coordinate real-world services.",
  "core_insight": "The missing layer is operational context, not raw information.",
  "claims": [
    {
      "claim": "Search results are not operational records.",
      "confidence": 0.85,
      "depends_on": ["definition of operational context"]
    }
  ],
  "objects": ["customer_request", "supplier", "installer", "quote", "signal"],
  "decision_rules": [
    "Treat no-reply as an operational signal.",
    "Separate supplier existence from supplier readiness.",
    "Do not route demand using website text alone."
  ],
  "counterarguments": [
    "Agents may solve this through live calling or scraping."
  ],
  "unknowns": [
    "How much structured context is needed before supplier matching improves materially?"
  ]
}
```

## Final Template

Use this as the canonical template:

```markdown
# Title

## Spark
The concrete irritation, contradiction, or puzzle.

## Stakes
Why this matters now.

## Core insight
The compressed thesis.

## Path
How the post will unfold.

## Argument
### Claim 1
Statement. Reasoning. Example.

### Claim 2
Statement. Reasoning. Example.

### Claim 3
Statement. Reasoning. Example.

## Concept map
Key objects, relationships, definitions, and events.

## Evidence ledger
Claims, evidence, confidence, assumptions, unknowns.

## Counterarguments
The strongest objections and responses.

## Implications
What changes if the post is correct.

## Agent card
Structured metadata: summary, claims, objects, rules, sources, unknowns.
```

## Deeper Rule

The final structure should not be:

> human prose first, machine summary later

It should be:

> structured thought first, human prose as rendering

But the visible post should still feel human:

> spark -> tension -> insight -> argument -> verification -> implication

Final philosophy:

- Write from discovery.
- Structure for retrieval.
- Verify with ledgers.
- Render for humans.
- Expose for agents.
