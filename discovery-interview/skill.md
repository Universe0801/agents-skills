---
name: discovery-interview
description: Conduct structured discovery interviews to collect organizational context from stakeholders before a technical assessment. Use this skill when Scout needs to gather information about an organization's current state, technology stack, processes, team structure, or pain points. Trigger when the user provides partial context and more information is needed, when starting a new organizational assessment, or when a stakeholder is available to answer questions. This skill guides the conversation to extract maximum signal with minimum friction.
---

# Discovery Interview — Structured Organizational Intake

This skill guides Scout through a structured but conversational discovery process to build the Organizational Context Report that feeds all other agents.

## Principles

- Ask questions in a conversational flow, not as a cold questionnaire
- Group related questions — don't jump between unrelated topics
- Start broad, then drill into areas of highest signal
- One topic at a time: don't overwhelm with multiple questions at once
- If the user provides context upfront (e.g., "we're a fintech startup of 15 engineers"), acknowledge it and skip to what's missing
- Be curious, not interrogating

## Discovery Flow

### Phase 1 — Organization Profile (start here)
Goal: understand who we're talking about

Opening question:
> "Para empezar, cuéntame un poco sobre la organización: ¿qué hacen, cuántas personas hay en el equipo técnico y en qué cloud o infraestructura trabajan actualmente?"

From the response, extract: org type, industry, team size, cloud. Fill gaps with follow-ups:
- "¿Cuántos de esos [N] son ingenieros de backend/infra/DevOps?"
- "¿Tienen algún rol dedicado a seguridad, plataforma o confiabilidad?"

### Phase 2 — Delivery Process
Goal: understand how they ship software today

> "¿Cómo es el ciclo típico de un cambio en producción? Desde que un dev termina el código hasta que está disponible para los usuarios."

Listen for: deployment frequency, manual steps, CI/CD existence, bottlenecks.

Follow-ups:
- "¿Cuánto tarda ese proceso típicamente? ¿Horas, días?"
- "¿Tienen pipeline de CI/CD? ¿Con qué herramienta?"
- "¿Los deploys son frecuentes o los agrupan en releases grandes?"

### Phase 3 — Pain Points
Goal: surface the most urgent problems

> "¿Cuál es el mayor dolor que tiene el equipo hoy relacionado con cómo entregan o operan el software? Si tuvieran que arreglar una sola cosa esta semana, ¿qué sería?"

This is the highest-signal question. Let them talk. Take notes.

### Phase 4 — Incidents & Reliability
Goal: understand operational health

> "¿Tienen incidentes en producción con frecuencia? ¿Tienen algún proceso para resolverlos y aprender de ellos?"

Follow-ups:
- "¿Cuánto tardan típicamente en resolver un incidente?"
- "¿Hay on-call? ¿Cómo está organizado?"

### Phase 5 — Security & Compliance
Goal: identify security posture and regulatory context

> "¿Tienen algún requerimiento de compliance o seguridad específico? Por ejemplo, ¿manejan datos de tarjetas, datos de salud, o tienen clientes enterprise que exijan certificaciones?"

Follow-ups:
- "¿Tienen controles de seguridad en el pipeline? ¿Se escanea el código automáticamente?"
- "¿Hubo algún incidente de seguridad en el pasado reciente?"

### Phase 6 — Constraints & Context
Goal: calibrate the depth of recommendations

> "Por último, ¿cuál es el contexto de este ejercicio? ¿Están buscando priorizar inversiones, tienen un problema urgente que resolver, o quieren una visión general de hacia dónde ir?"

Also surface:
- "¿Tienen restricciones de presupuesto que debamos tener en mente?"
- "¿Han intentado mejoras similares antes? ¿Qué funcionó y qué no?"

## Handling Common Situations

**User gives very complete context upfront:**
→ Acknowledge, confirm key facts, jump directly to output without asking questions.

**User gives minimal context:**
→ Follow the full flow above, but keep it conversational.

**User is in a hurry:**
→ Prioritize Phase 1 + Phase 3 (profile + pain points). That's the minimum viable context.

**User provides contradictory information:**
→ Flag it gently: "Antes mencionaste X, pero ahora describes Y — ¿podrías aclarar?"

## Output after Discovery

After completing the interview, produce the **Organizational Context Report** using the `org-context` skill schema, plus:

```markdown
## Resumen ejecutivo del Discovery

**Top 3 pain points identificados:**
1. [...]
2. [...]
3. [...]

**Señales de alerta:**
- [Cualquier hallazgo crítico que los demás agentes deben conocer antes de evaluar]

**Contexto para Nexus / Pulse / Forge:**
[Nota directa sobre qué aspectos son más relevantes para cada evaluador dado este contexto]
```
