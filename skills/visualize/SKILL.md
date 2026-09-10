---
name: visualize
description: Add a correct, minimal visual or interactive visualization when it materially improves understanding.
---

# Visualize

This skill follows the role of `skills/visualize/` in `amosblomqvist/learn`, but the output target is a standalone HTML lesson instead of an Obsidian image embed.

A visual earns its place only when it reveals structure, motion, geometry, dependence, sequence, comparison, or change more clearly than prose or one equation can.

The learner is strongly visual. When a concept naturally has a visual representation, prefer making that representation **interactive** rather than merely static.

## Choose the lightest useful representation

Use, in roughly this order:

1. **Plain HTML/CSS** for layout, highlighting, step reveals, comparisons, and simple state changes.
2. **Inline SVG** for diagrams, coordinate geometry, vectors, curves, spatial relationships, and animations.
3. **Canvas** only when SVG becomes awkward because many elements update continuously.
4. External libraries only when they provide substantial value that would be unreasonable to reproduce in a few lines of vanilla JavaScript.

Default to no dependencies, no framework, and no build step.

## Good reasons to visualize

Use an HTML visualization when the idea is naturally about:

- dependencies or a graph of concepts;
- a system or flow with parts and arrows;
- a sequence of events or messages;
- a state machine;
- geometry, coordinates, vectors, curves, or function shape;
- a transformation from one representation to another;
- the effect of changing a parameter;
- a multi-step procedure that becomes clearer when steps are revealed or animated.

Do not add decorative visuals that merely restate the prose.

## Interactivity

Prefer one meaningful interaction over many controls.

Examples:

- drag a point and update the tangent;
- move a slider and change a Taylor approximation order;
- click “next” to reveal one algebraic transformation at a time;
- press “send” to animate a packet through a network;
- toggle a prerequisite node and highlight everything that depends on it.

The interaction should expose the concept, not turn the page into a game.

## Standalone lesson pages

Visual lessons live in:

`docs/lessons/<topic-slug>.html`

Each lesson should be a single self-contained HTML file whenever practical. Put its CSS and JavaScript inside the file unless reuse is clearly justified.

A page should contain only what supports the current concept:

- a short title;
- the minimum explanatory text needed to orient the learner;
- the main visual/interactive representation;
- concise labels or instructions;
- optional step controls.

Do **not** duplicate the adaptive teaching conversation or quiz system in HTML. Questions, answers, diagnosis, and adaptation happen in ChatGPT.

## Correctness before aesthetics

Before treating a visualization as teaching material, inspect the logic carefully:

- labels must correspond to the right objects;
- arrows and dependencies must point in the correct direction;
- mathematical quantities must update consistently;
- animations must preserve the actual causal/temporal ordering;
- changing a control must never imply a false relationship.

A simple correct visual is better than a sophisticated misleading one.

## Keep the browser and chat complementary

The browser answers: **“Can I see or manipulate the idea?”**

ChatGPT answers: **“Why does this work, what do you understand already, and what should we learn next?”**

Keep those roles separate.
