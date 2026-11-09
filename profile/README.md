<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f172a,100:9f1239&height=200&section=header&text=OTI%20UNSCH&fontColor=ffffff&fontSize=52&fontAlignY=38&desc=Oficina%20de%20Tecnolog%C3%ADas%20de%20la%20Informaci%C3%B3n&descAlignY=58&descSize=18" width="100%" alt="OTI UNSCH" />

<div align="center">

<img src="https://res.cloudinary.com/c29eui41/image/upload/v1791261972/assets/logo.png" width="120" alt="Escudo de la Universidad Nacional de San Cristóbal de Huamanga" />

<br /><br />

<a href="https://www.unsch.edu.pe"><img src="./assets/button-website.svg" height="36" alt="unsch.edu.pe" /></a>
&nbsp;
<a href="mailto:oti@unsch.edu.pe"><img src="./assets/button-email.svg" height="36" alt="oti@unsch.edu.pe" /></a>
&nbsp;
<a href="https://github.com/OTI-UNSCH"><img src="./assets/button-github.svg" height="36" alt="GitHub" /></a>

<br /><br />

The **Oficina de Tecnologías de la Información** of the<br />
Universidad Nacional de San Cristóbal de Huamanga plans, builds and runs<br />
the information systems and infrastructure behind university life.

<sub>Founded 1677 · Ciudad Universitaria, Av. Independencia s/n · Ayacucho, Perú</sub>

</div>

<br />

## ✦ What we do

Our work drives the digital transformation of UNSCH's academic and administrative processes, ensuring the **availability, security and integrity** of the services the university community relies on.

<br />

## ✦ What we build

<img src="https://res.cloudinary.com/fdpwaa5i/image/upload/v1791261455/assets/matermark.png" align="right" width="170" alt="" />

**Institutional web applications** — `web-apps/`

**`intranet`** — central admin intranet: IAM, systems registry, content and portal catalog.<br />
**`certificados`** — issue and verify institutional attendance certificates with a visual editor.<br />
**`ldos`** — academic load management and planning.<br />
**`mesa-ayuda`** — help-desk and ticketing platform for the UNSCH community.<br />
**`perfil`** — user profile, document verification and biometric identification.

**Shared platform services** — `svc/`

**`svc/auth`** — authentication, sessions, JWT issuance and RBAC primitives.<br />
**`svc/mail`** — internal mail: SMTP, templates and async delivery over Kafka.<br />
**`svc/storage`** — S3-compatible object storage facade for institutional files.<br />
**`svc/sync`** — scheduled data synchronisation between UNSCH systems.

<sub>Each system lives in its own repository with its own build, test and deployment pipeline — there is no monorepo.</sub>

<br />

## ✦ Stack

<div align="center">

<sub><b>LANGUAGES</b></sub><br /><br />
<img src="https://skillicons.dev/icons?i=go,rust,py,ts&perline=8" alt="Go, Rust, Python, TypeScript" />

<br /><br />

<sub><b>FRONTEND · RUNTIME</b></sub><br /><br />
<img src="https://skillicons.dev/icons?i=nextjs,react,tailwind,bun&perline=8" alt="Next.js, React, Tailwind CSS, Bun" />

<br /><br />

<sub><b>DATA · INFRASTRUCTURE · ML</b></sub><br /><br />
<img src="https://skillicons.dev/icons?i=postgres,redis,kafka,docker,cloudflare,pytorch&perline=8" alt="PostgreSQL, Redis, Apache Kafka, Docker, Cloudflare, PyTorch" />

</div>

<br />

## ✦ How we work

> **Trunk-based development**<br />
> Short-lived feature branches and Pull Requests into `main`, written with Conventional Commits.

> **Mandatory review**<br />
> Every change is reviewed by an OTI maintainer, and CI must be green before integration.

> **Quality gates**<br />
> `golangci-lint`, `cargo clippy`, `ruff` and `eslint`, plus unit tests, on every pipeline.

> **Secrets outside the repository**<br />
> Environment variables and secret managers only — no credentials in history.

> **Accessible and localised**<br />
> User-facing interfaces target WCAG 2.1 AA and are localised for `es-PE`.

<br />

## ✦ Getting involved

Read the [`CODE_OF_CONDUCT`](../CODE_OF_CONDUCT.md), [`CONTRIBUTING`](../CONTRIBUTING.md) and [`SECURITY`](../SECURITY.md) guides before opening an issue or Pull Request. If you do not yet have a written collaboration agreement with UNSCH, write to [oti@unsch.edu.pe](mailto:oti@unsch.edu.pe) first.

**Security issues must never be reported in public issues** — follow the responsible-disclosure process in [`SECURITY.md`](../SECURITY.md).

<br />

<div align="center">

<sub>© Universidad Nacional de San Cristóbal de Huamanga — OTI · Licensed under the terms in [`LICENSE`](../LICENSE)<br />
Service hours: Monday – Friday, 08:00 – 16:00 (UTC−05:00)</sub>

</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:9f1239,100:0f172a&height=100&section=footer" width="100%" alt="" />
