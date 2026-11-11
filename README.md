## My projects/learnings/experiments with various data technologies

Five data platforms, all finance-shaped, all built end to end rather than as demos.

> **All independent personal projects.** Built entirely from public sources and
> synthetic data, on personal time and equipment.

### [rivus](https://github.com/ambarshukla/rivus)

Kafka, Flink SQL, ClickHouse, Redis, a C# API with SignalR, Airflow and dbt on DuckDB.
Runs in Docker Compose on one machine; not hosted.

A streaming market-data pipeline. Live trades from three crypto exchanges' public feeds
become one-second and one-minute price bars within about four seconds, with late trades,
sequence gaps and cross-venue differences recorded as they happen.

Every hour a batch job rebuilds the same bars from the raw messages with separately
written parsing, and every difference from the stream is classified. Everything downstream
of the raw messages can be deleted and rebuilt by replaying them.

[Screenshots](https://github.com/ambarshukla/rivus#what-it-looks-like) ·
[architecture](https://github.com/ambarshukla/rivus/blob/main/docs/ARCHITECTURE.md) ·
[build log](https://github.com/ambarshukla/rivus/blob/main/docs/BUILD_LOG.md)

### [merx](https://github.com/ambarshukla/merx)

DuckDB, Dagster, FastAPI, Docker containers. Hetzner hosted.

A commodities data operations platform. Public data on oil, gas, power, carbon, metals
and agriculture. Adding a dataset is a contract file rather than another pipeline.

Every value keeps its revision history, so a series can be rebuilt as it stood on a past
date, and where two sources publish the same number they're reconciled against each
other.


Live: [data](https://merx.ambarshukla.dev/client) ·
[two sources](https://merx.ambarshukla.dev/sources) ·
[operations](https://merx.ambarshukla.dev/ops)

### [pretium](https://github.com/ambarshukla/pretium)

Java 21, Spring Boot, Kafka and Postgres, a Next.js front end on Hetzner.

A price-comparison platform for sending money abroad. Four real public sources (World Bank
remittance prices, and ECB reference rates over three channels).
Rates flow through Kafka into Postgres and out to a comparison site.

When a source changes its page layout, a local LLM proposes new selectors, and nothing is
accepted unless the result matches the official data exactly. 

Replayed over nine years of
archived copies of one page, it read 118 of 119 correctly, with no wrong numbers.


Live: [comparison](https://pretium.ambarshukla.dev) ·
[operations](https://pretium.ambarshukla.dev/ops) ·
[method](https://pretium.ambarshukla.dev/about)

### [parvum](https://github.com/ambarshukla/parvum)

A wealth-management data platform. Custodial feeds arrive in real wire formats
(ISO 20022, SWIFT MT), get parsed and normalised against a securities master, reconciled, and served through a Java API to a React dashboard.

Alternatives arrive as PDFs — capital call notices, capital account statements — an LLM extracts the fields, and anything it isn't confident about goes to a human review queue.

Databricks and Delta for the lakehouse, Quarkus and Postgres for serving hosted on Hetzner after AWS free tier ran out.

Live: [client dashboard](https://parvum-dashboard.vercel.app) ·
[internal tools](https://parvum-internal.vercel.app/?demo=1)

### [intus](https://github.com/ambarshukla/intus)

A company-internal (CIO remit) database on Postgres star-schema warehouse migrated onto a Databricks lakehouse, with parity checks proving the new platform reproduces the old numbers, with row-level security, column masking, audit trails, access reviews.

---

[LinkedIn](https://www.linkedin.com/in/ambarshukla)
