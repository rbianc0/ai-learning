# ai-learning

A minimal AI learning system for use with ChatGPT in the browser.

Inspired by [amosblomqvist/learn](https://github.com/amosblomqvist/learn), but adapted for online ChatGPT: the conversation is the teacher/quiz interface and GitHub Pages is the visual learning surface.

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
2. ChatGPT probes the current knowledge frontier and the learning goal.
3. ChatGPT proposes a small dependency graph and waits for approval.
4. Teaching proceeds one node at a time.
5. When a concept is genuinely clearer visually, ChatGPT creates or updates a standalone HTML lesson in `docs/lessons/`.
6. The learner interacts with the page and answers checks/quizzes in ChatGPT.

The visual page is supporting material, not a second teacher. Chat remains the source of interaction and adaptation.

## GitHub Pages

Publish from the `main` branch, `/docs` folder. No Jekyll or build action is required.
