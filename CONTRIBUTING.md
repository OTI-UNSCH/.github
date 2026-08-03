# Contributing to OTI — UNSCH

Thank you for your interest in contributing to the institutional
software of the **Universidad Nacional de San Cristóbal de Huamanga**.

This organisation hosts proprietary software owned by UNSCH. By
contributing, you agree to the terms described in [`LICENSE`](./LICENSE)
and confirm that your contribution may be incorporated into the
Software under those terms.

> **External contributors:** please read section 5 _before_ opening a
> Pull Request. If you do not have a written collaboration agreement
> with UNSCH, please contact the OTI first.

---

## 1. Code of Conduct

All participants in OTI spaces are expected to follow our
[`CODE_OF_CONDUCT`](./CODE_OF_CONDUCT.md). Be respectful, be
professional, be inclusive.

---

## 2. How the OTI development workflow works

### 2.1 Branching model

We follow **trunk-based development**:

- `main` is always deployable. **Direct pushes to `main` are
  forbidden.**
- Long-lived release branches (`release/*`) are created from `main`
  when a milestone is cut, and receive only critical fixes.
- Day-to-day work happens on short-lived branches cut from `main`:
  - `feat/<scope>-<short-description>`
  - `fix/<scope>-<short-description>`
  - `refactor/<scope>-<short-description>`
  - `docs/<scope>-<short-description>`
  - `chore/<scope>-<short-description>`
  - `test/<scope>-<short-description>`

A Pull Request is merged back into `main` once it has the required
approvals and a green CI run.

### 2.2 Commit messages — Conventional Commits

