### Lawyer turned engineer. Ships from Rio, on your timezone.

I build and run production systems alone, end to end, and I fix bugs in the open source tools I depend on.

---

#### The short story

I'm a lawyer in Brazil. My practice needed software nobody sold, so I wrote it, and kept going.
Today I build and operate, by myself, the production stack behind a working law office:

- **A CRM in daily production use**: case tracking, deadlines, client messaging, document intake.
- **CI with a merge queue**: required checks, serialized merges, guards that fail closed. Tens of
  thousands of commits, reviewed and merged through that pipeline.
- **An LLM gateway with ~29 providers**: OpenAI-compatible routing, combo fallbacks, per-provider
  quota handling, so one outage or rate limit never stops the work.

Nobody hands me tickets. I decide what to build, measure whether it worked, and carry the pager.

#### What I ship

- **LLM gateways and routing**: OpenAI-compatible APIs, provider fallback chains, streaming,
  retries, cost and quota control.
- **TypeScript and Python automation**: backends, integrations, scrapers, scheduled jobs, CLIs.
- **CI and developer tooling**: merge queues, pre-push guards, test harnesses that actually catch
  the broken implementation.
- **Production bug fixing in open source**: reproduce, write the failing test, fix, upstream it.

#### Open source

I contribute to **OmniRoute**, an OpenAI-compatible LLM router. Every fix starts from a bug I hit in
production and ships with a test that fails without it.

<!-- PRS -->
- [#14941](https://github.com/diegosouzapw/OmniRoute/pull/14941) connection test no longer re-enables operator-disabled (paid) connections
- [#14942](https://github.com/diegosouzapw/OmniRoute/pull/14942) non-stream requests to chaos combos return JSON, not SSE
- [#14943](https://github.com/diegosouzapw/OmniRoute/pull/14943) OpenCode plugin keeps its model cache when a sync fetch fails
<!-- /PRS -->

#### Hire me

- **Remote full-time**, paid in USD or EUR. Brazil time (UTC-3) overlaps the US East Coast workday
  and the European afternoon.
- **Freelance**: LLM gateway setup, fallback routing, CI and automation, bug hunts in your stack.

Email **shipsfromrio@gmail.com**. If my public work has already saved you time, you can buy me a
coffee on [Ko-fi](https://ko-fi.com/shipsfromrio).

<sub>aka byterj</sub>
