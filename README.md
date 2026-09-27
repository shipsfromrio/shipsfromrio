# Caio Figueiroa: lawyer and engineer

I practice law in Rio de Janeiro, and I also build and operate the software my practice runs on.
Law trained me to write for a hostile reader and to never claim what the record doesn't support.
I apply the same rule to code: measure, don't guess.

## How it's built (said once, plainly)

I orchestrate a fleet of AI coding agents (Claude, Codex). I don't type most of the code.
My job is the part agents can't do alone: architecture, the guards, adversarial review,
and deciding what merges. The control system around them:

- GitHub merge queue; pre-push guards that fail closed (when in doubt, refuse)
- Adversarial review before merge; every fix needs a test that fails without it
- House rule: where deterministic code gives the same or a better answer, no LLM gets the job

## Measured on 2026-09-27 (private repo, first commit 2026-07-04)

- 5,995 commits on main (squash merge), 3,483 merged PRs, 3,636 issues
- 1,478 test files
- About 41 merged PRs/day. That cadence exists because of the agents;
  the guards are why it's safe to keep.
- Also in production: an LLM gateway (OmniRoute) with ~29 provider connections and fallback combos

The repo is private. I'm happy to walk through the architecture and the guards live in an interview.

## Open source: OmniRoute (open PRs, opened 2026-09-27, none merged yet)

Each one is a silent failure with a real cost, and each ships with a test that fails without the fix:

- [#14941](https://github.com/diegosouzapw/OmniRoute/pull/14941): connection test re-enabled a paid provider the user had turned off
- [#14946](https://github.com/diegosouzapw/OmniRoute/pull/14946): log export truncated with no warning
- [#14943](https://github.com/diegosouzapw/OmniRoute/pull/14943): OpenCode plugin cache wiped on timeout
- [#14942](https://github.com/diegosouzapw/OmniRoute/pull/14942): non-stream combo returned SSE
- [#14945](https://github.com/diegosouzapw/OmniRoute/pull/14945): docs for CONTEXT_LENGTH
- [#14949](https://github.com/diegosouzapw/OmniRoute/pull/14949): an open circuit breaker surfaced as a generic error, hiding the real cause
- [#14950](https://github.com/diegosouzapw/OmniRoute/pull/14950): a reserved provider prefix was rejected with a bare "Invalid request"
- [#14951](https://github.com/diegosouzapw/OmniRoute/pull/14951): the storage tab crashed with "[object Object]" instead of the API error
- [#14952](https://github.com/diegosouzapw/OmniRoute/pull/14952): setup-claude wrote profiles for providers the host cannot run
- [#14953](https://github.com/diegosouzapw/OmniRoute/pull/14953): self-host guide pointed to unreleased files

Plus [one issue comment](https://github.com/diegosouzapw/OmniRoute/issues/14931#issuecomment-5856149234) where a tokenizer measurement refuted the issue's premise.

## What I bring

- I hunt the failure that doesn't announce itself (unwanted billing, silent truncation)
- I can judge whether a legal output is correct, and build the harness that checks it every time
- Specs, postmortems and PR bodies written for a reader looking for the gap

## Hire me

Remote (USD/EUR) or freelance. Rio, UTC-3: overlaps the US East business day and European afternoons.
I keep practicing law, and I say so up front.

Contact: **shipsfromrio@gmail.com**

<sub>aka byterj</sub>
