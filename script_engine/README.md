# ETC Script Engine

A reusable writing system for creating research-backed, engaging technology and science documentaries for **ETC — Exploring Technology & Computing**.


## Mandatory editorial filter

Before creating or approving any script, read `EDITORIAL_GUARDRAILS.md`. It applies to every ETC documentary and is enforced by the master instructions and quality checklist. It covers story versus lecture, jargon control, coherent analogies and examples, confident but accurate narration, real demonstrations, code/output verification, pacing, and honest table-read status.

## How to use

Give the AI only:

```text
Title: [Your video title]
Duration: [Target video duration]
```

Example:

```text
Title: How Does Code Become a Running Program?
Duration: 10 minutes
```

Then ask the AI to follow `Who_to_write.md` and every relevant supporting file in this folder.

## File guide

| File | Responsibility |
|---|---|
| `Who_to_write.md` | Master instructions: role, workflow, storytelling, research, writing and deliverables |
| `RESEARCH_PROTOCOL.md` | Evidence standards, source hierarchy and claim verification |
| `SCRIPT_FORMAT.md` | Required structure and formatting of the finished script |
| `QUALITY_CHECKLIST.md` | Final editorial, factual and audience-retention review |
| `EDITORIAL_GUARDRAILS.md` | Mandatory preflight and final filter for clarity, storytelling, demonstrations, consistency, pacing and integrity |
| `INPUT_TEMPLATE.md` | Minimal user input format |

## Required output

The AI must produce:

1. A clear documentary premise and central question.
2. A research brief with traceable sources.
3. A structured narrative outline.
4. A complete, original, ready-to-record narration script.
5. A timestamped visual and sound-design direction alongside the narration.
6. A fact-check report and unresolved caveats.
7. A final quality assessment.

## Editorial identity

ETC makes complex ideas understandable without making them inaccurate. The goal is not to sound complicated or sensational. The goal is to make viewers curious, help them understand the real mechanism, and leave them with a stronger mental model.

**Editorial principle:** Accuracy before drama. Clarity before jargon. Evidence before confidence. Story before lecture.
