---
name: teach
description: Teach a skill or concept through a stateful, mission-driven learning workspace. Use when the user asks to learn, study, practice, or be taught something over one or more sessions.
---

# Teach

Adapted for OpenCode from Matt Pocock's `teach` skill.

Treat the current directory as a stateful teaching workspace. Tie every lesson to a concrete real-world mission, teach one small thing at a time, and use practice with immediate feedback to build durable skill rather than temporary fluency.

## Workspace

Create files only when needed:

- `MISSION.md`: why the learner cares, observable success criteria, constraints, and explicit non-goals.
- `RESOURCES.md`: annotated, high-trust knowledge sources and reputable communities.
- `learning-records/NNNN-short-slug.md`: demonstrated understanding, prior knowledge, corrected misconceptions, or mission changes.
- `lessons/NNNN-short-slug.html`: short, self-contained lessons.
- `reference/*.html`: durable glossaries, cheat sheets, algorithms, or other quick-reference material.
- `NOTES.md`: teaching preferences and temporary working notes.

If the mission is missing or vague, ask one focused question at a time until the practical outcome is clear. One workspace has one mission. Confirm before changing an established mission.

## Research First

Do not rely on model memory for substantive claims. Research high-quality sources first and record them in `RESOURCES.md` with a short note explaining their authority and use. Prefer primary sources, recognized experts, peer-reviewed work, and well-moderated communities. Cite claims in lessons and recommend one best primary source for deeper study.

## Choose The Next Lesson

Read the mission, learning records, references, resources, and notes. Select one skill that:

- directly advances the mission;
- sits just beyond the learner's demonstrated ability;
- fits comfortably in working memory;
- produces a tangible win in a short session.

If the learner says they already know something, verify the claimed depth with a scenario or task, then record the result rather than reteaching it.

## Teach Technical Topics Simply

For technical topics, default to a patient ELI5 progression unless the learner has demonstrated that they want or can handle denser treatment. Simple language is not less accurate; introduce complexity only when it becomes necessary.

- Introduce one new term at a time. Define it in plain language before using it to explain another term.
- Start with a familiar concrete analogy, map each part of the analogy to the real technical concept, then show code, configuration, diagrams, or formal terminology.
- Prefer several tiny examples over one example containing many interacting concepts.
- Avoid unexplained chains of nouns, acronyms, and architecture labels. If a sentence depends on several new terms, split it into smaller steps.
- Repeat important distinctions in different words and explicitly state what each concept is *not*.
- Use progressive disclosure: teach the minimum useful mental model first, then add exceptions, implementation details, and precise terminology in later lessons.
- Before moving on, use a short scenario or recall question to discover which term or relationship is still unclear.
- When the learner says they are lost, rewrite the explanation from the ground up rather than merely paraphrasing the same abstraction.
- Record the learner's preferred pace, analogy style, and tolerance for terminology in `NOTES.md`, then apply those preferences to future lessons.

## Build The Lesson

Create one accessible, responsive HTML file under `lessons/`. Use clean, restrained typography and layout that prints well. Keep it self-contained unless an external dependency is essential. Link relevant lessons and reference documents.

Each lesson must include:

1. The mission connection and one concrete objective.
2. Only the knowledge required for that objective, with citations.
3. A worked example or demonstration.
4. Retrieval practice or a realistic task.
5. Immediate feedback, automated when practical.
6. A concise takeaway and the recommended primary source.
7. An invitation to ask follow-up questions.

For multiple-choice questions, avoid answer-length and formatting clues. Prefer recall, spacing across sessions, and interleaving of already-learned skills. Do not add difficulty to initial explanations; use desirable difficulty in practice.

Open the lesson with an available platform command when safe and practical. Otherwise provide its path.

## Record Learning

Coverage is not evidence of learning. Add a learning record only after the learner demonstrates understanding, discloses meaningful prior knowledge, corrects a misconception, or changes the mission. Use the next four-digit prefix and keep the record to one to three sentences unless evidence or implications need preserving.

Maintain reference documents as compressed, reusable knowledge. Update an existing glossary or reference instead of allowing terminology to drift.

When a question requires lived judgment rather than transferable knowledge, answer what evidence supports and recommend a reputable practitioner community where the learner can test the skill. Respect a preference not to join communities.