Every commit must follow the [Conventional Commits](https://www.conventionalcommits.org/)
specification:

```
<type>(<scope>): <short summary>

<body — explain the "what" and the "why", not the "how">

<footer — references to issues, breaking changes, co-authors>
```

Allowed types: `feat`, `fix`, `refactor`, `perf`, `test`, `docs`,
`build`, `ci`, `chore`, `revert`.

Examples:

```
feat(auth): add MFA enrolment endpoint for student accounts
fix(ldos): correct pagination cursor on list endpoint
docs(readme): clarify local PostgreSQL bootstrap
```

### 2.3 Pull Requests

PRs are the only path into `main`. A good PR:

- **Is small and focused** — one concern per PR. Split larger changes.
- **Has a descriptive title** — a single line in conventional-commit
  form.
- **Has a description** that explains the motivation, the approach,
  and any trade-offs. Link the relevant issue (`Closes #123`).
- **Includes tests** that cover the change (unit, integration, or
  both, as appropriate).
- **Updates documentation** that would otherwise become stale
  (README, ARCHITECTURE, OpenAPI, .env.example).
- **Passes CI** — lint, format, type-check, tests, build.
- **Is reviewed** — at least one approving review from a code owner
  listed in `CODEOWNERS`. Two reviewers are required for changes
  touching authentication, authorisation, schema migrations, or
  production infrastructure.

Squash-merge is the default. The PR title becomes the squash commit
subject and must therefore be a valid Conventional Commit.

---

## 3. Engineering standards (baseline)

These standards apply across all OTI repositories. Stack-specific
guidance is documented in each repository's `AGENTS.md` or
`ARCHITECTURE.md`.

### 3.1 Languages

- **Go** — `gofmt`/`goimports`, `golangci-lint`, `go vet`. Errors must
  be wrapped (`fmt.Errorf("...: %w", err)`); no `panic` in business
  logic; context propagated as the first parameter.
- **Rust** — `cargo fmt`, `cargo clippy --all-targets -- -D warnings`,
  `cargo test`. Public APIs documented; `unsafe` requires an
  in-source justification comment.
- **Python** — `ruff format`, `ruff check`, `mypy` on typed modules.
  Type hints are required for all new public functions.
- **TypeScript / JavaScript** — `eslint` + `prettier`. `strict:
true`. Avoid `any` outside generated code.

### 3.2 Architecture

- **Backend services** are organised by **bounded context** inside
  `internal/`. Shared, non-domain code lives under `pkg/`. See the
  architecture guide of the relevant repository.
- **Database changes** ship as versioned migrations (Alembic, sqlx,
  or goose — per repository). Migrations are forward-only outside of
  unreleased branches.
- **Front-ends** follow a **feature-sliced structure** (`src/features/`,
  `src/entities/`, `src/shared/`) and use Next.js App Router.
- **APIs** are REST + JSON. Errors follow a consistent envelope (see
  each service's docs). Authentication is JWT over httpOnly cookies
  for browser flows; opaque session tokens for service-to-service
  SSO.

### 3.3 Quality gates

A Pull Request cannot be merged unless:

- [ ] Lint passes
- [ ] Formatter reports no diff
- [ ] Unit tests pass (and new code is covered)
- [ ] Build succeeds
- [ ] No secrets are introduced (CI runs `gitleaks` / `trufflehog`)
- [ ] Documentation is up to date

---

## 4. Local development

Common prerequisites for most repositories:

- Docker 24+ and Docker Compose v2
- A Unix-like shell (Linux, macOS, or WSL)
- Language toolchains:
  - Go ≥ 1.22
  - Rust ≥ 1.78 (stable)
  - Python ≥ 3.11 with `uv` or `poetry`
  - Bun ≥ 1.1 and Node ≥ 20
- PostgreSQL 15 and Redis 7 (typically via `docker compose up -d`)
- `make`

Each repository has its own `Makefile` or `package.json` scripts.
Typical first-time setup:

```bash
git clone git@github.com:OTI-UNSCH/<repo>.git
cd <repo>
cp .env.example .env
docker compose up -d          # or: make setup
make install                  # or: bun install / go mod download / uv sync
make dev                      # or: bun run dev / cargo run
make test
make lint
```

Specific commands and per-repository conventions are documented in
each `README.md` and (where applicable) `ARCHITECTURE.md`.

---

## 5. External contributors

The Software in this organisation is proprietary to UNSCH (see
[`LICENSE`](./LICENSE)). External collaboration is welcome, but:

1. **Open an issue first** describing what you would like to change
   and why. Do not start a Pull Request before a maintainer has
   confirmed that the contribution is in scope.
2. **Sign a Contributor Agreement** when requested. For non-trivial
   contributions, the OTI may ask you to sign a lightweight CLA that
   confirms your right to submit the work and assigns the
   contribution to UNSCH (or, where assignment is impossible, grants
   UNSCH a perpetual licence to use it).
3. **Do not include third-party copyrighted material** (logos, fonts,
   libraries) without a compatible licence.
4. **Do not include personal data** of UNSCH students, faculty, or
   staff in tests, fixtures, or examples. Use synthetic data only.

If you are not sure whether your contribution is appropriate, write to
[oti@unsch.edu.pe](mailto:oti@unsch.edu.pe) **before** opening an
issue.

---

## 6. Reporting bugs and requesting features

- **Security issues** — see [`SECURITY.md`](./SECURITY.md). **Do not
  open a public issue.**
- **Ordinary bugs** — open an issue with:
  - A clear, specific title.
  - Reproduction steps (commands, URLs, screenshots).
  - Expected vs. actual behaviour.
  - Environment (OS, browser, commit SHA).
- **Feature requests** — open an issue describing the user need, the
  proposed solution, and any alternatives considered. Feature
  requests are triaged by the OTI Product Committee.

---

## 7. Communication

| Channel            | Use                                                    |
| ------------------ | ------------------------------------------------------ |
| GitHub Issues      | Bug reports, feature requests, task tracking           |
| Pull Requests      | Code review and design discussion                      |
| GitHub Discussions | Open-ended questions, proposals, RFCs                  |
| Email              | Private matters, security, licensing: oti@unsch.edu.pe |

For urgent operational incidents in production, contact the OTI
on-call rotation via [oti@unsch.edu.pe](mailto:oti@unsch.edu.pe).

---

## 8. Recognition

Contributors are credited in each repository's `AUTHORS.md` (where
maintained) and in the OTI annual activity report. Significant
contributions are acknowledged in the corresponding release notes.

---

Thank you for helping us build reliable software for the UNSCH
community.

— _Oficina de Tecnologías de la Información, UNSCH_
