## My projects/learnings/experiments with various data technologies

Three data platforms, all built end to end rather than as demos.

> **All independent personal projects.** Built entirely from public sources and
> synthetic data, on personal time and equipment. They contain no confidential,
> proprietary or employer information, and are not affiliated with, endorsed by, or
> derived from the work of any employer, client, data vendor or exchange. Where a
> component is synthetic, it is labelled as synthetic.

### [merx](https://github.com/ambarshukla/merx)

A commodities data operations platform. **29 datasets from six public sources** — oil,
gas, power, carbon, metals and agriculture — all run through one engine, where adding a
dataset is a declarative **contract file** rather than a new pipeline.

Each dataset is downloaded and kept forever, staged, checked against rules declared in
its contract, and then either published or **held back** by a gate when a critical check
fails. Failed checks become tracked exceptions with owners and root causes. Every value
keeps its full revision history, so any series can be rebuilt **as it was known on a
past date** — which is what stops a backtest using numbers nobody had at the time.

Two sources for the same number are reconciled against each other, and the distinction
matters: two channels of one publisher should agree exactly, while two institutions
computing the same monthly price should only agree within a tolerance. A data-quality
lab scores anomaly detectors against deliberately seeded defects, measuring precision
and recall rather than asserting that the rules work.

Python, DuckDB, Dagster and FastAPI, in containers on a small box, with tests and an
automatic deploy on merge.

Live: [data](https://merx.ambarshukla.dev/client) ·
[two sources](https://merx.ambarshukla.dev/sources) ·
[operations](https://merx.ambarshukla.dev/ops)

### [parvum](https://github.com/ambarshukla/parvum)

A wealth-management data platform. Custodial feeds arrive in real wire formats
(ISO 20022, SWIFT MT), get parsed and normalised against a securities master, reconciled, and served through a Java API to a React dashboard.

Alternatives arrive as PDFs — capital call notices, capital account statements — an LLM extracts the fields, and anything it isn't confident about goes to a human review queue.

Databricks and Delta for the lakehouse, Quarkus and Postgres for serving, the AWS side defined in Terraform.

Live: [client dashboard](https://parvum-dashboard.vercel.app) ·
[internal tools](https://parvum-internal.vercel.app/?demo=1)

### [intus](https://github.com/ambarshukla/intus)

Same idea pointed inwards — a company's own data rather than its clients'. A legacy Postgres star-schema warehouse migrated onto a Databricks lakehouse, with parity checks proving the new platform reproduces the old numbers, and governance as the main event:
row-level security, column masking, audit trails, access reviews.

---

[LinkedIn](https://www.linkedin.com/in/ambarshukla)
