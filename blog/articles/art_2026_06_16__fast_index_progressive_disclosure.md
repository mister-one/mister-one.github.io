---
layout: default
title: Fast Index and Progressive Disclosure
permalink: /blog/art_2026_06_16__fast_index_progressive_disclosure/
date: 2026-06-16
categories:
  - Essays
---


# Fast Index and Progressive Disclosure

![Window example]({{ '/assets/images/chart-progressive-disclosure-cost.png' | relative_url }})

## Spark

Agents need to move quickly, but real-world answers are rarely simple.

If an agent asks, "Is there a table nearby now?", the first answer needs to be fast. But that answer is not enough. The agent may then need to know whether the table can seat four people, whether the restaurant has vegetarian options, whether the menu is current, and whether the table can actually be booked.

The same pattern appears in local services. "Is this builder available next week?" is only the first question. The agent may then need to know what kind of work they do, what price range they operate in, whether they can quote from photos, and whether their availability signal is trustworthy.

The puzzle is this: agents need fast search and deep answers at the same time.

A flat index is too shallow.

A full-context read for every candidate is too slow.

## Stakes

If this problem is not solved, agent coordination becomes expensive, noisy, and unreliable.

The search space can become huge: many entities, listings, transport requests, prices, availability signals, suppliers, and local constraints. Without a fast index, agents waste time inspecting irrelevant records or sending unnecessary agent-to-agent messages.

But speed alone is not enough. Fast retrieval is dangerous if the data is false. Deep answers are useless if the source is unreliable. Progressive disclosure only works if the system knows which actors and records deserve more attention.

For STAP to support real-world action, it needs three things working together:

* fast retrieval
* richer context on demand
* trust to decide what should surface and what deserves deeper inspection

## Core insight

Fast index makes STAP usable. Progressive disclosure makes STAP powerful. Trust makes both safe enough for real-world action.

## Path

First, define the search problem agents face when the space contains many entities and signals. Then separate the role of a fast index from the role of progressive disclosure. After that, show how a query can move from broad retrieval to richer context. Finally, place trust underneath both layers, because speed and depth are only useful when the system can judge reliability.

## Argument

### Claim 1

Agents need a fast index because the search space can become too large for direct inspection.

A practical agent system may need to search across many entities, many listings, many transport requests, many prices, many availability signals, and many supplier types. If every broad query requires deep inspection of every possible match, coordination becomes slow and expensive.

The fast index solves the first bottleneck. It reduces the search space, returns relevant entries faster, avoids unnecessary agent-to-agent messages, makes real-time coordination more practical, and makes discovery cheaper.

The index should carry the fields that help route the first pass:

* location
* time
* category
* intent
* availability
* price
* supplier type
* trust score
* popular search features

These fields are not the whole answer. They are the minimum useful surface for deciding what might deserve attention.

### Claim 2

Progressive disclosure is needed because the first answer should be fast, but the useful answer may need to be deeper.

Not every query needs every detail. A broad query needs routing. A specific question needs richer context.

Progressive disclosure lets the system reveal more only when useful. The first pass can answer, "Which entries are likely relevant?" The second pass can answer, "Which of these entries can actually satisfy the request?" A later pass can answer, "Which action should happen next?"

For a restaurant query, the flow might be:

* Is there a table nearby now?
* Can it seat four people?
* Does it have vegetarian options?
* Can it be booked?

For a builder query, the flow might be:

* Is this builder available next week?
* What kind of work do they do?
* What price range do they operate in?
* Can they quote from photos?

The agent should not need to load all possible detail for every possible result. It should earn deeper context by showing that the record is relevant.

### Claim 3

Fast index and progressive disclosure solve different parts of the same coordination problem.

The fast index is the routing layer. It is optimized for cheap, quick, approximate relevance.

Progressive disclosure is the context layer. It is optimized for richer, more specific answers once the agent has a reason to ask.

A simple flow looks like this:

* Agent asks a broad question.
* STAP returns the best matching entries.
* Agent asks a more specific question.
* Supplier or data source reveals richer context.
* Agent compares.
* Agent acts or asks another follow-up.

This flow keeps the system from doing too much work too early, while still allowing depth when the task requires it.

### Claim 4

Trust has to sit underneath both speed and depth.

Fast retrieval is dangerous if false data rises to the top. Deep answers are useless if the source is unreliable. Progressive disclosure also needs trusted actors, because richer context may come from suppliers, data sources, or other agents that differ in quality and incentives.

Trust decides what gets surfaced. It also decides what deserves more attention.

That does not mean every trusted result is true or every untrusted result is useless. It means the system needs a way to rank, qualify, and constrain what agents should rely on before taking action.

## Concept map

**STAP**: The coordination system implied by the draft. It returns matching entries, supports follow-up questions, and helps agents move from discovery to action.

**Fast index**: The quick retrieval layer. It contains routing fields such as location, time, category, intent, availability, price, supplier type, trust score, and popular search features.

**Progressive disclosure**: The mechanism for revealing deeper context only when useful. It prevents the system from loading full detail for every candidate.

**Broad question**: The agent's first-pass query, such as "Is there a table nearby now?" or "Is this builder available next week?"

