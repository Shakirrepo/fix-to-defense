# Research Plan

## Working title
Fix-to-Defense: Turning Vulnerability Repairs into Regression Tests and Preventive Rules for Web APIs

## Motivation
Automated vulnerability repair is now offered by commercial tools, but recent research notes that detection and repair are usually evaluated in isolation, and that repairs can introduce regressions or new flaws. Proof-of-vulnerability (PoV) tests are valuable because they fail while a vulnerability exists and pass once it is fixed, but they are rarely written and remain hard to generate automatically.

## Research questions
- **RQ1:** For a defined set of CWEs in Flask APIs, how often does the tool produce a fix that removes the finding and keeps existing tests passing?
- **RQ2:** How often do generated regression tests correctly fail on the vulnerable version and pass on the fixed version?
- **RQ3:** When fixed vulnerabilities are reintroduced (same location or new locations), how many are caught by generated tests and rules compared with a baseline Semgrep scan?

## Method (planned)
1. Target apps: VAmPI, OWASP crAPI (Python components where applicable), and a purpose-built vulnerable Flask app.
2. Detection with Semgrep, Bandit and gitleaks; findings normalized to SARIF.
3. Template-based repair for CWE-89, CWE-798, CWE-347.
4. Generate a pytest PoV test and a Semgrep rule per fix.
5. Reintroduction experiment: re-insert each vulnerability and controlled variants; record which mechanism detects it.
6. Report all outcomes, including failed fixes and false positives.

## Threats to validity
- Small number of target applications.
- Reintroduced variants are author-constructed and may not reflect real developer mistakes.
- Passing tests do not prove absence of a vulnerability.

## Key references
- Nitin et al., *FaultLine: Automated Proof-of-Vulnerability Generation Using LLM Agents* (arXiv:2507.15241)
- Pearce et al., *Examining Zero-Shot Vulnerability Repair with Large Language Models* (arXiv:2112.02125)
- OWASP API Security Top 10; OWASP ASVS
