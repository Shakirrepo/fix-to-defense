# Fix-to-Defense

**Fix a vulnerability once — and make sure it never silently comes back.**

> 🚧 **Status: Early development.** This repository currently contains the project design and research plan. Code will be added in stages (see [ROADMAP.md](ROADMAP.md)). No results are claimed yet.

## The problem

Security scanners find vulnerabilities, and tools such as GitHub Copilot Autofix and Snyk Agent Fix can now propose patches. But a patch alone does not stop the same mistake from returning in a later commit, in another file, or through AI-generated code.

## The idea

Fix-to-Defense is an open-source tool for **Python/Flask APIs** that turns every security fix into lasting protection:

```
DETECT  →  FIX  →  VERIFY  →  TEST  →  PREVENT  →  REPORT
```

| Step | What happens |
|------|--------------|
| **Detect** | Find vulnerabilities using Semgrep, Bandit and gitleaks, mapped to CWE / OWASP API Top 10 |
| **Fix** | Propose a patch as a diff — **nothing changes without developer approval** |
| **Verify** | Rescan, run the project's existing tests, and confirm the issue is gone |
| **Test** | Generate a proof-of-vulnerability **regression test** that fails if the bug returns |
| **Prevent** | Generate a project-specific **Semgrep rule** that flags the same pattern elsewhere |
| **Report** | Produce an evidence report: what passed, what failed, what remains unverified |

## Initial scope (MVP)

| Vulnerability | CWE |
|---------------|-----|
| SQL injection | CWE-89 |
| Hardcoded secrets | CWE-798 |
| JWT misconfiguration (no expiry, `none` algorithm, weak secret) | CWE-347 |

Planned next: missing rate limiting (CWE-307), debug mode in production (CWE-489), weak password hashing (CWE-916).

## Research question

> Do automatically generated regression tests and preventive rules catch reintroduced vulnerabilities more reliably than a standard static scan alone?

Planned evaluation on intentionally vulnerable APIs such as [VAmPI](https://github.com/erev0s/VAmPI) and [OWASP crAPI](https://github.com/OWASP/crAPI), comparing against a baseline Semgrep scan. See [docs/RESEARCH_PLAN.md](docs/RESEARCH_PLAN.md).

## Design principles

- **Developer stays in control** — every change is shown as a diff and needs approval.
- **Local first** — code does not need to leave your machine.
- **Honest evidence** — report failures and unverified results, not just successes.
- **Narrow and reliable** before broad and impressive.

## Tech stack (planned)

Python 3.10+, Semgrep, Bandit, gitleaks, pytest, SARIF output. VS Code extension (TypeScript) in a later phase.

## Author

**Shakir Ullah** — BS Computer Science (Software), CEH
Interests: software security, API security, automated vulnerability repair

## License

MIT — see [LICENSE](LICENSE).
