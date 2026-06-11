# Friction-First Learning

---
**Note**: this is an experimental template repo. I'm going to use it to learn or refresh one skill during 30-60 min a day, then debrief on [my blog](https://belderbos.dev) on whether the methodology delivers.

The method is about using AI to _force_ deliberate practice instead of shortcutting it; the template is the scaffold for that practice. (A language I'm relearning in parallel, I'm doing by immersion — forcing all my regular work into it — which is a different kind of effort than this deliberate-practice loop.)

How I came to this idea? Read [Don't Delegate the Friction](https://belderbos.dev/blog/dont-delegate-the-friction/).

If you prefer to do self-contained exercises instead of projects, check out the Pybites platforms: [Python](https://pybitesplatform.com) and [Rust](https://rustplatform.com). They have a similar philosophy of forcing you to write code yourself, without embedded AI to spoil the learning.

---

A 30-day deliberate practice template for learning (or relearning) a skill without succumbing to AI-induced atrophy. The worked examples use programming languages, but the method fits any craft where AI can hand you the answer (see [Beyond Languages](#beyond-languages)).

> "Surface correctness is not systemic correctness. To resist surrender, we have to build friction and calibration into our workflows." — Addy Osmani

This repo is a fork-and-fill scaffolding. It gives you the methodology, the prompts, the daily templates, and two worked examples. You bring the skill, the projects, and the discipline.

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

1. **Fork or copy** this repo into your own workspace. Your fork is where your progress lives — commit to it daily.
2. **Pick one language and three projects.** Copy `plans/_template.md` to `plans/my-plan.md` and fill it in. The two worked examples (`plans/rust-known.md`, `plans/go-new.md`) show the shape — one for a language you half-know, one for a clean slate.
3. **Set up the No-Spoiler Tutor as a Claude Project** (see the next section). This is the core of the method — do not skip it or substitute a general-purpose chat.
4. **Day 1**: write your design intent in `templates/design-intent.md`, open the official docs for your language, and start. No agent. No autocomplete. You type every character.
5. **Each session**: add a dated log file in `logs/` based on `templates/daily-log.md`. The friction log is the actual deliverable — protect it over finishing projects.
6. **Stick to the phase protocol.** The system prompt does most of the enforcement; your job is to not switch tabs.

---

## Setting Up the No-Spoiler Tutor (Claude Project)

The tutor is not a prompt you paste into every chat — it's a **persistent Claude Project** that governs every conversation inside it. That persistence is the point: a general-purpose chat loses the discipline within a session.

1. In Claude, go to **Projects → Create project**. Name it e.g. `Friction-First: <LANG>`.
2. Open the project's **instructions** (custom instructions) and paste the full prompt from `prompts/no-spoiler-tutor.md`. Replace `<LANG>` with your language.
3. Optionally add your `plans/my-plan.md` to the project's knowledge so the tutor has context on your projects and current phase.
4. **Start every Phase 1–2 session as a new chat inside this project.** The instructions apply automatically — the guardrails don't evaporate between sessions.
5. **Phase 3 only**: do code generation in a separate agentic tool (Claude Code, Cursor), then bring each generated block back to _this_ project and run it through `prompts/comprehension-gate.md`. Keep the tutor and the code generator in different windows on purpose.

(ChatGPT equivalent: a **Custom GPT** with the same text as its system instructions. Same idea — persistent instructions, not a per-message paste.)

---

## How Persistence Works

Two separate things persist, in two separate places:

- **The tutor's behavior** persists in the **Claude Project** (or Custom GPT). You configure it once; it applies to every chat in that project. There's no automated loop or memory injection — the Project config _is_ the persistence.
- **Your progress** persists in your **git fork**: `plans/my-plan.md`, the dated files in `logs/`, and your final `retro.md`. Commit them daily. This is your real state — the friction log becomes a precise map of where AI taught you versus where it papered over a gap.

The template itself does nothing at runtime. It ships a methodology, prompts, templates, and worked examples. The discipline is yours; the scaffold just makes it harder to cheat.

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

## Beyond Languages

The worked examples here are programming languages, but nothing about the method is. The premise — that _spoilers_ shortcut the loop where skill forms — holds for any craft where AI can hand you a finished artifact and a feedback signal exists to struggle against: **writing, math, design, a human language**. Skills that are purely motor or perceptual (sport, drawing, music) fit poorly, because there's no copy-pasteable spoiler to resist.

To re-skin the scaffold for a non-code skill, swap the code-specific pieces for domain equivalents:

| Code version | Generic version |
|---|---|
| Type every character, no autocomplete | Write the draft yourself, no AI sentences |
| "The compiler is the better tutor" | Your own feedback signal (an editor, a proof checker, a critic) |
| Comprehension gate: _could I rewrite this block equivalently?_ | _Could I reproduce this paragraph / proof / argument from scratch?_ |
| Phases keyed to _how much code AI writes_ | Phases keyed to _how much of the artifact AI produces_ |

The no-spoiler tutor prompt, the phase structure, the design-intent-before-doing rule, and the friction log all carry over unchanged.

---

## License & Attribution

MIT. Built by [Bob Belderbos](https://belderbos.dev) as a companion to coaching work on deliberate AI-era learning.
