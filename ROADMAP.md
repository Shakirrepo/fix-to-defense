# Roadmap

## Phase 0 — Project setup ✅
- [x] Project design and README
- [x] Research plan

## Phase 1 — Detection
- [ ] CLI skeleton (`ftd scan <path>`)
- [ ] Run Semgrep + Bandit + gitleaks and merge results into one SARIF report
- [ ] Map findings to CWE and OWASP API Top 10
- [ ] Small intentionally vulnerable Flask app for testing (`examples/vuln_flask_app/`)

## Phase 2 — Fix + verify
- [ ] Template-based fixes for CWE-89, CWE-798, CWE-347
- [ ] Show fix as a diff; apply only after approval
- [ ] Verification: rescan + run existing tests

## Phase 3 — Fix-to-Defense
- [ ] Generate a proof-of-vulnerability regression test (pytest) for each fix
- [ ] Generate a project-specific Semgrep rule for each fixed pattern
- [ ] Store tests and rules in `.ftd/` so they stay with the project

## Phase 4 — Evaluation
- [ ] Run on VAmPI and the example app
- [ ] Reintroduce fixed vulnerabilities (same file and new locations)
- [ ] Measure detection: generated tests + rules vs. baseline Semgrep
- [ ] Write up results, including failures and limitations

## Phase 5 — Extensions
- [ ] VS Code extension wrapper
- [ ] LLM-generated fixes for cases templates can't handle (compared against templates)
- [ ] More CWEs: CWE-307, CWE-489, CWE-916
