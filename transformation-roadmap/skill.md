---
name: transformation-roadmap
description: Design and produce a prioritized technology transformation roadmap for an organization based on DevSecOps, SRE/DORA, and Platform Engineering assessments. Use this skill when Spark needs to synthesize findings from multiple assessment domains, prioritize initiatives using the Value/Effort/Risk framework, and produce a 30/90/180/365-day roadmap with quick wins, structural improvements, and strategic initiatives. Trigger whenever the conversation moves from diagnosis to action planning, when a user asks "what should we do first?", "where do we start?", "give me a roadmap", or when all or most assessment domains have been evaluated. Also trigger if the user skips assessment and asks directly for transformation recommendations — in that case, document assumptions explicitly.
---

# Transformation Roadmap — From Diagnosis to Action

This skill guides Spark through synthesizing all assessment outputs into a coherent, prioritized transformation roadmap.

## Before You Start

Confirm inputs available:
- [ ] Org context (from Scout / `org-context` skill)
- [ ] DevSecOps assessment (from Nexus)
- [ ] SRE/DORA assessment (from Pulse)
- [ ] Platform DX assessment (from Forge)

If any input is missing, proceed with available data and flag assumptions clearly.

## Step 1: Consolidate Initiatives

Collect all initiatives from Nexus (N-XX), Pulse (P-XX), and Forge (F-XX).
De-duplicate: if multiple agents recommended the same initiative (e.g., "implement structured logging"), merge into one.
Assign a unified ID (T-01, T-02...) and note which domains benefit.

## Step 2: Score Each Initiative (V/E/R)

Rate each initiative on three dimensions (1–5 scale):

**Value (V) — Impact if done**
| Score | Description |
|-------|-------------|
| 5 | Resolves a critical blocker or enables major capability |
| 4 | High impact on team productivity or system reliability |
| 3 | Clear improvement, meaningful but not urgent |
| 2 | Nice-to-have, limited measurable impact |
| 1 | Cosmetic or very minor improvement |

**Effort (E) — Cost to implement**
| Score | Description |
|-------|-------------|
| 5 | Months of work, team dedication, significant cost |
| 4 | Several weeks, multiple people involved |
| 3 | 1–2 weeks, one or two engineers |
| 2 | Days, one engineer |
| 1 | Hours, one engineer, zero/near-zero cost |

**Risk (R) — Risk of disruption or failure**
| Score | Description |
|-------|-------------|
| 5 | High risk of production disruption or organizational resistance |
| 4 | Significant coordination needed, rollback complex |
| 3 | Moderate risk, manageable with care |
| 2 | Low risk, easily reversible |
| 1 | No risk, purely additive or isolated |

**Priority Score = V / (E × √R)**

Higher score = do first. Use this to rank, but apply judgment for context (regulatory requirements, dependencies).

## Step 3: Map to Horizons

Assign each initiative to a horizon based on score AND dependencies:

| Horizon | Criteria |
|---------|----------|
| **Quick Wins (0–30d)** | Score ≥ 3.0, E ≤ 2, R ≤ 2. Start immediately. |
| **Corto plazo (31–90d)** | Score ≥ 2.0, foundational items that unlock others |
| **Mediano plazo (91–180d)** | Structural improvements requiring planning |
| **Largo plazo (181–365d)** | Strategic transformation, requires org readiness |

**Capacity rule:** Never put more than 3 parallel initiatives per horizon for teams < 10. For teams 10–30: max 5. For teams > 30: use judgment.

## Step 4: Identify Dependencies

Map initiative dependencies as a DAG (Directed Acyclic Graph). Express as:
- `T-03 requires T-01 to be complete`
- `T-07 is enabled by T-04 and T-05`

Group dependent chains and ensure the roadmap respects the order.

## Step 5: Define Success KPIs

For each initiative, define 1–2 measurable success criteria:

Good KPIs:
- "Deployment frequency increases from weekly to daily within 90 days"
- "Lead time for changes drops below 4 hours"
- "0 hardcoded secrets in main branch (verified by scanner)"
- "Onboarding time for new devs < 2 days"

