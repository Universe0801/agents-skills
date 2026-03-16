---
name: sre-dora
description: Measure and analyze DORA metrics and SRE maturity for an organization. Use this skill when Pulse needs to assess deployment frequency, lead time for changes, mean time to restore (MTTR), and change failure rate. Also covers SLO/SLA definition, incident management processes, observability stack maturity, on-call practices, and reliability engineering capabilities. Trigger for any conversation about reliability, incidents, uptime, how fast the team ships, how quickly they recover from failures, or whether DORA metrics are being tracked — even informally.
---

# SRE & DORA Assessment — Reliability & Delivery Performance

This skill guides Pulse through a structured SRE maturity and DORA metrics assessment.

## Data Collection Approach

DORA metrics require actual data. Collection strategy by availability:

**Best case:** Organization has dashboards or tooling (LinearB, Sleuth, Jellyfish, DORA dashboard)
→ Request exports or ask for current values directly.

**Typical case:** No formal tracking, but engineers have intuition
→ Use the estimation interview below to approximate values.

**Minimal case:** No data, no intuition
→ Document as "unknown," flag as a finding in itself (not measuring = not managing).

## DORA Metrics Estimation Interview

Use these questions when formal data is unavailable:

**Deployment Frequency:**
> "En una semana típica, ¿cuántos deploys llegan a producción? ¿Uno? ¿Varios? ¿Depende del sprint?"

> "¿Los deploys son frecuentes (cada día o varios al día) o los agrupan en releases grandes (semanal, quincenal, mensual)?"

**Lead Time for Changes:**
> "Desde que un desarrollador termina una feature o fix, ¿cuánto tarda en estar en producción? ¿Horas, días, semanas?"

> "¿Cuál es el paso que más tiempo consume? ¿El testing? ¿Las aprobaciones? ¿El deploy manual?"

**Mean Time to Restore (MTTR):**
> "Cuando hay un incidente que afecta a usuarios, ¿cuánto tardan típicamente en resolverlo? ¿Menos de una hora? ¿Un día? ¿Más?"

> "¿Tienen un proceso claro de respuesta a incidentes o depende de quién esté disponible?"

**Change Failure Rate:**
> "De cada 10 deploys, ¿cuántos generan un problema que requiere rollback o hotfix urgente? ¿Rara vez? ¿Uno o dos? ¿Más?"

## DORA Benchmarks Reference

| Métrica | Elite | High | Medium | Low |
|---------|-------|------|--------|-----|
| Deployment Frequency | Múltiples/día | 1/día–1/semana | 1/sem–1/mes | < 1/mes |
| Lead Time | < 1 hora | 1 día–1 semana | 1 sem–1 mes | > 6 meses |
| MTTR | < 1 hora | < 1 día | < 1 semana | > 6 meses |
| Change Failure Rate | 0–5% | 5–10% | 10–15% | 15–45% |

**Global DORA Profile assignment:**
- All 4 metrics at Elite → **Elite**
- 3+ metrics at High or Elite → **High**
- Mixed scores, at least one Low → **Medium**
- 2+ metrics at Low → **Low**

## SRE Maturity Domains

### Observability
Score: ✅ Present | ⚠️ Partial | ❌ Missing

- [ ] Centralized log aggregation (CloudWatch Logs, ELK, Loki, Datadog)
- [ ] Structured logging (JSON, with request IDs / correlation IDs)
- [ ] Infrastructure metrics (CPU, memory, disk, network — dashboards)
- [ ] Application metrics (RED: Rate, Errors, Duration per service)
- [ ] Distributed tracing for inter-service calls (OpenTelemetry, X-Ray, Jaeger)
- [ ] Alerting configured on meaningful signals (not just CPU > 80%)
- [ ] Dashboards accessible to all engineers (not just ops)

### SLOs & Error Budgets
- [ ] SLOs defined for at least one critical service
- [ ] SLOs tied to user-facing reliability (availability, latency, error rate)
- [ ] Error budget policy: what happens when it's exhausted?
- [ ] Alerts based on SLO burn rate (not raw thresholds)
- [ ] SLO review cadence (quarterly or on incidents)

### Incident Management
- [ ] Defined severity levels (SEV1–SEV3 or equivalent)
- [ ] On-call rotation with documented coverage
- [ ] Runbooks for common failure modes
- [ ] Incident communication protocol (status page, internal channel)
- [ ] Blameless post-mortem process
- [ ] Action items from post-mortems tracked to completion
- [ ] MTTR tracked and trending

### Reliability Engineering
- [ ] Chaos engineering or failure injection practiced (even informally)
- [ ] Load testing before major releases
- [ ] DR (Disaster Recovery) plan with defined RTO/RPO
- [ ] DR drills conducted at least annually
- [ ] Capacity planning process (not purely reactive)

### On-Call Health
- [ ] Reasonable on-call load (< 2 pages/night on average)
- [ ] Off-hours pages only for genuinely critical issues
- [ ] On-call compensation / recognition policy
- [ ] Toil tracking and reduction program

## SRE Maturity Scoring

| Level | Description |
|-------|-------------|
| 1 — Reactivo | Sin monitoreo, incidentes resueltos ad-hoc, no hay on-call formal |
| 2 — Básico | Logs y alertas básicos, incidentes resueltos pero sin proceso |
| 3 — Definido | Observabilidad básica completa, proceso de incidentes, on-call formal |
| 4 — Gestionado | SLOs definidos, post-mortems regulares, MTTR medido |
| 5 — Optimizado | Error budgets activos, chaos engineering, toil < 50% on-call work |

## Output Format

```markdown
## Evaluación SRE & DORA — [Organización]

### Perfil DORA
| Métrica | Valor actual | Perfil | Gap con Elite |
|---------|-------------|--------|---------------|
| Deployment Frequency | [...] | [E/H/M/L] | [...] |
| Lead Time for Changes | [...] | [E/H/M/L] | [...] |
| MTTR | [...] | [E/H/M/L] | [...] |
| Change Failure Rate | [...] | [E/H/M/L] | [...] |

**Perfil DORA global: [Elite / High / Medium / Low]**

### Madurez SRE: [Nivel 1-5] — [Nombre]

### Semáforo SRE
| Dominio | Estado | Hallazgo principal |
|---------|--------|--------------------|
| Observabilidad | 🔴/🟡/🟢 | [...] |
| SLOs / Error Budgets | 🔴/🟡/🟢 | [...] |
| Incident Management | 🔴/🟡/🟢 | [...] |
| Reliability Engineering | 🔴/🟡/🟢 | [...] |
| On-Call Health | 🔴/🟡/🟢 | [...] |

### Principales aceleradores de DORA disponibles
[Top 3 cambios que más impactarían las métricas DORA de esta organización]

### Iniciativas para Spark
| ID | Iniciativa | Métrica DORA impactada | Valor | Esfuerzo | Riesgo |
|----|------------|----------------------|-------|----------|--------|
| P-01 | [...] | [...] | 1-5 | 1-5 | 1-5 |
```
