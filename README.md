## Andrey Karazhev

I work on data that moves between systems: integration, migration and data quality. Most of my time goes into
finding why numbers stop matching after a load, an import or a migration, and into checks that catch it the next
time. Nineteen years of backend and data systems; SQL, Python, Java, Go.

### Demo

**[Money reconciliation demo](https://reconciliation.minihub.app)**: three made-up companies (a Stripe web shop, an
Ozon seller and a Wildberries seller) whose books, payouts and bank are reconciled to the cent in SQL. The Stripe
shop also closes [a second month](https://reconciliation.minihub.app/stripe/october/), where September's open
items carry into October.
[Code](https://github.com/akarazhev/reconciliation-demo) · write-ups:
[September](https://dev.to/akarazhev/why-stripe-payouts-dont-match-your-books-3aoa),
[October](https://dev.to/akarazhev/stripe-reconciliation-carrying-september-into-october-2743)

### Fixes in other people's code

- **[nats-server#8671](https://github.com/nats-io/nats-server/pull/8671)**: a config reload quietly stopped MQTT
  delivery. Merged less than two hours after I opened it.
- **[factur-x#96](https://github.com/akretion/factur-x/pull/96)**: the wrong exception on Belgian e-invoices. Merged
  within about an hour, released in 7.7.
- **[numaflow#3660](https://github.com/numaproj/numaflow/pull/3660)**: why a watermark stopped moving; the team kept
  the design and merged my docs fix.
  [Write-up](https://dev.to/akarazhev/why-a-numaflow-watermark-wouldnt-move-287m)
- **[nats-server#8691](https://github.com/nats-io/nats-server/pull/8691)**: a stalled stream restore now reports like
  other failed restores. Merged.
- **[airflow#75425](https://github.com/apache/airflow/pull/75425)**: the Snowflake hook lost its transaction when
  session parameters were set. Merged less than two hours after I opened it.
- **[OCA/queue#998](https://github.com/OCA/queue/pull/998)**: Odoo jobs lost the name of the method they were asked
  to run. Merged.
- **[OCA/edi#1423](https://github.com/OCA/edi/issues/1423#issuecomment-5995142801)**: Odoo's PDF invoice import
  silently dropped some amounts; checked against the module's own test invoices.
- **[erpnext#62390](https://github.com/frappe/erpnext/issues/62390)**: an asset created from a purchase receipt could
  be submitted at any value; the fix and a test are on a branch linked in the issue.

More diagnoses: [dbt#16807](https://github.com/dbt-labs/dbt/issues/16807#issuecomment-6289878718),
[pulsar#27019](https://github.com/apache/pulsar/issues/27019#issuecomment-6317931666),
[seatunnel#12934](https://github.com/apache/seatunnel/issues/12934#issuecomment-6336562059),
[nats-server#8781](https://github.com/nats-io/nats-server/issues/8781#issuecomment-6289932435),
[nats-server#8607](https://github.com/nats-io/nats-server/issues/8607),
[ccxt#26773](https://github.com/ccxt/ccxt/issues/26773), [Lean#9790](https://github.com/QuantConnect/Lean/issues/9790),
[nautilus_trader#5332](https://github.com/nautechsystems/nautilus_trader/issues/5332#issuecomment-6186486735).

<a href="https://github.com/OCA/queue/pull/998"><img src="oca-contributor.png" alt="OCA Contributor" width="120"></a>

### Surveys

- **[What breaks in price feeds](https://github.com/akarazhev/price-feed-failure-survey)**: 1,163 commits across 48
  crypto organisations; a hand check found that about one in six is a real repair.
- **[What DAOs actually fund](https://github.com/akarazhev/dao-funding-survey)**: 93 funding proposals across 29
  governance forums.

### Earlier

As an independent contractor I worked directly for Iskratel and RC IKT in Slovenia. Older projects:
[crypto-scout](https://github.com/akarazhev/crypto-scout), [metacfg4j](https://github.com/akarazhev/metacfg4j).

[minihub.app](https://minihub.app) · hello@minihub.app
