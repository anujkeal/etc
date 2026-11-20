# ETC SCRIPT GUARDRAILS — EDITORIAL PREFLIGHT AND FINAL FILTER

> Mandatory for every ETC script. Apply these checks to the subject at hand; do not force a technical demonstration or analogy where it would be unnatural. This file supplements the master instructions, research protocol, format, and quality checklist.

## 1. The audience contract

Assume an intelligent, curious viewer with no specialist background unless the user specifies otherwise.

- Explain the real mechanism, not merely the vocabulary surrounding it.
- Introduce a technical term only when the viewer needs it. Define it in plain language at first use.
- Prefer one useful term explained well over several impressive terms left unexplained.
- As an editorial default, keep specialist jargon to the minimum necessary; aim to remove roughly one in five nonessential technical terms during revision.
- Never confuse accessibility with childishness or factual simplification.

## 2. Story, not a lecture

Before drafting, write down:
- The central question.
- The viewer's reason to care.
- The mystery, tension, problem, contradiction, or practical consequence that drives the explanation.
- The specific discovery or payoff the viewer will reach.
- The most memorable idea the viewer should retain.

Every scene must advance the story, deepen understanding, show evidence, or deliver a payoff. A sequence of accurate definitions is not automatically a documentary.

Open a meaningful question early. Create progression by revealing information in a useful order. Resolve the opening promise clearly. Do not manufacture suspense or hide a simple answer merely to increase retention.

## 3. Analogy discipline

Use a recurring everyday analogy when it genuinely makes an unfamiliar mechanism easier to understand.

- Choose one primary analogy and keep its mapping consistent across the relevant scenes.
- Map each important part of the real process to the analogy before using it.
- Do not casually switch between unrelated analogies; if a second analogy is essential, signal the change and explain why.
- State where the analogy stops matching reality. Never let the analogy replace the actual mechanism.
- Do not force an analogy onto a subject where it would distort the explanation. A concrete example, experiment, visual model, or case study may work better.

The analogy should be a bridge into the real explanation, not the explanation itself.

## 4. Example and sequence consistency

- If the premise promises one example, use one example consistently unless there is a clear editorial reason to introduce another.
- Follow one example through the complete process before switching languages, systems, people, locations, time periods, or cases.
- If comparison is the point, introduce each case deliberately and explain why the comparison matters.
- Avoid introducing an example, abandoning it for several scenes, then returning without a clear transition.
- Check that the title, premise, narration, visuals, and conclusion all describe the same scope.

## 5. Narration confidence and factual calibration

Write spoken narration in clear, direct, confident language when the evidence supports it.

- Remove habitual hedging such as repeated "can", "may", "might", "possibly", and "it depends" when it adds no meaningful precision.
- Do not remove qualifications that are necessary for truth. Move secondary implementation details, exceptions, and edge cases to concise on-screen notes or editorial notes when they are not needed in the spoken story.
- State the scope of a claim clearly (for example, the named product, version, platform, jurisdiction, period, or implementation) instead of weakening every sentence.
- Never turn a qualified fact into a universal claim just to sound confident.
- Separate what is established, what is typical, what is an illustrative model, and what remains uncertain.

Confidence must come from precise scope and evidence, not from overstatement.

## 6. Concrete proof and "aha" moments

Look for at least one visible or audible payoff that lets the viewer observe the subject rather than only hear an explanation.

Depending on the subject, this may be:
- A real terminal or software demonstration.
- An experiment with observable results.
- A before-and-after comparison.
- A primary-source document, original recording, dataset, or measurement.
- A real object, process, interface, or location.
- A carefully labelled conceptual animation when direct observation is impossible.

Make the demonstration answer a specific question. Show the actual input, operation, and result where feasible. Do not invent outputs, interfaces, logs, experiments, footage, or evidence. Label simulations and conceptual visualisations honestly.

For code or commands shown on screen:
1. Verify syntax, escaping, filenames, commands, and output.
2. Run the exact snippet or command in the stated environment when practical.
3. Record the operating system, tool/compiler/interpreter version, architecture, and relevant flags if they affect the result.
4. Ensure the displayed output comes from the actual run. If it cannot be run, label it as illustrative and do not present it as recorded evidence.
5. Check that every on-screen code sample matches the final narration and source file character-for-character.

A demonstration is not mandatory when it would be artificial or impossible. In that case, use the strongest honest evidence or visual model available and explain its status.

## 7. Technical and factual integrity

- Do not treat one implementation, version, platform, architecture, or workflow as universal.
- Verify exact code, commands, equations, units, dates, names, quotations, and outputs.
- Test executable examples when practical; inspect outputs rather than assuming what they will be.
- Distinguish actual footage/data from simulations, reconstructions, diagrams, and conceptual visuals.
- Put implementation-specific caveats close to the claim or in a clearly visible note.
- Never fabricate a test, terminal recording, source, quotation, result, or fact-check.

## 8. Pacing and runtime

Estimate the runtime from the actual narration word count and planned visual-only time.

- Use the narration-speed guidance in `Who_to_write.md` as a planning estimate, not a guarantee.
- Do not assign long timestamps to short narration unless the visual action genuinely carries the time.
- Give abstract sections a concrete visual change, example, comparison, demonstration, or deliberate pause.
- Watch for consecutive scenes that explain concepts without showing evidence or producing a new insight.
- Do not pad the script with repeated explanations to reach the requested duration.
- Recalculate runtime after every substantial revision.

