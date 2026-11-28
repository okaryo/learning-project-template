# Learning Project Pattern

This document describes a reusable way to run AI-assisted learning projects.
It can be copied into a new repository and adapted to the subject being studied.

## Purpose

Use small implementation projects to understand how a tool, system, protocol,
or library works internally.

The project should optimize for learning and inspectability rather than feature
volume. A successful project does not need to become production-ready. It should
make the important mechanisms visible.

## Core Principles

- Define the learning goal before expanding the roadmap.
- Define non-goals so the project does not drift into a production rewrite.
- Start with a deliberately small core milestone.
- Make the first milestone small enough that the source-to-result lifecycle is
  visible quickly.
- Treat roadmap sections as learning themes, not as single implementation
  steps.
- A request to proceed advances one learning unit once the current unit's
  understanding check is complete.
- Confirm the learning objective before starting a major implementation step.
- Keep changes small, inspectable, and explainable.
- Prefer standard library or minimal local implementations when the goal is to
  understand the mechanism.
- Add external dependencies only when they directly support a learning question.
- Record decisions, direction changes, open questions, and completed learning
  units as the project evolves.
- Update the roadmap when the learning direction changes instead of forcing the
  original plan.
- Keep optional follow-ups separate from the main learning path.
- Mark each milestone complete when its stated learning objective is met.
- Explain the fundamental concepts and important mechanisms behind each learning
  unit before assuming the learner understands them.
- Use implementation and experiments to reinforce conceptual understanding,
  rather than treating implementation itself as the learning goal.

## Setting Up A New Project

Start with this document and the new project's subject. The learner can share
specific mechanisms, questions, or constraints as they become clear.

When the goal is still broad, work it out with the learner. Offer a few concrete
directions and a small experiment for each. Ask a focused question about what
they already know, what interests them, or what they want to be able to explain
by the end. Use what they have already shared and ask about details that would
change the roadmap. Agree on an initial goal and a first observable milestone
before writing `ROADMAP.md`. Revisit the goal as the first experiments reveal new
questions.

An earlier project can serve as an optional example. Name the file or section
and the aspect to borrow, such as how a learning unit records its result or how
a README describes the scope. Carry over the requested convention and derive
the new roadmap's topics, prerequisites, and milestones from the new goal.

A reusable setup request can be as short as this.

> Set up a learning project for [subject] using `LEARNING_PROJECT.md`. Help me
> narrow the goal and agree on a small first milestone. Build `ROADMAP.md` around
> the questions we choose and the behavior we can observe to answer them.

When a reference would help, add a sentence such as this.

> Use [repository and file] as a reference for [specific convention].

Once the initial learning goal and first observable milestone are agreed upon,
initialize the project documentation.

- Update `README.md` to describe the project's purpose, learning goals,
  scope, and non-goals.
- Create `AGENTS.md` with project-specific working rules and instructions
  to follow `LEARNING_PROJECT.md`. Avoid duplicating shared guidelines.
- Create `ROADMAP.md` with the agreed learning goal, first milestone,
  planned learning themes, and optional follow-ups.

Keep these documents up to date as the project evolves.

## Project Documents

Initialize the following documents when setting up a new learning project.

- `README.md`: project purpose, learning goals, scope, non-goals, how to run
  the project, and the current achievement level.
- `AGENTS.md`: instructions for AI agents to follow `LEARNING_PROJECT.md`
  and project-specific working rules.
- `ROADMAP.md`: a living roadmap containing learning goals, planned learning
  themes, milestone status, experiment results, and open questions.

Add the following directories as needed throughout the project.

- `docs/`: topic-specific learning notes and explanations of important
  concepts and mechanisms.
- `examples/`: small executable examples that reproduce important behavior
  or comparisons.

## Roadmap Shape

A useful roadmap starts with a small observable milestone and orders later
themes by what the learner needs to understand next. Give each theme three parts.

