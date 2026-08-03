# Security Policy

The **Oficina de Tecnologías de la Información (OTI)** of the
**Universidad Nacional de San Cristóbal de Huamanga (UNSCH)** takes
the security of its information systems and the privacy of the UNSCH
community very seriously.

We value the work of security researchers and the wider technical
community and welcome coordinated, responsible disclosure of
vulnerabilities.

---

## 1. Supported versions

The repositories under `OTI-UNSCH` follow **continuous delivery**: the
`main` branch is always the supported version. Older releases receive
security fixes only on a best-effort basis and at the discretion of
the OTI.

| Branch / component           | Status             | Notes                                 |
| ---------------------------- | ------------------ | ------------------------------------- |
| `main`                       | :white_check_mark: | Production-ready code; security-fixed |
| `release/*` (active)         | :white_check_mark: | Receives critical security patches    |
| `develop` / feature branches | :white_check_mark: | Pre-release; included in next release |
| Anything older / archived    | :x:                | Update to the latest release          |

For each individual repository, the supported-versions matrix is
maintained in the repository's own `SECURITY.md`.

---

## 2. Reporting a vulnerability

> **Do not file public GitHub issues for security vulnerabilities.**
> Public disclosure before a fix is available puts the UNSCH community
> at risk.

### 2.1 Where to send the report

Send a private report to the OTI Security Team:

- **Primary email:** [oti@unsch.edu.pe](mailto:oti@unsch.edu.pe)
- **Security alias (preferred when available):**
  [seguridad.oti@unsch.edu.pe](mailto:seguridad.oti@unsch.edu.pe)
- **Subject line:** `[SECURITY] Vulnerability report — <component>`

### 2.2 What to include

To help us triage quickly, please provide:

1. **Summary** — a short, clear description of the issue.
2. **Affected component** — repository, version/commit SHA, endpoint
   or file path, and deployment context (staging vs. production).
3. **Reproduction steps** — minimal, step-by-step instructions or a
   safe Proof of Concept. **Never run a PoC against production data.**
4. **Impact assessment** — what an attacker could achieve
   (authentication bypass, data exfiltration, privilege escalation,
   remote code execution, etc.) and the affected user groups.
5. **Environment** — OS, browser, runtime version, network position.
6. **Suggested remediation** — if you have one (optional but
   appreciated).
7. **Disclosure preferences** — whether you wish to be credited, and
   any constraints on disclosure timing.

### 2.3 Optional: encrypted report

If the report contains sensitive information, request the OTI PGP key
by replying to an initial unencrypted acknowledgement email. We will
provide the public key and a secure channel for follow-up.

---

## 3. Our commitments to you

When you submit a report in good faith, the OTI will:

| Step                                   | Target                                           |
| -------------------------------------- | ------------------------------------------------ |
| Acknowledge receipt                    | Within **2 business days**                       |
| Initial triage and severity assessment | Within **5 business days**                       |
| Status update with reproduction/impact | Within **10 business days**                      |
| Fix or mitigation in supported code    | Depending on severity (see below)                |
| Coordinated public disclosure          | After a fix is available, or by mutual agreement |
| Credit to the reporter (if requested)  | In the release notes / advisory                  |

We will keep you informed of progress, and we will not pursue legal
action against researchers who comply with this policy and applicable
Peruvian law.

### Severity-based remediation targets

| Severity (CVSS v3.1) | Target for fix or mitigation |
| -------------------- | ---------------------------- |
| Critical (≥ 9.0)     | Within **7 days**            |
| High (7.0 – 8.9)     | Within **30 days**           |
| Medium (4.0 – 6.9)   | Within **90 days**           |
| Low (< 4.0)          | Next regular release         |

---

## 4. Rules of engagement

By interacting with UNSCH systems as part of a security investigation,
you agree to:

- **Not cause disruption.** No denial-of-service, traffic flooding,
  rate-limit busting, or resource-exhaustion attacks. No social
  engineering of UNSCH staff, students, or faculty.
- **Not access or modify real personal data.** Stop immediately if
  you encounter personally identifiable information of students,
  faculty, or staff. Provide us with the minimal proof needed to
  confirm the issue and let us collect the rest.
- **Not pivot laterally.** If you find access to a system or account,
  do not explore further; report the access level and let us
  investigate.
- **Avoid destructive testing.** No mass automated scanning,
  vulnerability fuzzing of production, or destructive actions
  against production data.
- **Maintain confidentiality.** Give us a reasonable window to
  release a fix before any public write-up. We will work with you
  on a coordinated disclosure timeline.
- **Comply with Peruvian law.** This policy does not authorise
  activity that violates Peruvian law (including but not limited
  to the Código Penal and Ley N.° 30096 — Delitos Informáticos).

---

## 5. Security practices in OTI systems

The OTI builds and operates its systems with security as a baseline,
not a feature. Across repositories you will find:

- **Authentication and authorisation**
  - JWT access and refresh tokens over `httpOnly`, `Secure`,
    `SameSite=Lax` cookies.
  - Server-side sessions for cross-system SSO with opaque tokens.
  - Role-based access control (RBAC) with global and system-scoped
    roles; middleware-enforced on every protected route.
  - Mandatory MFA for administrative accounts.
- **Transport security**
  - HTTPS/TLS 1.2+ on every public endpoint (Cloudflare in front
    of production).
  - HSTS, secure cookies, and modern cipher suites.
  - mTLS between internal services in higher-security contexts.
- **Application security**
  - Input validation and parameterised queries (SQLi prevention).
  - CSRF protection on state-changing requests.
  - Output encoding and a strict Content Security Policy.
  - Centralised structured logging with redaction of PII.
- **Data protection**
  - Encryption at rest for sensitive columns and backups.
  - Secrets outside version control (environment variables, secret
    managers).
  - Compliance with Ley N.° 29733 (Protección de Datos Personales).
- **Operational security**
  - Dependency scanning and `gitleaks`/`trufflehog` in CI.
  - Container image scanning on every build.
  - Audit logs of administrative actions, retained per UNSCH policy.
  - Regular vulnerability assessments and external penetration tests.

---

## 6. Out-of-scope reports

The following are generally considered out of scope and may be
closed without a fix. We still appreciate the report, but please do
not expect a CVE-level response:

- Reports that require physical access to a UNSCH device.
- Reports that require access to an already-compromised account.
- Lack of a particular security header without demonstrable impact.
- Self-XSS or issues that only affect the reporter's own account.
- Spam or social-engineling capabilities without a concrete bypass.
- Recently disclosed zero-days for which a vendor patch is already
  applied and verified.
- Reports against third-party services not operated by UNSCH.

---

## 7. Recognition

We maintain a **Hall of Fame** for researchers who have helped us
improve the security of UNSCH systems. Inclusion is at the discretion
of the OTI and conditional on the researcher's agreement.

---

## 8. Contact

- **General security email:** [oti@unsch.edu.pe](mailto:oti@unsch.edu.pe)
- **Subject prefix:** `[SECURITY]`
- **Office hours:** Monday – Friday, 08:00 – 16:00 (UTC−05:00)

If you cannot reach us by email and the issue is critical and ongoing,
contact the UNSCH central switchboard at +51 (66) 31-XXXX and ask
for the OTI on-call engineer.

---

Thank you for helping us keep the UNSCH community safe.

— _Oficina de Tecnologías de la Información, UNSCH_
