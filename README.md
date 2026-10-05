## Andrey Karazhev

Data integration and reconciliation, including data written by automation and
AI: I find why it quietly goes wrong. Nineteen years of backend and data systems.
I work on data in motion — parsing and normalising what arrives from other
systems, moving it, reconciling what does not match, and the analytics built on
top. Java, Python, Go, SQL.

Most of what I publish is about the quiet failures — duplicates, gaps, stale
values, order and reprocessing. They produce no errors in the log and surface
weeks later as a wrong number. Automation and AI now write into accounting
systems too — invoices read from PDFs, documents recognised from scans — and
they make the same mistakes, only faster.

### Fixes and diagnoses in other people's code

Reading unfamiliar code until the mechanism is named, with line references and,
where possible, a test that shows it.

**[nats-server#8661](https://github.com/nats-io/nats-server/issues/8661)** — when
`max_ack_pending` was not set, a configuration reload left open MQTT sessions with
a limit of zero, and QoS 1 and 2 delivery stopped. The fix and a regression test
were merged in [#8671](https://github.com/nats-io/nats-server/pull/8671) less than
two hours after it was opened.

**[numaflow#3645](https://github.com/numaproj/numaflow/issues/3645)** — an
accumulator watermark that never advances when a key keeps receiving data and the
function emits nothing for it. Verified with a local test against the Rust core.
The team revisited the design, kept the behaviour as intended and restored the
drop API in four SDKs; the documentation fix is merged in
[#3660](https://github.com/numaproj/numaflow/pull/3660).

**[nats-server#8687](https://github.com/nats-io/nats-server/issues/8687)** — a
stalled stream restore returned before the restore had stopped and without the
completion advisory other failed restores send. The change and a test are
approved by a maintainer in [#8691](https://github.com/nats-io/nats-server/pull/8691)
and wait to be merged.

**[nats-server#8607](https://github.com/nats-io/nats-server/issues/8607)** — why
adding a stream source scans the whole stream, what `opt_start_time` actually
applies to, and what does bound the scan. Checked against the reporter's own
version rather than `main`.

**[ccxt#26773](https://github.com/ccxt/ccxt/issues/26773)** — a balance update
lost rather than delayed, because `deepExtend` builds a new object.

**[Lean#9790](https://github.com/QuantConnect/Lean/issues/9790)** — three of
eight `Send` calls run off the result thread.

**[OCA/queue#996](https://github.com/OCA/queue/issues/996)** — an Odoo job
recorded under the `__name__` of the function it found, not the name it was
asked for. When a module installs a replacement under another name, as auditlog
does for `write` and `unlink`, the job fails the moment it runs. The name was
lost in four places; the fix and three tests are in
[#998](https://github.com/OCA/queue/pull/998).

**[OCA/edi#1423](https://github.com/OCA/edi/issues/1423#issuecomment-5995142801)** —
Odoo's PDF invoice import dropped a total printed with one decimal and turned an
integer into hundredths, without an error. Checked by running the conversion
against the module's own test cases and sample invoice: the proposed fix changes
none of them, while making the decimals optional would let a fragment of the VAT
number beat any smaller total under the `max` rule.

<a href="https://github.com/OCA/queue/pull/998"><img src="oca-contributor.png" alt="OCA Contributor" width="120"></a>

### Writing

**[A watermark that wouldn't move](https://dev.to/akarazhev/why-a-numaflow-watermark-wouldnt-move-287m)** —
the numaflow case above, step by step: following a state clean-up condition
through the code and checking it with a test.

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

As an independent contractor I worked directly for telecom companies in
Slovenia — Iskratel and RC IKT — remotely, with acceptance testing on
the client's own equipment.

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