Avoid vague KPIs like "improved security" or "better DX."

## Step 6: Write the Transformation Narrative

Write 3–5 paragraphs that tell the story of transformation:
1. **Hoy:** Honest description of the current state and its cost to the organization
2. **Por qué actuar ahora:** The risk or opportunity cost of staying where they are
3. **El camino:** What the roadmap achieves at each horizon
4. **Cómo se verá diferente:** Concrete, human-scale description of life after transformation (devs shipping faster, fewer incidents waking people up, security not being a blocker)
5. **El primer paso:** Make the first action extremely concrete and achievable

The narrative should motivate, not overwhelm. Avoid jargon in this section.

## Calibration by Org Type

**Startup (< 10 engineers, early stage):**
- Focus on 3–5 quick wins max
- Avoid anything that requires a dedicated platform team
- Prioritize velocity (DORA) and basic security hygiene

**MiPyME / SME (10–30 engineers, growing):**
- Quick wins + structural foundation in 90 days
- Start platform team conversation (even 1 person part-time)
- Balance speed with operational stability

**Scale-up (30–100 engineers):**
- Full roadmap with all four horizons
- Explicit Team Topologies recommendation
- Platform as product is achievable

**Enterprise (100+ engineers):**
- Multi-team coordination required
- Each domain may have its own workstream
- Change management is as important as the technical roadmap

## Output Format

```markdown
## Roadmap de Transformación Tecnológica
### [Nombre Organización] | [Fecha] | Preparado por APEX + Spark

---

### Síntesis del diagnóstico
[5 líneas máximo: situación actual, brechas principales, oportunidad]

**Perfil actual:**
- DevSecOps: Nivel [1-5]
- DORA: [Elite/High/Medium/Low]
- Platform DX: Nivel [1-5]

---

### Iniciativas priorizadas
| ID | Iniciativa | Dominios | V | E | R | Score | Horizonte |
|----|------------|---------|---|---|---|-------|-----------|
| T-01 | [...] | DevSecOps | 5 | 1 | 1 | 5.0 | Quick Win |

---

### Roadmap

#### ⚡ QUICK WINS — 0 a 30 días
> Objetivo: generar momentum y cerrar las brechas de mayor riesgo con mínimo esfuerzo

- [ ] **T-01** [Iniciativa] → KPI: [métrica de éxito]
- [ ] **T-02** [Iniciativa] → KPI: [métrica de éxito]

#### 🔧 CORTO PLAZO — 31 a 90 días
> Objetivo: establecer los fundamentos técnicos y organizacionales

- [ ] **T-03** [Iniciativa] → KPI: [...] *(Depende de: T-01)*
- [ ] **T-04** [Iniciativa] → KPI: [...]

#### 🏗️ MEDIANO PLAZO — 91 a 180 días
> Objetivo: mejoras estructurales que escalan con el crecimiento

- [ ] **T-05** [Iniciativa] → KPI: [...] *(Depende de: T-03, T-04)*

#### 🎯 LARGO PLAZO — 181 a 365 días
> Objetivo: transformación estratégica y madurez sostenible

- [ ] **T-06** [Iniciativa] → KPI: [...]

---

### KPIs de transformación
| KPI | Hoy | Meta 90d | Meta 365d |
|-----|-----|----------|-----------|
| Deployment Frequency | [...] | [...] | [...] |
| Lead Time for Changes | [...] | [...] | [...] |
| MTTR | [...] | [...] | [...] |
| Onboarding time | [...] | [...] | [...] |

---

### Narrativa de transformación
[3-5 párrafos: hoy / por qué / el camino / cómo se verá / primer paso]

---

### Riesgos del roadmap
| Riesgo | Prob. | Impacto | Mitigación |
|--------|-------|---------|------------|
| [...] | Alta/Med/Baja | Alto/Med/Bajo | [...] |

---

### Próximos pasos concretos
1. **Esta semana:** [acción específica, responsable sugerido, tiempo estimado]
2. **Este mes:** [...]
3. **Este trimestre:** [...]
```
