---
name: devsecops-assessment
description: Conduct a structured DevSecOps maturity assessment for an organization, evaluating CI/CD pipelines, security integration (shift-left, SAST, SCA, DAST), secrets management, IaC security, supply chain security, and software quality practices. Use this skill when Nexus needs to evaluate or diagnose the DevSecOps posture of an organization. Trigger for any assessment involving pipelines, CI/CD, application security, developer security practices, compliance posture, or software delivery quality — even if the user just asks "how secure is our pipeline?" or "what's wrong with our CI/CD?"
---

# DevSecOps Assessment — Maturity Evaluation Framework

This skill guides Nexus through a structured DevSecOps maturity assessment, from data collection to prioritized recommendations.

## Assessment Approach

Adapt depth to organization size:
- **< 10 engineers:** Focus on CI/CD basics and critical security gaps. Skip advanced supply chain security.
- **10–50 engineers:** Full assessment of all domains. Prioritize shift-left and secrets management.
- **50+ engineers:** Include compliance automation, supply chain security, and policy-as-code.

## Evaluation Domains & Scoring Criteria

### Domain 1: CI/CD Pipeline
Score each criterion: ✅ Present | ⚠️ Partial | ❌ Missing

**Basics (all orgs)**
- [ ] Automated build triggered on every commit/PR
- [ ] Automated test execution in pipeline
- [ ] Automated deployment to at least one environment
- [ ] Rollback capability (manual or automated)
- [ ] Artifact versioning and storage

**Advanced (10+ engineers)**
- [ ] Multi-stage pipeline (dev → staging → prod)
- [ ] Environment promotion gates (approval or automated quality gates)
- [ ] Pipeline as code (stored in repo, reviewed like code)
- [ ] Blue/green or canary deployment strategy

### Domain 2: Security Integration (Shift-Left)

**Code & dependency scanning**
- [ ] SAST tool configured and running on PRs (Semgrep, SonarQube, CodeQL)
- [ ] Dependency vulnerability scanning (Dependabot, Snyk, OWASP DC)
- [ ] License compliance scanning
- [ ] Secrets detection in code (GitLeaks, TruffleHog, detect-secrets)

**Runtime & infrastructure**
- [ ] Container image scanning (Trivy, Grype, Snyk Container)
- [ ] IaC security scanning (Checkov, tfsec, KICS)
- [ ] DAST in staging environment (OWASP ZAP, Burp Suite)

**Policy enforcement**
- [ ] Security gates that block merges on critical findings
- [ ] Defined severity thresholds for auto-blocking vs warnings

### Domain 3: Secrets & Configuration Management
- [ ] No hardcoded secrets in codebase (verified via scanning)
- [ ] Centralized secrets management (Vault, AWS Secrets Manager, Azure KV)
- [ ] Secrets rotation policy defined and enforced
- [ ] Different secrets per environment (no prod secrets in dev)
- [ ] Audit trail for secrets access

### Domain 4: Supply Chain Security
*(Prioritize for 20+ engineers or B2B/regulated orgs)*
- [ ] Pinned dependency versions (no floating `latest`)
- [ ] SBOM generation (CycloneDX, SPDX)
- [ ] Image signing (Cosign, Notation)
- [ ] Verified base images from trusted registries
- [ ] Third-party action/plugin vetting (GitHub Actions, Jenkins plugins)

### Domain 5: Code Quality & Testing
- [ ] Automated unit tests with coverage tracking (target: ≥ 70%)
- [ ] Integration tests in pipeline
- [ ] Formal PR review process (≥ 1 approval required)
- [ ] Branching strategy defined and followed (trunk-based or GitFlow)
- [ ] Static code quality tools (linting, formatting enforced)

### Domain 6: Compliance Posture
*(Only if regulatory context applies)*
- [ ] Evidence of security controls exportable for audits
- [ ] Change management trail (who deployed what, when)
- [ ] Vulnerability management SLA defined (critical: 24h, high: 7d)
- [ ] Penetration testing schedule defined

## Maturity Scoring

Count the ✅ across all applicable domains:

| Score | Level | Description |
|-------|-------|-------------|
| < 20% | 1 — Inicial | Procesos manuales, sin automatización de seguridad |
| 20–40% | 2 — Básico | CI básico, sin seguridad integrada |
| 40–60% | 3 — Definido | CI/CD completo, seguridad básica en pipeline |
| 60–80% | 4 — Gestionado | Shift-left completo, gestión activa de vulnerabilidades |
| > 80% | 5 — Optimizado | Supply chain, compliance automatizado, feedback loops |

## Output Format

```markdown
## Evaluación DevSecOps — [Organización]

### Nivel de Madurez: [1-5] — [Nombre]
**Score:** [X/Y criterios aplicables] ([Z]%)

### Semáforo por dominio
| Dominio | Estado | Score | Hallazgo crítico |
|---------|--------|-------|-----------------|
| CI/CD Pipeline | 🔴/🟡/🟢 | X/Y | [...] |
| Shift-Left Security | 🔴/🟡/🟢 | X/Y | [...] |
| Secrets Management | 🔴/🟡/🟢 | X/Y | [...] |
| Supply Chain | 🔴/🟡/🟢 | X/Y | [...] |
| Code Quality | 🔴/🟡/🟢 | X/Y | [...] |

### Brechas críticas (acción inmediata recomendada)
1. **[Brecha]** — Riesgo: [Alto/Crítico] — Remediación: [acción concreta]

### Iniciativas para Spark
| ID | Iniciativa | Valor | Esfuerzo | Riesgo |
|----|------------|-------|----------|--------|
| N-01 | [...] | 1-5 | 1-5 | 1-5 |
```

## Common Patterns by Org Type

**Startups (< 10 engineers):** Usually at Level 1-2. Most impactful quick win: enable Dependabot + block secrets in PRs. Takes 1 day.

**MiPyMEs (10–30 engineers):** Usually at Level 2-3. Focus: SAST in PRs + secrets management + multi-stage pipeline.

**Scale-ups (30–100 engineers):** Usually at Level 3-4. Gaps typically in: supply chain security, compliance evidence, policy-as-code.
