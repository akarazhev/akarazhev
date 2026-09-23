## Andrey Karazhev

Data engineering: backend and distributed systems, 19 years. I work on data in
motion — parsing and normalising what arrives from other systems, moving it,
reconciling what does not match, and the analytics built on top. Java, Python, Go.

Most of what I publish is about the quiet failures — duplicates, gaps, stale
values, order and reprocessing. They produce no errors in the log and surface
weeks later as a wrong number.

### Diagnoses in other people's code

Reading unfamiliar code until the mechanism is named, with line references and,
where possible, a test that shows it.

**[numaflow#3645](https://github.com/numaproj/numaflow/issues/3645)** — an
accumulator watermark that never advances when a key keeps receiving data and the
function emits nothing for it. Verified with a local test against the Rust core.
The team revisited the design, kept the behaviour as intended and restored the
drop API in four SDKs; the documentation fix is merged in
[#3660](https://github.com/numaproj/numaflow/pull/3660).

**[nats-server#8607](https://github.com/nats-io/nats-server/issues/8607)** — why
adding a stream source scans the whole stream, what `opt_start_time` actually
applies to, and what does bound the scan. Checked against the reporter's own
version rather than `main`.

**[ccxt#26773](https://github.com/ccxt/ccxt/issues/26773)** — a balance update
lost rather than delayed, because `deepExtend` builds a new object.

**[Lean#9790](https://github.com/QuantConnect/Lean/issues/9790)** — three of
eight `Send` calls run off the result thread.

### Surveys, with their collectors and raw data

**[What breaks in price feeds](https://github.com/akarazhev/price-feed-failure-survey)** —
1,163 commits matching six feed-failure terms across 48 crypto organisations,
and how the vocabulary differs between publishing a feed and consuming one. A
hand check of 100 diffs found about one in six is an actual repair; the
correction and every classification are in the repository.

**[What DAOs actually fund](https://github.com/akarazhev/dao-funding-survey)** —
93 funding proposals across 29 governance forums: what gets funded, for how much,
and through which channel. `analyse.py` reproduces the dataset byte for byte.

### Before that

**[crypto-scout](https://github.com/akarazhev/crypto-scout)** — event-driven
services that ingest market and on-chain events: collector, queue, analyst,
TimescaleDB.

**[metacfg4j](https://github.com/akarazhev/metacfg4j)** — a configuration library
with a business abstraction over CRUD services, a DSL and an MVP.

### How I work

I write the method down next to the result. If a number is published here, the
code that produced it and the data it ran on are published with it — a
disagreement should be with a rule you can read, not a figure you have to
believe.

Limits go in before conclusions, not in a footnote.

---

[minihub.app](https://minihub.app) · [hello@minihub.app](mailto:hello@minihub.app)
