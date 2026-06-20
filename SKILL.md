---
name: project-learning-notes
description: Turn a code project into an evolving study system: inspect source files, generate or refresh learning notes and a progress document, and persist chapter-specific user questions with their answers. Use when a user wants to learn from an existing repository, asks to create study notes or a learning plan from project code, or asks a question about a named chapter, module, or lesson that should be added to the project's learning documentation.
---

# Project Learning Notes

Build an evidence-based learning loop from the target repository. Keep the learning documents aligned with the code and preserve chapter questions as durable Q&A.

## 1. Inspect before writing

1. Read repository instructions and list source files with `rg --files`.
2. Identify the entry points, modules, feature groups, and existing documentation.
3. Infer chapters from the code structure; do not invent features that the code does not demonstrate.
4. Reuse existing learning documents. If none exist, create `docs/<project>-study-notes.md` and `docs/learning-progress.md`.

## 2. Create or refresh the study system

Maintain three artifacts:

| Artifact | Purpose |
| --- | --- |
| Study notes | Chapter map, concepts, code references, concise explanations, and Q&A |
| Progress document | Ordered checklist, current chapter, mastery notes, next action, and dated changelog |
| `AGENTS.md` | Persistent project rule that chapter questions must be answered and then recorded |

For each chapter, include the source file paths, what the code demonstrates, key concepts, a small representative snippet only when useful, and pitfalls visible in the project. Keep notes in the user's language when clear from the repository or conversation.

## 3. Handle a chapter question

When the user asks about a chapter, lesson, module, or example file:

1. Locate the matching chapter and read the relevant source before answering.
2. Give a direct, code-grounded answer.
3. Append a non-duplicate `Q&A` entry to that chapter in the study notes using the user's question and the final answer.
4. Update the progress document only when the question proves a new learning state, adds a useful mastery note, or changes the next action.
5. Add a dated changelog entry for substantive updates.

Record the answer after answering in the conversation. Do not ask for separate permission to update the learning documents. Never copy secrets, access tokens, passwords, or private data from source files into notes.

## 4. Keep the documents trustworthy

- Link every topic to one or more repository files.
- Preserve user-written notes and existing Q&A; improve only the relevant section.
- Mark uncertain interpretations as questions for the learner instead of presenting them as facts.
- Keep progress honest: completion means the learner has studied or verified the topic, not merely that a source file exists.
- Make documentation changes only; do not alter application code unless the user also requests implementation work.

## Completion check

Before handing off, verify that the notes and progress files exist, chapter references point to real files, the current chapter has a clear next action, and any chapter question from the session appears exactly once in the matching Q&A section.
