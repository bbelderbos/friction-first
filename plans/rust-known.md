# Plan: Rust (basics known)

A 30-day Friction-First plan for a developer who knows Rust basics (syntax, ownership at a surface level, simple programs) and wants to build durable intuition for lifetimes, traits, async, and architecture.

---

## Starting Point

- **Language**: Rust
- **Prior knowledge**: Basics. Can write small programs. Still fights the borrow checker. Limited exposure to async, traits, lifetimes in anger.
- **Daily commitment**: 1 hour, alternating days with the Go plan
- **Total horizon**: 30 sessions (15 in this track if paired with Go A/B)

---

## Why this language

Rust forces a different kind of thinking than dynamic languages: explicit lifetimes, exhaustive error handling, no garbage collector to paper over decisions. Building intuition here strengthens systems thinking that pays back in every other language. The goal by day 30 is to read Rust idiomatically and write small programs without fighting the compiler every line.

---

## Projects

### Project 1: CLI text/file processor (Phase 1, no-spoiler tutor only)

- **What**: A small `grep`-like or log-parser CLI. Reads from a file or stdin, filters, formats, writes to stdout.
- **Why this scope**: Forces ownership and borrowing under real conditions. String slicing, `&str` vs `String`, iterator chains, basic error handling with `Result` and `?`.
- **Done when**: Handles three real input files end-to-end. Has unit tests. Compiles without warnings under `cargo clippy -- -D warnings`.
- **Stretch**: Add a `--count` mode and a `--invert-match` flag without growing the file beyond 200 lines.

### Project 2: Concurrent HTTP scraper (Phase 2, tutor + design critique)

- **What**: A CLI that fetches a list of URLs concurrently, parses something out of each response, writes results to a file.
- **Why this scope**: Introduces async/await with `tokio`, channels (`mpsc`), proper error propagation across `.await` boundaries, and structured concurrency.
- **Done when**: Fetches 50 URLs concurrently with a configurable concurrency limit. Handles timeouts and HTTP errors without panicking. Tests use a local test server or mock.
- **Stretch**: Add rate limiting and graceful shutdown on Ctrl-C.

### Project 3: Small TUI or hand-rolled mini-parser (Phase 3, full agentic + comprehension gate)

- **What**: Either a `ratatui`-based TUI for browsing local files or logs, or a recursive-descent parser for a small DSL (e.g. a config language).
- **Why this scope**: Forces architecture decisions: traits and module boundaries, lifetime annotations on real structs, generics, the visitor pattern or state machines.
- **Done when**: Three-module minimum, public API has rustdoc comments, integration tests exercise the full flow, comprehension gate passed for every AI-generated block.
- **Stretch**: Publish as a crate to crates.io (private or public).

---

## Resources

- Official: [The Rust Book](https://doc.rust-lang.org/book/)
- For Phase 2: [Tokio tutorial](https://tokio.rs/tokio/tutorial)
- One idioms reference: [Rust by Example](https://doc.rust-lang.org/rust-by-example/)

That's it. Resist the temptation to bookmark twenty more.

---

## Calendar

| Days | Phase | Project | AI mode |
|---|---|---|---|
| 1–10 | 1 | CLI text/file processor | No-Spoiler Tutor only |
| 11–20 | 2 | Concurrent HTTP scraper | Tutor + design critique |
| 21–30 | 3 | TUI or mini-parser | Full agentic + comprehension gate |

If running paired A/B with the Go plan, alternate days within each block. Five sessions per project per track.

---

## Definition of Done

- 30 friction-log entries in `logs/`
- All three projects compile, pass `cargo clippy -- -D warnings`, pass `cargo test`
- A `retro.md` covering what changed in your relationship to the borrow checker, where AI hurt vs helped per phase, what you'd cut from the protocol next time

---

## Things specific to Rust to watch for

- **Don't ask the tutor to "fix the borrow checker."** Ask what the compiler error is actually telling you about lifetimes. The compiler is the better tutor here; the AI tutor's job is to translate the message, not bypass it.
- **Resist `clone()` as a coping mechanism.** When you reach for `clone()`, log it in the friction log. Was it the right call or a shortcut around understanding ownership?
- **Phase 3 trap**: `cargo` and crate culture make it easy to pull in a dependency for everything. The comprehension gate applies to dependency choices too. If you can't explain what `serde_json` does under the hood at a sketch level, you don't get to use it on autopilot.
