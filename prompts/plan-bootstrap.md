# The Plan Bootstrap — One-Time Setup Prompt

Use this **once**, before Phase 1, to turn "I want to learn `<LANG>`" into a filled-in `plans/my-plan.md`. This is the one place AI is *allowed* to do the work for you — picking and scoping projects is meta-work, not the skill you're building. (Contrast `no-spoiler-tutor.md`, which refuses to help the moment you start coding.)

Run it in any general chat or agent. Answer its questions, read the output critically, commit it.

## The prompt

```
You are helping a developer scaffold a Friction-First learning plan for <LANG>.

First, ask in one message:
- Prior experience with <LANG>: none | basics | intermediate
- Daily commitment and total horizon (e.g. 30 min, 20 sessions)
- A domain they're drawn to (CLIs, parsing, web, games, data...)

Then choose the project count by experience — fewer is better when new:
- none: ONE project that escalates across all three phases (build the
  foundation by hand in Phase 1, add architecture under design critique in
  Phase 2, integrate real-world concerns under the comprehension gate in
  Phase 3). One maturing codebase builds deeper instinct than three cold
  starts, and it keeps the experiment clean: the only variable changing is
  how much code AI writes.
- basics: 2 projects.
- intermediate: 2-3 projects of increasing complexity.

Mirror the section structure of plans/_template.md — for each project (or each
phase, if it's one escalating project): What / Why this scope / Done when /
Milestones / Stretch. plans/rust-known.md and plans/go-new.md show the level of
filled-in detail to aim for. The scope must force the language's signature
concepts — name them for <LANG>.

For each, add a Milestone map using the mind-map scoping method
(belderbos.dev/blog/mind-map-software-project-scope):
- Sketch the user journey: 4-6 stages, first use to done.
- Draw the MVP boundary: which stages are "Done when", which are Stretch.
- Drill each MVP stage until every leaf is issue/PR-sized — something the
  learner could finish and test in one short session.
- Output the leaves as an ordered list. This is the spine; the learner still
  scopes each session toward the next leaf themselves.

Finally, stamp blank log files logs/01.md ... logs/NN.md (N = total sessions),
each copying templates/daily-log.md with only the header filled (sequence,
project, session number) and the body left empty.

Do NOT write any <LANG> code. The plan and the milestone leaves are prose.
```

## After running it

- Read the projects critically — swap any that don't excite you. Motivation is what carries you past Day 17.
- The milestone map is a guide, not a contract. Expect to redraw it as you learn the language.
- Commit `plans/my-plan.md` and the blank logs. Then open `no-spoiler-tutor.md` and start Phase 1.
