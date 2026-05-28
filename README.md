# Friction-First Learning

A 30-day deliberate practice template for learning (or relearning) a programming language without succumbing to AI-induced skill atrophy.

> "Surface correctness is not systemic correctness. To resist surrender, we have to build friction and calibration into our workflows." — Addy Osmani

This repo is a fork-and-fill scaffolding. It gives you the methodology, the prompts, the daily templates, and two worked examples. You bring the language, the projects, and the discipline.

Background reading: [Don't Delegate the Friction](https://belderbos.dev/blog/dont-delegate-the-friction/).

---

## The Premise

The danger of AI-assisted coding isn't AI itself. It's **spoilers**.

Google delivers spoilers (Stack Overflow copy-paste). Blog posts deliver spoilers (full working code). Copilot delivers spoilers (auto-completing the next decision). Claude and ChatGPT deliver spoilers (generating the whole function).

Every spoiler shortcuts the loop where skills actually form: load working memory, form a hypothesis, test it, get feedback, update the mental model. Skip that loop often enough and the muscle atrophies.

The fix is not "no AI". The fix is engineered friction. Use AI as a Socratic tutor that refuses to give you the answer. Write your design before you prompt. Type every character yourself, at least in the early phases. Log what surprises you and where you almost cheated.

---

## The Method

Three phases, each with escalating AI assistance. Test for yourself where on the spectrum your skills compound versus erode.

| Phase | Duration | AI mode | What's allowed |
|---|---|---|---|
| **1. Foundations** | ~10 hrs | No-Spoiler Tutor | Socratic AI tutor that refuses to write code. Official docs. The book. You type every character. No Copilot autocomplete. |
| **2. Rubber Duck** | ~10 hrs | Tutor + design critique | AI explains concepts and critiques your design. Still no code generation, no autocomplete. You write the code. |
| **3. Real-World Gated** | ~10 hrs | Full agentic | AI may generate code. Every block passes a comprehension gate. Design doc written before prompting. |

The variable being tested is **how much code AI writes for you**. That is the actual driver of skill atrophy.

---

## Repo Layout

```
README.md                         # this file
plans/
  rust-known.md                   # worked example: Rust, basics already known
  go-new.md                       # worked example: Go, clean slate
  _template.md                    # blank plan to fork for any language
templates/
  daily-log.md                    # friction log template, one per session
  design-intent.md                # design-intent prompt, written before coding
prompts/
  no-spoiler-tutor.md             # system prompt for the Socratic AI tutor
  comprehension-gate.md           # the 4-question gate for Phase 3
```

---

## How to Use This Repo

1. **Fork or copy** this repo into your own workspace.
2. **Pick a language and three projects.** Copy `plans/_template.md` to `plans/my-plan.md` and fill it in. The two worked examples show the shape.
3. **Set up the No-Spoiler Tutor** as a dedicated Claude or ChatGPT instance using `prompts/no-spoiler-tutor.md`. Bookmark it. Do not use a general-purpose chat for Phase 1.
4. **Open a `logs/` folder** in your fork. Each session gets a dated log file based on `templates/daily-log.md`.
5. **Day 1**: write your design intent in `templates/design-intent.md`, open the official docs for your language, and start. No agent. No autocomplete.
6. **Stick to the protocol** for each phase. The system prompt does most of the enforcement; your job is to not switch tabs.

---

## What Guarantees Skill Compound

- The **no-AI-code-generation baseline** in Phase 1. Non-negotiable.
- **Writing design intent before code**, every session.
- **The daily friction log.** Forces meta-cognition.
- **No autocomplete acceptance** in Phases 1 and 2. One "tab to accept" steals a decision.
- **The comprehension gate** in Phase 3. If you can't explain it, it doesn't ship.

---

## A/B Variant

If you want to test how prior knowledge affects pace, run two tracks in parallel:

- **Track A**: a language you already know basics of
- **Track B**: a clean-slate language

Same phase protocol, alternate days. By day 30 you'll know how much your existing mental models actually transfer, and where pure language fluency has to be rebuilt from scratch.

The two worked examples (`plans/rust-known.md`, `plans/go-new.md`) are a paired set if you want to run them as the canonical A/B.

---

## License & Attribution

MIT. Built by [Bob Belderbos](https://belderbos.dev) as a companion to coaching work on deliberate AI-era learning.
