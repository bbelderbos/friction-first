# Plan: Go (clean slate)

A 30-day Friction-First plan for a developer learning Go from scratch. Designed to pair with `rust-known.md` as an A/B test of how prior knowledge affects learning.

---

## Starting Point

- **Language**: Go
- **Prior knowledge**: None. Has read about Go but never shipped anything in it.
- **Daily commitment**: 1 hour, alternating days with the Rust plan
- **Total horizon**: 30 sessions (15 in this track if paired A/B)

---

## Why this language

Go is intentionally simple. No classes, no inheritance, no generics until recently, no macros. Explicit error returns. Goroutines and channels as first-class concurrency. Learning Go is partly unlearning patterns from richer languages. The goal by day 30 is to write idiomatic Go: not Python translated, not Rust without lifetimes, but Go.

---

## Projects

*Three parallel projects, kept that way so this clean-slate B-track stays comparable to the Rust A-track. A solo from-scratch learner (not running A/B) should instead prefer **one project that escalates across the three phases** — see the README's setup step.*

### Project 1: CLI tool (Phase 1, no-spoiler tutor only)

- **What**: A small CLI utility. Pick something practical: a directory size analyzer, a markdown link checker, a tiny todo manager backed by a JSON file.
- **Why this scope**: Learn `flag`, `os`, `io`, error returns, struct methods, package layout. Get used to `gofmt` and the Go project conventions.
- **Done when**: Builds with `go build`, passes `go vet`, has table-driven tests, handles a real workload end-to-end.
- **Stretch**: Cross-compile for Linux/Mac/Windows.

### Project 2: HTTP service with goroutines (Phase 2, tutor + design critique)

- **What**: A small HTTP service with two or three endpoints, doing some real work in the background using goroutines.
- **Why this scope**: `net/http`, handlers, middleware, channels, `sync` package, context cancellation. The "Go way" of concurrency.
- **Done when**: Service handles concurrent requests correctly. Graceful shutdown on SIGINT. Tests use `httptest`. Race detector clean (`go test -race`).
- **Stretch**: Add a metrics endpoint or structured logging with `slog`.

### Project 3: Job queue or multi-API CLI (Phase 3, full agentic + comprehension gate)

- **What**: Either a small worker that pulls jobs off a queue and processes them with retries, or a CLI that fans out to multiple APIs concurrently and aggregates results.
- **Why this scope**: Forces composition with interfaces, real-world concurrency patterns (worker pools, fan-out/fan-in), retries with backoff, timeouts.
- **Done when**: Handles failure modes (timeouts, partial results) without losing data or hanging. Comprehension gate passed for every AI-generated block.
- **Stretch**: Package as a reusable library with a clean public API.

---

## Resources

- Official: [The Tour of Go](https://go.dev/tour/) (do this in week 1, evenings outside the hour)
- The book: [The Go Programming Language](https://www.gopl.io/) (Donovan & Kernighan) or [Learning Go](https://learning.oreilly.com/library/view/learning-go-2nd/9781098139285/) (Bodner)
- Idioms: [Effective Go](https://go.dev/doc/effective_go) and [Go Code Review Comments](https://go.dev/wiki/CodeReviewComments)

Three references. No more.

---

## Calendar

| Days | Phase | Project | AI mode |
|---|---|---|---|
| 1–10 | 1 | CLI tool | No-Spoiler Tutor only |
| 11–20 | 2 | HTTP service with goroutines | Tutor + design critique |
| 21–30 | 3 | Job queue or multi-API CLI | Full agentic + comprehension gate |

If running paired A/B with the Rust plan, alternate days within each block.

---

## Definition of Done

- 30 friction-log entries in `logs/`
- All three projects build, pass `go vet`, pass `go test -race`
- A `retro.md` answering: how much did your existing instincts help vs mislead, what felt genuinely new, where AI hurt vs helped per phase

---

## Things specific to Go to watch for

- **Resist translating from Python or Rust.** When you reach for a pattern that "should" exist (decorators, classes, generics-heavy code, Result types), stop and check what the idiomatic Go solution is. Often it's simpler than you expect.
- **Error returns are the language, not boilerplate.** If you find yourself wishing for `?`, that's a signal to pause. The explicitness is the point: it forces you to think about every failure path.
- **Goroutines without channels are usually wrong.** If your Phase 2 design includes goroutines and shared mutable state via `sync.Mutex`, ask the tutor whether a channel-based redesign would be cleaner first.
- **`interface{}` and `any` are smells in beginner code.** Phase 1 and 2: avoid them entirely. Phase 3: only with the comprehension gate explicitly justifying why.
