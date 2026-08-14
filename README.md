## My projects/learnings/experiments with various data technologies

Two data platforms, both finance-shaped, both built end to end rather than as demos.

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
