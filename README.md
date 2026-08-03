# OTI — UNSCH

> Office of Information Technologies (Oficina de Tecnologías de la Información)
> Universidad Nacional de San Cristóbal de Huamanga · Ayacucho, Perú

This organization hosts the source code, infrastructure, and
documentation of the institutional systems developed and maintained by
the **OTI** for the **UNSCH** community: students, faculty, staff, and
administrative units.

The Software in this organization is proprietary to UNSCH. See
[`LICENSE`](./LICENSE) for the terms under which it may be read, used,
and contributed to.

---

## About the OTI

The **Oficina de Tecnologías de la Información (OTI)** is the
institutional unit of the Universidad Nacional de San Cristóbal de
Huamanga responsible for planning, designing, developing, integrating,
and operating the university's information systems and technological
infrastructure.

Its mandate is the digital transformation of UNSCH's academic and
administrative processes, ensuring the **availability, security, and
integrity** of the services that support university life.

|                          |                                                             |
| ------------------------ | ----------------------------------------------------------- |
| **Parent institution**   | Universidad Nacional de San Cristóbal de Huamanga (UNSCH)   |
| **Office**               | Oficina de Tecnologías de la Información (OTI)              |
| **Location**             | Ciudad Universitaria, Av. Independencia s/n, Ayacucho, Perú |
| **Email**                | [oti@unsch.edu.pe](mailto:oti@unsch.edu.pe)                 |
| **Institutional portal** | [www.unsch.edu.pe](https://www.unsch.edu.pe)                |
| **Service hours**        | Monday – Friday, 08:00 – 16:00 (UTC−05:00)                  |

---

## Mission

Deliver robust, secure, and accessible software platforms that support
UNSCH's teaching, research, and administrative activities, with public
accountability and respect for the personal data of the university
community.

---

## What lives in this organization

The repositories here cover, but are not limited to:

- **Web applications** — academic and administrative front-ends
  (intranet, certificates, ldos, help desk, profile, and others).
- **Back-office services (`svc/`)** — shared platform services such as
  authentication (`auth`), mail (`mail`), object storage (`storage`),
  and data synchronisation (`sync`).
- **Internal tooling and knowledge bases** — operations runbooks and
  reference material used by the OTI team.

Each repository is self-contained, with its own build, test, and
deployment instructions. Refer to the `README.md` and (where
applicable) `ARCHITECTURE.md` of each repository before contributing.

---

## Technology stack

The institutional platform is built on **modern, open, long-term-
supported** foundations. Per-stack tooling lives in each repository
and is summarised below.

**Languages**

- Go (Fiber v3, sqlx)
- Rust (axum, sqlx, tokio)
- Python 3.11+ (FastAPI, SQLAlchemy 2, Celery)
- TypeScript on Node 20 / Bun

**Front-end**

- Next.js 16 with React 19 (App Router)
- Tailwind CSS, shadcn/ui, Radix
- Bun as the package manager and runtime in development

**Data and messaging**

- PostgreSQL 15 (primary store)
- Redis (cache, rate limiting, sessions)
- Apache Kafka (asynchronous inter-service messaging)

**Infrastructure and operations**

- Docker / Docker Compose for local and production deployments
- Cloudflare in front of public endpoints (DNS, WAF, edge cache)
- GitHub Actions for CI
- Linux servers on premise and in managed cloud

**AI / ML**

- PyTorch and ONNX Runtime for in-house inference (e.g. document
  verification in the certificates and profile subsystems)

---

## Engineering standards

Every repository under OTI-UNSCH is expected to comply with the
following baseline. Stack-specific details are documented in each
repository's `AGENTS.md`, `CLAUDE.md`, or `ARCHITECTURE.md`.

- **Versioning and branching** — Trunk-based development with short-
  lived feature branches; the `main` branch is always deployable.
- **Commit conventions** — [Conventional Commits](https://www.conventionalcommits.org/)
  (`feat:`, `fix:`, `refactor:`, `docs:`, `chore:`, …).
- **Code review** — Every change lands through a Pull Request with at
  least one approving review from a maintainer.
- **Secrets management** — Credentials, keys, and tokens are never
  committed; configuration is loaded from environment variables or a
  secrets manager.
- **Documentation** — Every repository ships a `README.md`, a
  changelog, and (where relevant) an `ARCHITECTURE.md`.
- **Quality gates** — Linting and formatting (`golangci-lint`, `cargo
clippy`, `ruff`, `eslint`) and unit tests are part of the CI
  pipeline.
- **Accessibility and localisation** — User-facing interfaces follow
  WCAG 2.1 AA and are localised for the UNSCH community (es-PE).

---

## Getting started

If you are an authorised collaborator:

1. Read the [`CODE_OF_CONDUCT`](./CODE_OF_CONDUCT.md).
2. Read the [`SECURITY`](./SECURITY.md) policy before reporting any
   issue.
3. Read the [`CONTRIBUTING`](./CONTRIBUTING.md) guide for branching,
   commits, and review expectations.
4. Clone the specific repository you need; there is no monorepo at the
   organization level.
5. Open a Pull Request against the appropriate `develop` (or
   repository-default) branch.

External contributors without a written collaboration agreement should
contact the OTI before opening issues or Pull Requests; please see the
licence terms in [`LICENSE`](./LICENSE).

---

## Reporting security issues

**Do not open public GitHub issues for security vulnerabilities.**

See [`SECURITY.md`](./SECURITY.md) for the responsible-disclosure
process and the contact channel
([oti@unsch.edu.pe](mailto:oti@unsch.edu.pe)).

---

## Licence

All original work in this organization is © Universidad Nacional de
San Cristóbal de Huamanga — Oficina de Tecnologías de la Información.
See [`LICENSE`](./LICENSE) for the proprietary terms under which it
is made available.

Third-party components used by the projects retain their respective
upstream licences.

---

<div align="center">
  <sub>Oficina de Tecnologías de la Información &nbsp;·&nbsp; Universidad Nacional de San Cristóbal de Huamanga &nbsp;·&nbsp; Ayacucho, Perú</sub>
</div>
