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
6. For an approved multi-node learning plan, create a navigable visual path under `docs/lessons/<topic-slug>/`: an `index.html` roadmap plus one permanent HTML page per taught node (`01-<node>.html`, `02-<node>.html`, ...). Do not overwrite earlier node lessons when advancing.
7. Every node page should link back to the path index and to existing previous/next nodes. When a new node is created, update the previous node's Next link and the path index status/progress.
8. Add the learning-path index to `docs/index.html` and give the learner the GitHub Pages path URL so it can stay open beside ChatGPT.
9. Do not build extra infrastructure unless the learner explicitly asks for it. Preserve the minimal architecture: vanilla HTML/CSS/JS, no backend, no database, no framework, no build step.
10. Follow the core sequence **probe → plan → teach**. Do not begin Phase 3 teaching until the learner has approved the plan.
11. **Ask only one question at a time.** During the probe phase and all later quiz-checks, default to a single **4-option multiple-choice question (A–D)**, wait for the learner's answer, give concise feedback, and adapt the next question to that answer. Never dump a batch of diagnostic or quiz questions unless the learner explicitly asks for a batch.
12. After the learner approves the dependency plan, save a checkpoint under `sessions/<topic-slug>.md`. Record the learning goal, established foundations, identified gaps, approved dependency graph, teaching preferences that matter to the session, completed nodes, and the exact next step.
13. Update that checkpoint at meaningful milestones so a future conversation can resume without repeating the probe or losing progress.

If the learner starts a genuinely new topic later, repeat the process from the probe phase rather than assuming their level from an unrelated topic. If the learner resumes an existing topic, read its checkpoint first and continue from the saved next step unless the learner asks to reassess.

## Design

The system intentionally has three parts:

1. **ChatGPT teaches** — probe → plan → teach, using `skills/teach/SKILL.md`.
2. **GitHub persists** — teaching protocol, session checkpoints, and permanent node lessons live in this repository.
3. **GitHub Pages visualizes** — each learning path has an index and self-contained interactive node pages.

There is no backend, database, framework, build step, or quiz synchronization. Keep ChatGPT and the lesson page side by side; answer all teaching questions in chat.

## Repository

```text
skills/
  teach/SKILL.md       teaching philosophy and process
  visualize/SKILL.md   visual/interactive lesson policy
agents/
  researcher.md        research/verification policy
sessions/
  <topic-slug>.md      resumable learning checkpoints
docs/
  index.html           GitHub Pages home / list of learning paths
  lessons/
    <topic-slug>/
      index.html       path roadmap and progress
      01-<node>.html   permanent interactive lesson
      02-<node>.html
      ...
```

## Learning workflow

The general workflow is:

**probe → approve plan → save checkpoint → teach → periodically update checkpoint**

In practice:

1. Ask ChatGPT to teach a topic using this repository.
2. ChatGPT probes the current knowledge frontier and the learning goal, **one 4-option multiple-choice question at a time**.
3. ChatGPT proposes a small dependency graph and waits for approval.
4. Once approved, ChatGPT saves the plan and current frontier in `sessions/<topic-slug>.md` before teaching begins.
5. For a multi-node plan, ChatGPT creates `docs/lessons/<topic-slug>/index.html` as the visual roadmap.
6. Teaching proceeds one dependency node at a time. When visualization helps, that node gets a permanent self-contained HTML page.
7. After each taught node, ChatGPT asks **one quiz-check at a time** before advancing.
8. When a node is completed, ChatGPT updates the session checkpoint and path index. When the next node page is created, neighboring Previous/Next navigation is wired automatically.
9. The learner keeps the current node page open beside ChatGPT, interacts with it, and answers checks/quizzes in chat.

The checkpoint is the source of continuity across conversations. The learning-path index is the source of visual navigation. Individual node pages are durable learning artifacts that remain directly revisitable.

To resume a saved session in a fresh conversation, use:

```text
@GitHub Read rbianc0/ai-learning/README.md and rbianc0/ai-learning/sessions/<topic-slug>.md, then continue from the saved checkpoint.
```

The visual pages are supporting material, not a second teacher. Chat remains the source of interaction and adaptation.

## GitHub Pages

Publish from the `main` branch, `/docs` folder. No Jekyll or build action is required.

Once Pages is enabled, the site should be available at:

```text
https://rbianc0.github.io/ai-learning/
```
