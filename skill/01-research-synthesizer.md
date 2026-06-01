# Skill 1: Research Synthesizer

> **When to use this:** Use this skill at the very start of any new learning or research project. This is always the first step before building any learning path.

---

## How to Trigger This Skill

Copy the prompt below, paste it into your Research & Learning Hub project, then provide your sources in any of these formats:
- **Links** — paste URLs directly
- **Text/content** — paste the content itself
- **Files** — upload PDFs or documents
- **Mix** — any combination of the above is fine

---

## The Prompt

```
SKILL: Research Synthesizer

I am providing source materials on the following topic: [TOPIC NAME]

Sources are provided below (may be links, pasted content, uploaded files, or a mix):
[PASTE SOURCES / LINKS / UPLOAD FILES HERE]

---

Instructions:

1. SYNTHESIZE all provided sources into a unified understanding of the topic.
   - Do not summarize each source individually
   - Find the common threads, key principles, and important distinctions across all sources
   - Note any conflicts or disagreements between sources

2. OUTPUT a CONCEPT MAP in two formats:
   a. Structured Outline — a hierarchical text-based breakdown of the core concepts, sub-concepts, and how they relate
   b. Visual Diagram — a Mermaid diagram showing the relationships between concepts

3. OUTPUT KEY INSIGHTS — a list of the most important takeaways from the synthesis. Each insight should be 1-2 sentences, written in 3rd person.

4. OUTPUT a SUGGESTED TOPIC LIST for a learning path on this subject.
   - Be bold — go beyond just what the sources cover
   - Suggest a full, logical progression of topics a learner would need to truly understand this subject
   - Flag any suggested topics that are NOT covered in the provided sources with a [GAP] tag
   - Sequence topics from foundational to advanced
   - Group topics by logical day/module if possible
   - Standardize the columns: Day/Module, Topics, Phase, Tag
   - Use the Phase column to group topics by architectural layer or pipeline phase (e.g., Storage, Catalog & Security, ETL & Quality, Orchestration, Analytics & Governance, Capstone)
   - Use the Tag column for flags only — `[GAP]` for topics not in sources, leave as `—` otherwise

---

Constraints:
- All output written in 3rd person — no you / I / me / we / your / our
- Do not recommend or validate any links at this stage — that happens in a later skill
- Do not build the learning path yet — only produce the concept map, key insights, and suggested topic list
- Wait for owner confirmation before proceeding to Skill 2

---

End with this exact line:
"Synthesis complete. Please review the concept map, key insights, and suggested topic list. Confirm, adjust, or add topics before proceeding to Skill 2: Learning Path Architect."
```

---

## What You Will Get Back

| Output | Description |
|---|---|
| **Concept Map (Outline)** | Hierarchical text breakdown of all core concepts and how they connect |
| **Concept Map (Visual)** | Mermaid diagram of concept relationships |
| **Key Insights** | The most important takeaways across all sources, in 3rd person |
| **Suggested Topic List** | Bold, full-progression topic list with [GAP] flags for topics beyond your sources |

---

## Your Action at Checkpoint 1

Once you receive the output, review the suggested topic list and do one of the following:

- ✅ **Confirm** — "Topic list looks good, proceed to Skill 2"
- ✏️ **Adjust** — "Remove X, add Y between topic 2 and 3, then proceed to Skill 2"
- ❌ **Reject and redo** — "This missed the mark, here is what I actually need: [explain]"

Do not proceed to Skill 2 until this is confirmed.

---

## Example Trigger (What It Looks Like in Practice)

```
SKILL: Research Synthesizer

I am providing source materials on the following topic: Apache Airflow for Data Engineering

Sources:
- https://airflow.apache.org/docs/
- https://medium.com/some-article-on-airflow
- [uploaded PDF: airflow-internals-paper.pdf]
- [pasted content: blog post text here...]
```

---

*Skill 1 of 5 — Research & Learning Hub*
*Output feeds into → Skill 2: Learning Path Architect*