### Table-read rule

A script is not "table-read" merely because its word count was calculated.

- If a real read-aloud is possible, read the complete narration at a natural recording pace and time it.
- If no actual read-aloud was performed, state: **"Table read pending — runtime is an estimate."**
- Never claim a timed table read, recording, or final runtime that did not happen.
- After the table read, adjust scene timestamps to the measured narration and visual pauses.

## 9. Mandatory final filter

Before delivery, run these checks against the final version, not an earlier draft:

- **Promise:** Does the script deliver exactly what its title and opening promise?
- **Story:** Does it feel like a journey of discovery rather than a lecture?
- **Clarity:** Can a non-specialist follow the causal chain without unexplained jargon?
- **Consistency:** Are examples, analogies, terminology, and chronology coherent?
- **Confidence:** Is narration direct without becoming inaccurate?
- **Proof:** Is there a real, feasible demonstration or the strongest honest alternative?
- **Visual payoff:** Does each abstract section give the viewer something meaningful to see or understand?
- **Accuracy:** Have code, commands, outputs, facts, and source claims been checked?
- **Pacing:** Are timestamps and word counts plausible? Are any scenes long or slow without a visual reason?
- **Completion:** Is the table read genuinely complete, or clearly marked pending?
- **Integrity:** Are all uncertainties, simulations, and unperformed checks disclosed?

If a critical item fails, mark the script **REVISE** or **RESEARCH REQUIRED**. Do not label it production-ready to be agreeable.


## 2A. Narrative tension, specificity, and retention

A script can be accurate, clear, and logically organised yet still feel like a lecture. Do not mistake completeness for watchability. The viewer should experience a sequence of discoveries, not receive the conclusion followed by ten minutes of supporting definitions.

### Build an unresolved question

- Open with a concrete puzzle, contradiction, consequence, unusual event, surprising demonstration, or human story that makes the subject matter.
- Do not reveal the full thesis or answer in the opening. Establish the question and stakes; let the explanation earn the answer.
- Give the viewer enough context to understand why the question matters, but preserve a meaningful discovery for later.
- Create honest tension from a real problem, constraint, conflict, failure, decision, or consequence. Never manufacture danger or exaggerate the evidence.
- Each major section should change what the viewer understands, raise a more precise question, or pay off an earlier question.
- Do not use artificial cliffhangers. Curiosity must be rewarded with substantive information.

### Prefer specific stories over generic placeholders

- Search for two or three strong, verifiable real-world stories, people, decisions, incidents, inventions, failures, or surprising applications when the topic supports them.
- Prefer a named person, organisation, place, date, system, and consequence over generic phrases such as "imagine a company" or "scientists wanted".
- Use anecdotes as evidence and narrative engines, not decorative trivia. Explain what happened, why it happened, and what it reveals about the central question.
- Research the exact details and context. Do not repeat a viral anecdote, attribution, date, or causal explanation without checking it against reliable sources.
- Do not force a fixed number of stories onto subjects that do not support them. One compelling, well-supported case is better than three weak ones.
- Keep the number of examples manageable. Each story must deepen the central argument rather than become a tangent.

### Make the mechanism visible

- Identify the strongest demonstration that lets viewers see the idea work.
- For programming and computing topics, prioritise real code, terminal output, interfaces, source documents, benchmarks, or a controlled side-by-side comparison when relevant and feasible.
- If comparing technologies, demonstrate the same meaningful task or constraint across them. Explain what the comparison does and does not prove.
- Verify every code sample and output. Label unexecuted examples as illustrative; never fabricate a terminal run or result.
- Use logos only for identification. A sequence of logos, generic icons, abstract diagrams, or animated labels is not a substitute for showing the mechanism, event, evidence, or consequence.
- When archival footage, documents, interfaces, or real objects exist and are relevant, use them to anchor the story. Label reconstructions and conceptual visuals honestly.

### Vary the narration and scene rhythm

- Vary sentence length, paragraph shape, and scene function. Use short lines for emphasis, not as the default rhythm for every paragraph.
- Mix explanation with narrative scenes, demonstrations, evidence, consequences, and moments of reflection.
- Avoid repetitive rhetorical questions and predictable templates such as repeated "It's not X, it's Y", "But here's the important part", or "Imagine..." openings.
- Read transitions for natural spoken flow. Do not make every scene end with a formulaic tease.
- Remove repeated explanations even when they use different wording. Each return to an idea must add a new layer, evidence, consequence, or resolution.

### Stress-test the middle

- The middle of the documentary is a common retention failure point. Review it separately, not just the opening and ending.
- For every middle scene, state what new fact, story, demonstration, complication, or payoff it contributes.
- Merge or cut scenes that merely restate the thesis, list examples, or repeat trade-offs already explained.
- Introduce a meaningful escalation: a more difficult case, a surprising exception, a real consequence, or a test of the viewer's developing mental model.
- Do not keep a chapter simply because it is technically relevant. Relevance is not enough; it must earn its runtime.
- If the requested duration causes padding, recommend a shorter, stronger runtime rather than stretching the material.

The goal is not relentless excitement. It is forward motion: each scene should make the viewer want the next piece because it changes or completes the picture.

