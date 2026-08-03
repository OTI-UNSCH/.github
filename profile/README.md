<div align="center">

  <img src="https://avatars.githubusercontent.com/u/281988247?s=200&v=4" width="120" alt="OTI UNSCH"/>

  <h2>Oficina de Tecnologías de la Información</h2>
  <h3>Universidad Nacional de San Cristóbal de Huamanga</h3>

  <p><em>Founded 1677 · Ayacucho, Perú</em></p>

  <hr/>

</div>

## About the OTI

The **Oficina de Tecnologías de la Información (OTI)** is the
institutional unit of the Universidad Nacional de San Cristóbal de
Huamanga responsible for planning, designing, developing, integrating,
and operating the university's information systems and technological
infrastructure.

Our work focuses on the digital transformation of UNSCH's academic
and administrative processes, ensuring the **availability, security,
and integrity** of the services that support university life.

&nbsp;

|                          |                                                               |
| :----------------------- | :------------------------------------------------------------ |
| **Parent unit**          | Rectorado — Universidad Nacional de San Cristóbal de Huamanga |
| **Office**               | Oficina de Tecnologías de la Información (OTI)                |
| **Location**             | Ciudad Universitaria, Av. Independencia s/n, Ayacucho, Perú   |
| **Email**                | [oti@unsch.edu.pe](mailto:oti@unsch.edu.pe)                   |
| **Institutional portal** | [www.unsch.edu.pe](https://www.unsch.edu.pe)                  |
| **Service hours**        | Monday – Friday, 08:00 – 16:00 (UTC−05:00)                    |

&nbsp;

## What we build

The repositories in this organisation fall into two broad groups:
**institutional web applications** (`web-apps/`) and **shared
platform services** (`svc/`). Each system is developed as an
independent repository (or set of repositories) with its own build,
test, and deployment pipeline.

### Web applications

| System             | Purpose                                                                   | Stack                                      |
| :----------------- | :------------------------------------------------------------------------ | :----------------------------------------- |
| **`intranet`**     | Central admin intranet: IAM, systems registry, content, portal catalog    | Go (Fiber v3) · Next.js 16 · PostgreSQL    |
| **`certificados`** | Issue and verify institutional attendance certificates with visual editor | Python (FastAPI) · Next.js 16 · WeasyPrint |
| **`ldos`**         | Academic load management and planning                                     | Go · Next.js 16 · Docker Compose           |
| **`mesa-ayuda`**   | Help-desk / ticketing platform for the UNSCH community                    | Go (Fiber v3) · Next.js 16                 |
| **`perfil`**       | User profile, document verification and biometric identification          | Go · Next.js 16 · ONNX Runtime             |

### Shared services (`svc/`)

| Service           | Purpose                                                            | Stack                                   |
| :---------------- | :----------------------------------------------------------------- | :-------------------------------------- |
| **`svc/auth`**    | Authentication, sessions, JWT issuance and RBAC primitives         | Go                                      |
| **`svc/mail`**    | Internal mail service: SMTP, templates, and async delivery (Kafka) | Rust (axum) · Next.js 16 · Apache Kafka |
| **`svc/storage`** | Object storage facade (S3-compatible) for institutional files      | Go                                      |
| **`svc/sync`**    | Scheduled data synchronisation between UNSCH systems               | Go · Next.js 16                         |

> Each repository contains its own `README.md`, and the more
> complex ones (e.g. `intranet-backend`) ship a dedicated
> `ARCHITECTURE.md`.

&nbsp;

## Technology stack

The platform is built on modern, open, long-term-supported
foundations. Per-stack conventions live in each repository.

<div align="center">

![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white) ![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white) ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=next.js&logoColor=white) ![React](https://img.shields.io/badge/React_19-20232A?style=flat-square&logo=react&logoColor=61DAFB) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL_15-336791?style=flat-square&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white) ![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white) ![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white) ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white) ![ONNX](https://img.shields.io/badge/ONNX_Runtime-005CED?style=flat-square&logo=onnx&logoColor=white) ![Bun](https://img.shields.io/badge/Bun-000000?style=flat-square&logo=bun&logoColor=white)

</div>

&nbsp;

## Engineering standards

Every repository under `OTI-UNSCH` is expected to follow the same
baseline. Stack-specific details are documented in each repository's
`AGENTS.md`, `CLAUDE.md`, or `ARCHITECTURE.md`.

- **Trunk-based development** with short-lived feature branches and
  Pull Requests into `main`.
- **Conventional Commits** for every commit (`feat:`, `fix:`,
  `refactor:`, `docs:`, …).
- **Mandatory code review** by an OTI maintainer before integration;
  CI must be green.
- **Secrets outside the repository** — environment variables and
  secret managers only; no credentials in history.
- **Per-repository documentation** — `README.md`, changelog, and
  (where applicable) `ARCHITECTURE.md`.
- **Quality gates** — linting and formatting (`golangci-lint`,
  `cargo clippy`, `ruff`, `eslint`) and unit tests in CI.
- **Accessibility and localisation** — user-facing interfaces aim for
  WCAG 2.1 AA and are localised for `es-PE`.

&nbsp;

## Getting involved

External contributors are welcome, but the Software is proprietary
to UNSCH. Please:

1. Read the organisation-level [`CODE_OF_CONDUCT`](../CODE_OF_CONDUCT.md)
   and [`SECURITY`](../SECURITY.md) before opening any issue.
2. Read [`CONTRIBUTING`](../CONTRIBUTING.md) for branching, commits,
   and review expectations.
3. Clone the specific repository you need; there is **no monorepo**
   at the organisation level.
4. Open a Pull Request against the appropriate `develop` (or
   repository-default) branch.

If you do not yet have a written collaboration agreement with UNSCH,
write to [oti@unsch.edu.pe](mailto:oti@unsch.edu.pe) **before**
opening an issue.

&nbsp;

## Reporting security issues

**Do not open public GitHub issues for security vulnerabilities.**
See [`SECURITY.md`](../SECURITY.md) for the responsible-disclosure
process and the contact channel
([oti@unsch.edu.pe](mailto:oti@unsch.edu.pe)).

&nbsp;

## Licence

All original work in this organisation is © Universidad Nacional de
San Cristóbal de Huamanga — Oficina de Tecnologías de la Información,
made available under the terms described in [`LICENSE`](../LICENSE).
Third-party components retain their respective upstream licences.

&nbsp;

---

<div align="center">
  <sub>Oficina de Tecnologías de la Información &nbsp;·&nbsp; Universidad Nacional de San Cristóbal de Huamanga &nbsp;·&nbsp; Ayacucho, Perú</sub>
</div>