- The question the learner wants to answer.
- The smallest implementation, experiment, or example that exposes the
  mechanism.
- An observable result that answers the question, such as behavior reproduced
  by a test, a small demo, or a focused comparison.

For example, a Virtual DOM project might ask when the renderer can reuse an
existing DOM node. Updating text inside a compatible element and checking the
node's reference demonstrates both the visible update and the reuse.

Keep a topic on the main path when it directly answers a learning question or
makes a later theme possible. Include error cases and diagnostics where they
reveal the mechanism. Rollback on an exception belongs in a transaction lesson,
for example. General error-message polish, broader edge-case coverage, and
logging can go under `Optional Follow-ups` when there is a reason to revisit
them. A follow-up can be simple or advanced. Record relevant limitations next
to the themes they affect.

## Explaining Core Concepts

Identify the fundamental concepts and important mechanisms needed to understand
each learning unit. Explain them before the learner is expected to reason about
the implementation or answer an understanding question.

When introducing an unfamiliar concept, explain the following where relevant.

- What it is and why it exists.
- How it works at a conceptual level.
- How it relates to other important concepts.
- What role it plays in the current learning unit.

Use concrete examples, comparisons, or diagrams when they help make an abstract
mechanism understandable. Explain prerequisite concepts when they are necessary
to understand the current topic.

Adapt the depth of the explanation to the learner's existing knowledge.
Avoid repeating concepts the learner has already demonstrated an understanding
of, and avoid introducing details unrelated to the current learning objective.

Connect the conceptual explanation to the implementation and observed behavior.
The learner should understand not only what the code does, but also the
mechanism that the code demonstrates.

## Explaining A Completed Learning Unit In Chat

Use the final chat response to teach the mechanism from the current unit.
Write in the learner's language and make the explanation understandable on
its own. Link to repository notes for deeper reading.

- Reconnect the result to the learning question. Say what we can now observe.
- Walk through one concrete example. Show the starting point, what the code
  does, and the result. Use a small snippet or an input and output pair when
  it helps. Explain the decision in the code that produces the behavior.
- Point to one place to start reading, such as the assertion that demonstrates
  the behavior or the branch that decides it. Explain what to look for there.
- Report verification briefly and mention a limitation when it matters to
  the example. End with one understanding question when the check is pending.

Match the depth to the unit. A small unit may need only a few paragraphs. If
the unit introduces a new mechanism, spend more of the response on how it works.

## Checking Understanding Before Moving On

At the end of a learning unit, ask the learner to explain its central mechanism
in their own words before advancing. A sentence or two about what happens and
why is enough. Ground the question in the code, test, or example from the unit.
Vary one detail from the walkthrough when that helps the learner apply the idea.
For example, after showing how a `p` stays in place when its text changes, ask
what happens to the original node if the `p` changes to a `section`, and why.
An explanation the learner already gave during the discussion counts.

Group mechanical tasks such as setup and renaming into the learning unit they
support. When part of the explanation is unclear, work through that part with
a small example and invite the learner to explain it again. A request to move
on while the check is pending is a cue to ask the question first.

Before asking an understanding question, make sure the fundamental concepts
and mechanisms needed to answer it have been explained or are already
understood by the learner.

Do not assume familiarity with unexplained technical terms or mechanisms.
If the learner struggles because of missing prerequisite knowledge, pause
the understanding check, explain the missing concepts, and revisit the question.

When the learner raises a related conceptual question, address it before
advancing to the next learning unit.

## Completion Criteria

Mark the first milestone complete when its planned behavior is observable and
the learner can explain it in their own words.
Use these criteria to decide when the main learning path is complete.

- The original learning goal has been met.
- The main internal boundaries are visible in code or examples.
- The project has tests or reproducible examples for the important behavior.
- The learner can explain the main mechanisms in their own words.
- The roadmap records what was completed and what remains optional.
- Relevant limitations are documented.

Once the main path is complete, use a specific learning question to choose any
follow-up.