**Specific question**: A follow-up that requires richer context, such as seating capacity, vegetarian options, work type, price range, or quote-from-photo ability.

**Supplier or data source**: The actor or record that can reveal richer context after the fast index has narrowed the search.

**Trust score**: A routing and attention signal that helps decide which records should surface and which deserve deeper inspection.

**Availability signal**: A time-sensitive indicator that something may be bookable, usable, open, or otherwise actionable.

**Action**: The point where the agent does something useful: book, compare, request, ask another follow-up, or hand off to a human.

The key relationship is this:

Fast index narrows the search space. Progressive disclosure reveals richer context for the candidates that matter. Trust governs which fast results and deeper answers are reliable enough to use.

## Evidence ledger

| Claim | Evidence | Confidence | Unknown |
|---|---|---:|---|
| Agents need a fast index because the search space can become large. | The draft lists many entities, listings, transport requests, prices, availability signals, and the need for relevant results quickly. | 0.85 | The draft does not quantify the scale where indexing becomes necessary. |
| Progressive disclosure is needed because not every query needs every detail. | The draft states that a first answer should be fast, deeper answers should be available when asked, and specific questions need richer context. | 0.90 | The exact disclosure layers and schemas are not specified. |
| Fast index and progressive disclosure solve different parts of coordination. | The draft separates quick retrieval from richer context and gives a flow from broad question to STAP results to specific question to supplier/data-source detail. | 0.85 | The boundary between indexed fields and deeper context may vary by domain. |
| Trust is required for real-world action. | The draft says fast retrieval is dangerous if data is false, deep answers are useless if sources are unreliable, and trust decides what surfaces. | 0.90 | The trust model, scoring method, and update mechanism are not defined. |

## Counterarguments

One objection is that a powerful agent could skip the fast index and inspect everything directly.

That may work for small spaces. It breaks down when there are many entities, listings, prices, availability signals, and suppliers. Direct inspection turns every query into a deep-read problem, which makes real-time coordination more expensive than it needs to be.

Another objection is that progressive disclosure adds complexity. Why not put all the useful context in the index?

Because not all context is equally useful at the first step. Some fields are expensive, stale, private, domain-specific, or only relevant after a candidate has been shortlisted. A fast index should route. It should not try to become the entire world model.

A third objection is that trust scores can become a false sense of safety.

That is a real risk. Trust should not be treated as certainty. It should qualify attention and action: which records surface first, which sources deserve deeper inspection, and where the agent should ask for confirmation before acting.

## Implications

If this argument is right, STAP should not be designed as either a simple search index or a giant context dump.

It needs a layered architecture:

* fast indexed fields for broad retrieval
* progressive disclosure for richer answers
* trust signals that rank and constrain both layers
* follow-up flows that let agents move from broad search to specific action

The design principle is simple: answer fast first, then answer deeply when the task justifies it.

That makes discovery cheaper, coordination more practical, and agent action safer.

## Agent card

```json
{
  "title": "Fast Index and Progressive Disclosure",
  "spark": "Agents need fast search and deep answers at the same time; a flat index is too shallow, but reading full context for every candidate is too slow.",
  "core_insight": "Fast index makes STAP usable. Progressive disclosure makes STAP powerful. Trust makes both safe enough for real-world action.",
  "claims": [
    {
      "claim": "Agents need a fast index because the search space can become too large for direct inspection.",
      "confidence": 0.85,
      "depends_on": ["large search space", "many entities", "many availability signals"]
    },
    {
      "claim": "Progressive disclosure is needed because the first answer should be fast, but specific questions need richer context.",
      "confidence": 0.9,
      "depends_on": ["broad query", "specific follow-up", "richer context"]
    },
    {
      "claim": "Fast index and progressive disclosure solve different parts of the same coordination problem.",
      "confidence": 0.85,
      "depends_on": ["routing layer", "context layer", "STAP flow"]
    },
    {
      "claim": "Trust has to sit underneath both speed and depth because false fast results and unreliable deep answers are dangerous.",
      "confidence": 0.9,
      "depends_on": ["trust score", "source reliability", "real-world action"]
    }
  ],
  "objects": [
    "stap",
    "fast_index",
    "progressive_disclosure",
    "broad_question",
    "specific_question",
    "supplier",
    "data_source",
    "trust_score",
    "availability_signal",
    "action"
  ],
  "decision_rules": [
    "Use the fast index for broad retrieval, not full understanding.",
    "Reveal deeper context only when the candidate is relevant enough to justify it.",
    "Include location, time, category, intent, availability, price, supplier type, trust score, and popular search features in the routing layer.",
    "Treat trust as an attention and action constraint, not as proof of truth.",
    "Let agents move from broad question to specific follow-up to comparison to action."
  ],
  "counterarguments": [
    "A powerful agent might inspect everything directly instead of needing a fast index.",
    "Progressive disclosure may add complexity compared with putting everything in one index.",
    "Trust scores may create a false sense of safety."
  ],
  "unknowns": [
    "How large must the search space be before fast indexing becomes essential?",
    "Which fields belong in the fast index versus the deeper disclosure layer?",
    "How should trust scores be calculated and updated?",
    "What kinds of agent actions require confirmation even when trust is high?"
  ]
}
```
