# ai-learning

A minimal AI learning system for use with ChatGPT in the browser.

Inspired by [amosblomqvist/learn](https://github.com/amosblomqvist/learn), but adapted for online ChatGPT: the conversation is the teacher/quiz interface and GitHub Pages is the visual learning surface.

## Start a new learning session

In any fresh ChatGPT conversation with GitHub connected, send:

```text
@GitHub Read rbianc0/ai-learning/README.md and teach me <TOPIC>.
```

Example:

```text
@GitHub Read rbianc0/ai-learning/README.md and teach me Fourier transforms.
```

That is enough. The README is the bootstrap file for the whole system.

### Instructions for ChatGPT when bootstrapping from this README

Before teaching the requested topic:

1. Read `skills/teach/SKILL.md` and follow it as the teaching protocol.
2. Read `skills/visualize/SKILL.md` and use it whenever a visual or interactive representation materially improves understanding.
3. Read `agents/researcher.md` when factual verification or current research is needed.
4. Keep diagnostic questions, Socratic questions, quizzes, answers, and adaptation inside the ChatGPT conversation.
5. Use the GitHub repository as the persistent learning-material store.
6. When visualization is useful, create or update a self-contained HTML page under `docs/lessons/<topic-slug>.html` and add its link to `docs/index.html`.
7. Give the learner the GitHub Pages lesson URL after creating or updating the page so they can keep it open beside ChatGPT.
8. Do not build extra infrastructure unless the learner explicitly asks for it. Preserve the minimal architecture: vanilla HTML/CSS/JS, no backend, no database, no framework, no build step.
9. Follow the core sequence **probe → plan → teach**. Do not begin Phase 3 teaching until the learner has approved the plan.
10. **Ask only one question at a time.** During the probe phase and all later quiz-checks, default to a single **4-option multiple-choice question (A–D)**, wait for the learner's answer, give concise feedback, and adapt the next question to that answer. Never dump a batch of diagnostic or quiz questions unless the learner explicitly asks for a batch.

If the learner starts a new topic later, repeat the process from the probe phase rather than assuming their level from an unrelated topic.

## Design

The system intentionally has three parts:

1. **ChatGPT teaches** — probe → plan → teach, using `skills/teach/SKILL.md`.
2. **GitHub persists** — teaching protocol and lesson pages live in this repository.
3. **GitHub Pages visualizes** — each lesson is a standalone HTML page with only the CSS/JavaScript it needs.

There is no backend, database, framework, build step, or quiz synchronization. Keep ChatGPT and the lesson page side by side; answer all teaching questions in chat.

## Repository

```text
skills/
  teach/SKILL.md       teaching philosophy and process
  visualize/SKILL.md   visual/interactive lesson policy
agents/
  researcher.md        research/verification policy
docs/
  index.html            GitHub Pages home
  lessons/              standalone interactive lessons
```

## Learning workflow

1. Ask ChatGPT to teach a topic using this repository.
2. ChatGPT probes the current knowledge frontier and the learning goal, **one 4-option multiple-choice question at a time**.
3. ChatGPT proposes a small dependency graph and waits for approval.
4. Teaching proceeds one node at a time, with **one quiz-check at a time** before advancing.
5. When a concept is genuinely clearer visually, ChatGPT creates or updates a standalone HTML lesson in `docs/lessons/`.
6. The learner keeps that page open beside ChatGPT, interacts with it, and answers checks/quizzes in chat.

The visual page is supporting material, not a second teacher. Chat remains the source of interaction and adaptation.

## GitHub Pages

Publish from the `main` branch, `/docs` folder. No Jekyll or build action is required.

Once Pages is enabled, the site should be available at:

```text
https://rbianc0.github.io/ai-learning/
```
