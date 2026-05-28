# The Comprehension Gate

A four-question gate every AI-generated code block must pass before it gets merged. Use this in Phase 3, when full agentic assistance is allowed.

The gate is the difference between AI-accelerated learning and AI-driven skill atrophy.

## The Four Questions

Run these against every block of code an AI agent produced for you, before committing.

### 1. Can I describe what this code does without reading it line-by-line?

Close the file. Out loud or in writing, explain what the function (or struct, or module) does in two sentences. If you have to peek, the understanding isn't there yet.

### 2. Can I explain *why* this approach was chosen over alternatives?

Most non-trivial code makes design choices: a `HashMap` vs a `BTreeMap`, a goroutine vs a channel-based handoff, recursion vs iteration, an interface vs a concrete type. Why this one? What does the alternative cost?

If you can't answer, you have a learning opportunity right there. Ask the no-spoiler tutor (not the agent that wrote it) what the tradeoffs are.

### 3. If I deleted this block and rewrote it from scratch, would I produce something equivalent?

Not character-identical. Equivalent in shape, intent, and correctness. If the answer is no, the AI taught you nothing here, it just shipped code on your behalf.

### 4. Are there parts I'd flag to a code reviewer as "I'm not sure about this"?

If yes, flag them. To yourself, in the friction log. To the tutor as the next session's question. To a real human reviewer if you have one.

Pretending to understand the parts you don't is the fastest path to skill atrophy. Honest flagging is the antidote.

---

## Decision

| Result | Action |
|---|---|
| All four pass | Merge. Commit. Move on. |
| Any one fails | Do not merge yet. Use the tutor to bridge the gap. Re-evaluate after. |
| Multiple fail | Throw away the block. Write your own version, slower, with the tutor's help. The AI did too much. |

The third option feels expensive. It is. It is also the only way to keep the trend line on skill going up.

---

## Friction log entry

When you run the gate, log it. In your daily log:

```
## Comprehension gate — <file>:<lines>
- Q1: pass | fail (why)
- Q2: pass | fail (why)
- Q3: pass | fail (why)
- Q4: pass | fail — flagged: <list>

Action: <merged | deferred | rewrote>
```

Over 10 sessions in Phase 3, these entries become a precise map of where AI is teaching you and where it's papering over gaps. That map is worth more than the projects themselves.
