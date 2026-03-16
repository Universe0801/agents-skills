---
name: platform-dx
description: Assess the maturity of the internal developer platform, golden paths, self-service capabilities, and developer experience (DX) in an organization. Use this skill when Forge needs to evaluate how well the engineering platform supports developer productivity, reduces cognitive load, and enables autonomous teams. Trigger for conversations about developer productivity, onboarding time, toolchain complexity, internal platforms, Backstage, golden paths, self-service infrastructure, Team Topologies implementation, or any complaint about how painful it is to develop or deploy — even if the user just says "developers are slow" or "everyone is blocked waiting for ops."
---

# Platform Engineering & DX Assessment — Developer Experience Evaluation

This skill guides Forge through a structured assessment of platform engineering maturity and developer experience quality.

## Framing: Why Platform Engineering Matters

The goal of platform engineering is to reduce cognitive load on development teams so they can focus on delivering value. A good internal platform is a product — not a shared ops team. Assessing platform engineering means asking: "How much of a developer's day is spent fighting the platform vs. building product?"

Use this mental model throughout the assessment:
- **High cognitive load** = developers must know too much to get things done
- **Toil** = repetitive, manual work that could be automated
- **Ticket-ops** = waiting for another team to do something for you

## DX Signal Questions

When formal metrics are unavailable, use these:

> "¿Cuánto tarda un desarrollador nuevo en hacer su primer commit útil en producción? ¿Horas? ¿Días? ¿Una semana?"

> "Cuando un dev quiere desplegar su código, ¿qué pasos tiene que hacer? ¿Cuántos de esos son manuales o requieren esperar a alguien?"

> "¿Cuántas herramientas diferentes necesita dominar un dev para hacer su trabajo del día a día?"

> "¿Existe algún proceso de 'golden path' o plantilla oficial para crear un nuevo servicio? ¿O cada equipo hace lo suyo?"

> "¿Los devs pueden provisionar infraestructura ellos mismos (base de datos, colas, etc.) o tienen que abrir un ticket a ops/infra?"

> "¿Cuánto tarda en ejecutarse la suite de tests local? ¿Minutos? ¿Horas?"

## Evaluation Domains

### Internal Developer Platform (IDP)
Score: ✅ Present | ⚠️ Partial | ❌ Missing

**Service Catalog**
- [ ] Developers can discover all existing services/APIs in one place
- [ ] Each service has documented owner, status, and how to use it
- [ ] Tech radar or approved technology list exists

**Self-Service Capabilities**
- [ ] Developers can create new services from templates without ops involvement
- [ ] Developers can provision standard infrastructure (databases, queues) without tickets
- [ ] Developers can manage deployments without Ops intervention (in non-prod)
- [ ] Environment management (create/destroy test environments) is self-service

**Developer Portal**
- [ ] Internal portal exists (Backstage, Port, Cortex, or equivalent)
- [ ] Portal integrates with CI/CD, monitoring, and docs
- [ ] Adoption rate > 60% of engineering team

### Golden Paths
- [ ] Defined golden path for at least one primary use case (e.g., "new backend service")
- [ ] Golden path includes: repo template + CI/CD + observability + security baseline
- [ ] Documentation for the golden path is up-to-date and findable
- [ ] Teams actually use the golden path (not bypassing it)
- [ ] Golden paths reviewed and updated quarterly

### Developer Experience Metrics
Collect or estimate:

| Metric | Current | Target |
|--------|---------|--------|
| Onboarding time to first prod commit | ? | < 2 days |
| Local test suite execution time | ? | < 5 min |
| PR cycle time (open to merge) | ? | < 4 hours |
| Time from merge to prod deploy | ? | < 1 hour |
| Number of tools a dev must master | ? | < 5 core tools |
| % of time on toil vs product work | ? | < 20% toil |

### Cognitive Load Assessment
- [ ] Developers do NOT need to understand networking/infrastructure to deploy
- [ ] Error messages from the platform are actionable (not cryptic)
- [ ] Runbooks and troubleshooting guides exist and are current
- [ ] Incident resolution doesn't require deep infra knowledge for most devs
- [ ] New team members can be productive without an "infra expert" pairing

### Team Topologies Alignment
Assess current vs. recommended structure:

**Stream-aligned teams** (deliver value end-to-end)
- Do product teams own their services fully, including deployment?
- Can a team release independently without coordinating with other teams?

**Platform team** (reduces cognitive load for stream-aligned teams)
- Is there a dedicated platform team? Or is "ops" doing everything reactively?
- Does the platform team treat their platform as a product with a roadmap?
- Do they gather feedback from developer teams regularly?

**Enabling teams** (temporary upskilling)
- Are there guild structures or enabling teams helping with adoption?
- Is knowledge-sharing formalized (internal docs, workshops)?

**Interaction modes**
- Is the platform consumed as-a-service (low friction) vs. collaboration-heavy (high friction)?
- Are cognitive load conversations happening between teams?

## Maturity Levels

| Level | Description |
|-------|-------------|
| 1 — Caótico | Sin plataforma, alto toil, devs esperan a ops para todo |
| 2 — Reactivo | Ops ayuda cuando se les pide, sin estandarización |
| 3 — Estandarizado | Algunos golden paths, CI/CD templates, docs básicos |
| 4 — Self-service | Devs autónomos en 80% de tareas, IDP básico funcional |
| 5 — Platform as Product | IDP con roadmap, DX medido, NPS de desarrolladores > 7 |

## Output Format

```markdown
## Evaluación Platform Engineering & DX — [Organización]

### Madurez Platform Engineering: [Nivel 1-5] — [Nombre]

### Métricas DX actuales
| Métrica | Valor actual | Target | Gap |
|---------|-------------|--------|-----|
| Onboarding (1er commit prod) | [...] | < 2 días | [...] |
| Test suite local | [...] | < 5 min | [...] |
| Ciclo PR (open→merge) | [...] | < 4 h | [...] |
| Herramientas a dominar | [...] | < 5 | [...] |

### Semáforo por dominio
| Dominio | Estado | Hallazgo principal |
|---------|--------|--------------------|
| Internal Developer Platform | 🔴/🟡/🟢 | [...] |
| Golden Paths | 🔴/🟡/🟢 | [...] |
| Self-Service | 🔴/🟡/🟢 | [...] |
| Cognitive Load | 🔴/🟡/🟢 | [...] |
| Team Topologies | 🔴/🟡/🟢 | [...] |

### Principales fuentes de fricción para los devs
1. [...]
2. [...]
3. [...]

### Iniciativas para Spark
| ID | Iniciativa | DX Impact | Valor | Esfuerzo | Riesgo |
|----|------------|-----------|-------|----------|--------|
| F-01 | [...] | [...] | 1-5 | 1-5 | 1-5 |
```
