# Skill 2: Learning Path Architect

> **When to use this:** Use this skill after Checkpoint 1 is confirmed — when the topic list from Skill 1 has been reviewed and approved. This skill builds the full day-by-day skeleton of the learning path before any content is written.

---

## How to Trigger This Skill

Copy the prompt below and paste it into your Research & Learning Hub project. You will be asked a set of questions before anything is built.

---

## The Prompt

```
SKILL: Learning Path Architect

The confirmed topic list is as follows:
[PASTE CONFIRMED TOPIC LIST FROM SKILL 1 OUTPUT HERE]

Audience for this learning path: [DESCRIBE AUDIENCE — experience level, role, background]

---

Before building anything, ask the following questions and wait for answers:

QUESTION 1: How many days should this learning path span?
QUESTION 2: How many hours per day is a learner expected to dedicate to this?
QUESTION 3: Who is the Training POC (point of contact) for this learning path?

Do not proceed until all four questions are answered.

---

Once answers are received, do the following:

1. BUILD the full day-by-day learning path skeleton using the confirmed topic list and the schema below.

2. DISTRIBUTE topics across the specified number of days logically:
   - Sequence from foundational to advanced
   - Group related concepts into the same day where it makes sense
   - Never overload a single day beyond the specified hours
   - If the topic list cannot fit within the specified days at the specified hours, flag this clearly and suggest either adding days or splitting heavy topics — do not silently compress

3. FOR EACH DAY include:
   - Day number and topic name
   - Learning objective (one clear sentence, 3rd person, starts with an action verb)
   - List of concepts to be covered
   - Estimated time for that day
   - Hands-on flag: [HANDS-ON RECOMMENDED] or [THEORY ONLY] based on topic type
   - Visual flag: [VISUAL RECOMMENDED] or [NO VISUAL NEEDED] based on topic type

4. VISUAL DECISION GATE — after presenting the skeleton, ask:
   "Some modules have been flagged as [VISUAL RECOMMENDED]. Should visuals be included for these modules? Please confirm which flags to keep, remove, or add before proceeding."

5. OUTPUT a METADATA BLOCK at the top of the learning path:
   - Learning Path Title
   - Training POC (use the name provided in Question 4)
   - Version (start at v1.0)
   - Date Created (use today's date)
   - Created By (use the name provided in Question 3)
   - Objective (overall — what the learner will be able to do by the end)
   - Target Audience
   - Knowledge Prerequisites
   - Tools Needed (if technical topic)
   - Total Duration (days + hours)

---

Constraints:
- All output written in 3rd person — no you / I / me / we / your / our
- Do not write any What / How / Why content yet — this is a skeleton only
- Do not write quiz questions yet
- Do not suggest reading links yet
- Each day must have an estimated time
- If a topic from the confirmed list does not fit logically, flag it rather than silently dropping it
- Wait for owner confirmation of the skeleton and visual flags before proceeding to Skill 3

---

End with this exact line:
"Learning path skeleton complete. Please review the structure, day breakdown, and visual flags. Confirm, adjust, or add changes before proceeding to Skill 3: Module Content Builder."
```

---

## What You Will Get Back

| Output | Description |
|---|---|
| **Metadata Block** | Title, Training POC, version, date created, created by, objective, audience, prerequisites, tools, total duration |
| **Day-by-Day Skeleton** | Each day with topic, objective, concepts, estimated time, hands-on flag, visual flag |
| **Visual Decision Gate** | A prompt asking you to confirm which visual flags to keep before content is written |

---

## Your Action at Checkpoint 2

Once you receive the skeleton, review it and do one of the following:

- ✅ **Confirm** — "Structure looks good, visual flags confirmed, proceed to Skill 3"
- ✏️ **Adjust** — "Move topic X to Day 3, remove visual flag on Day 2, add a hands-on flag to Day 4, then proceed"
- ➕ **Add a day** — "Insert a new day between Day 2 and Day 3 covering [topic], keep everything else as is"
- ❌ **Reject and redo** — "The sequencing doesn't feel right, here is how I'd restructure it: [explain]"

Do not proceed to Skill 3 until structure and visual flags are confirmed.

---

## Important: Adding or Editing Days Later

If a new topic needs to be added after Checkpoint 2, use this instruction:

```
Add a new day between Day [X] and Day [X+1] covering [TOPIC NAME].
Keep all other days exactly as they are — do not restructure or renumber the rest.
Apply the same skeleton format: objective, concepts, estimated time, hands-on flag, visual flag.
```

This prevents AI from rebuilding the entire learning path when only one module is being changed.

---

## Example Trigger (What It Looks Like in Practice)

```
SKILL: Learning Path Architect

The confirmed topic list is as follows:
1. What is Apache Airflow and why it exists
2. Core concepts: DAGs, operators, tasks, and connections
3. Setting up a local Airflow environment
4. Building a first DAG
5. Scheduling and dependencies
6. Monitoring and debugging pipelines
7. Best practices and production considerations

Audience for this learning path: Junior data engineers with basic Python knowledge
and some exposure to SQL. No prior experience with orchestration tools.
```

*(AI will then ask the four questions before building anything.)*

---

*Skill 2 of 5 — Research & Learning Hub*
*Input comes from → Skill 1: Research Synthesizer (Checkpoint 1 confirmed)*
*Output feeds into → Skill 3: Module Content Builder*