# Caio Figueiroa: lawyer and engineer

I practice law in Rio de Janeiro, and I also build and operate the software my practice runs on.
Law trained me to write for a hostile reader and to never claim what the record doesn't support.
I apply the same rule to code: measure, don't guess.

My edge is putting LLMs to work in production without letting them break things:
a fleet of AI coding agents does the typing, and a control system I designed decides what ships.

![Rio, UTC-3](https://img.shields.io/badge/Rio_de_Janeiro-UTC--3-0f766e?style=flat-square)
![Remote USD/EUR](https://img.shields.io/badge/open_to-remote_USD%2FEUR_·_freelance-2563eb?style=flat-square)
[![Email](https://img.shields.io/badge/shipsfromrio%40gmail.com-contact-6b7280?style=flat-square)](mailto:shipsfromrio@gmail.com)

## LLMs in production: what I actually run

- **An agent fleet, in parallel.** Claude Code and Codex agents work several lanes at once,
  each in its own git worktree and branch. I own the architecture, the review and the merge decision.
- **An LLM gateway** ([OmniRoute](https://github.com/diegosouzapw/OmniRoute)) with fallback combos across
  about 29 provider connections, so one outage or rate limit doesn't stop the work.
- **Determinism first.** Where plain code gives the same or a better answer, no LLM gets the job.

## How the work flows

1. Every task starts as an issue; an agent picks it up in an isolated worktree.
2. Pre-push guards run on the diff and **fail closed**: when in doubt, they refuse.
3. Adversarial review before merge. Every fix ships with a test that fails without it,
   and mutation testing where the guard matters.
4. A GitHub merge queue with required checks, on self-hosted CI:
   13 runners on 5 machines (Linux, macOS and a cloud VM), measured on 2026-09-29.
5. Anything an agent learns the hard way ends up versioned: a script, a guard or a runbook, never just chat.

The production repo is private. I'm happy to walk through the architecture and the guards live in an interview.

## Tools

![Claude Code](https://img.shields.io/badge/Claude_Code-D4A27F?style=flat-square&logo=anthropic&logoColor=white)
![Codex](https://img.shields.io/badge/Codex-412991?style=flat-square)
![MCP](https://img.shields.io/badge/MCP-111827?style=flat-square)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=flat-square&logo=powershell&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black)
![macOS](https://img.shields.io/badge/macOS-000000?style=flat-square&logo=apple&logoColor=white)

## Featured

### [homecoming](https://github.com/shipsfromrio/homecoming)

A TypeScript CLI that brings your own Claude Code sessions back into the sidebar after you switch
accounts, without moving or modifying the originals. Dry run by default, reversible, and extensible
through a small plugin API. 1,932 tests.

### [failclosed-pii-guard](https://github.com/shipsfromrio/failclosed-pii-guard)

A git pre-push hook that refuses a push carrying a Brazilian CPF or CNJ case number. It fails closed
on every doubt, never prints an unmasked value, and a mutation bench proves the tests fail when the
guard is broken (92 tests, 25 of 25 mutants killed).

## Open source: OmniRoute

[Merged pull requests](https://github.com/diegosouzapw/OmniRoute/pulls?q=is%3Apr+author%3Ashipsfromrio+is%3Amerged)
in an open source LLM gateway. Most fix a failure that didn't announce itself, and every code fix
ships with a test that fails without it.

<details>
<summary>The list</summary>

- [#14941](https://github.com/diegosouzapw/OmniRoute/pull/14941): connection test re-enabled a paid provider the user had turned off
- [#14946](https://github.com/diegosouzapw/OmniRoute/pull/14946): log export truncated with no warning
- [#14943](https://github.com/diegosouzapw/OmniRoute/pull/14943): OpenCode plugin cache wiped on timeout
- [#14942](https://github.com/diegosouzapw/OmniRoute/pull/14942): non-stream combo returned SSE
- [#14945](https://github.com/diegosouzapw/OmniRoute/pull/14945): docs for CONTEXT_LENGTH
- [#14949](https://github.com/diegosouzapw/OmniRoute/pull/14949): an open circuit breaker surfaced as a generic error, hiding the real cause
- [#14950](https://github.com/diegosouzapw/OmniRoute/pull/14950): a reserved provider prefix was rejected with a bare "Invalid request"
- [#14951](https://github.com/diegosouzapw/OmniRoute/pull/14951): the storage tab crashed with "[object Object]" instead of the API error
- [#14953](https://github.com/diegosouzapw/OmniRoute/pull/14953): self-host guide pointed to unreleased files
- [#14954](https://github.com/diegosouzapw/OmniRoute/pull/14954): Gemini's default thinking budget could eat the whole max_tokens and return empty content
- [#14955](https://github.com/diegosouzapw/OmniRoute/pull/14955): a malformed 200 was replayed on the same account after the upstream had already billed it
- [#14956](https://github.com/diegosouzapw/OmniRoute/pull/14956): responses served by the emergency fallback carried no marker of the provider swap
- [#14957](https://github.com/diegosouzapw/OmniRoute/pull/14957): rate-limit overrides left abandoned jobs in the queue and stalled it
- [#14958](https://github.com/diegosouzapw/OmniRoute/pull/14958): a search connection kept showing a stale error while it served traffic
- [#14959](https://github.com/diegosouzapw/OmniRoute/pull/14959): a 429 with a long retry hint was still retried on the same account, stretching requests

Plus [one issue comment](https://github.com/diegosouzapw/OmniRoute/issues/14931#issuecomment-5856149234)
where a tokenizer measurement refuted the issue's premise.

</details>

## What I bring

- I hunt the failure that doesn't announce itself: unwanted billing, silent truncation, a retry that bills twice
- I can judge whether a legal output is correct, and build the harness that checks it every time
- Specs, postmortems and PR bodies written for a reader looking for the gap

## Hire me

Remote (USD/EUR) or freelance. Rio, UTC-3: overlaps the US East business day and European afternoons.
I keep practicing law, and I say so up front.

Contact: **shipsfromrio@gmail.com**

<sub>aka byterj</sub>
