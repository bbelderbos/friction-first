# Friction-First Speedrun (90 minutes)

The full plan is 30 sessions because the *experiment* — measuring where AI help compounds skill versus erodes it — needs that long. The *method* doesn't. This is the method in one sitting: all three phases once, on one throwaway task, so you can feel the loop before committing a month to it.

Not a substitute for the real plan. A test drive.

## Pick a task

Something small enough to finish, just unfamiliar enough to struggle. A good default: **a CLI that reads a text file and prints the N most common words**, in a language you half-know — or a cold one for a more honest "new skill" run. Any tiny kata works: a temperature converter, a JSON pretty-printer, FizzBuzz with a twist.

One rule: pick something you can't already type from memory. The struggle is the product.

## Before you start (2 minutes)

- Set up the No-Spoiler Tutor: paste `prompts/no-spoiler-tutor.md` into a fresh Claude Project (or ChatGPT custom GPT) and replace `<LANG>`. For a 90-minute taster, a single fresh chat with that prompt pasted as the first message is also fine — just don't reuse a chat that's been writing code for you.
- Keep `templates/daily-log.md` open; you'll append to it after each phase.

## The 90 minutes

| Time | Phase | AI mode | What you do |
|---|---|---|---|
| 0:00–0:10 | **Setup** | — | Toolchain `--version`, compile a hello world. Skip if already installed. |
| 0:10–0:40 | **1 · Foundations** | No-Spoiler Tutor | Build the smallest slice by hand (read file → print lines). Tutor gives hints only. You type every character. |
| 0:40–1:05 | **2 · Rubber Duck** | Tutor + design critique | Spend 5 min on design intent for the next slice (count + sort). Tutor critiques it. Then you write it. |
| 1:05–1:30 | **3 · Real-World Gated** | Full agentic | Let AI generate *one* block (the top-N sort). Run it through the comprehension gate (`prompts/comprehension-gate.md`). Accept or rewrite. |

Set a timer per block. When it rings, move on even if unfinished — finishing the task is not the goal.

## What you log

After each phase, 3–4 honest lines in a `logs/` entry (copy `templates/daily-log.md`):

- **What you built** — one line.
- **Friction** — what surprised you, what you looked up, and *where you almost cheated* (asked for the answer instead of a hint, pasted something unread, accepted an autocomplete). The almost-cheated line is the one that matters.

Then a 3-line retro at the end:

- Where did the friction feel productive versus just slow?
- Where did AI teach you something versus paper over a gap?
- Would you run the full 30 after this?

That retro — not the word counter — is what you take to the article, the talk, or the next month.

## Then what

Liked the loop? Fork properly and run the real thing: start from `plans/_template.md` (or have AI draft it with `prompts/plan-bootstrap.md`), pick one project that escalates across the three phases, and follow the [README](README.md).
