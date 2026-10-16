## My projects/learnings/experiments with various data technologies

Three data platforms, all finance-shaped, all built end to end rather than as demos.

> **All independent personal projects.** Built entirely from public sources and
> synthetic data, on personal time and equipment. They contain no confidential,
> proprietary or employer information, and are not affiliated with, endorsed by, or
> derived from the work of any employer, client, data vendor or exchange. Where a
> component is synthetic, it is labelled as synthetic.

### [merx](https://github.com/ambarshukla/merx)

A commodities data operations platform. Public data on oil, gas, power, carbon, metals
and agriculture gets downloaded and kept, staged, checked against rules declared per
dataset, then published — or held back when a check fails. Adding a dataset is a
contract file rather than another pipeline.

Every value keeps its revision history, so a series can be rebuilt as it stood on a past
date, and where two sources publish the same number they're reconciled against each
other.

DuckDB, Dagster and FastAPI, in containers with an automatic deploy on merge.

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
