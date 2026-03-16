---
name: org-context
description: Capture, structure, and maintain the organizational context of a company being assessed. Use this skill whenever any agent needs to reference or document the current state, constraints, technology stack, team size, or maturity level of the organization. Trigger whenever the conversation involves an organization's profile, technology landscape, team structure, or business context — even if the user doesn't explicitly mention 'context'. All agents in the devsecops-crew should apply this skill to ensure they work from a shared, consistent understanding of the organization.
---

# Org Context — Shared Organizational Context

This skill provides a shared structure for capturing and referencing organizational context across all agents in the assessment crew. It ensures every agent works from the same foundational understanding of the organization being evaluated.

## When to apply this skill

Apply this skill when:
- Starting any assessment (fill the context from what's available)
- Any agent needs to adapt its output to the organization's size, maturity, or constraints
- A user provides new information about the organization mid-session
- The context needs to be passed between agents

## Organizational Context Schema

Always structure and reference organizational context using these dimensions:

### Identification
- **Organization name** (or anonymized identifier)
- **Type:** startup / mype / SME / scale-up / enterprise / non-profit / public sector
- **Industry / vertical**
- **Geographic location / regulatory zone**

### Team
- **Total technical team size** (# engineers)
- **Roles present:** DevOps / SRE / Security / Platform / Backend / Frontend / Data / QA
- **Engineering maturity:** junior-heavy / mixed / senior-heavy
- **Team structure:** single team / multiple squads / distributed

### Technology
- **Cloud provider(s):** AWS / GCP / Azure / hybrid / on-premise
- **Primary languages/frameworks**
- **Repository platform:** GitHub / GitLab / Bitbucket / Azure DevOps
- **Current CI/CD:** none / basic / advanced (specify tooling)
- **Observability:** none / basic logs / full stack (specify tooling)
- **Key services / products**

### Constraints
- **Budget:** unconstrained / limited / very limited / unknown
- **Regulatory requirements:** none / industry-specific / government / GDPR / PCI-DSS / SOC2
- **Technical debt level:** low / medium / high / critical
- **Time constraints:** known deadlines or release pressures

### Current Maturity Signals
- **Deployment frequency:** multiple/day / daily / weekly / monthly / less
- **Last major incident / recovery time** (if known)
- **Known pain points** (from the team or stakeholders)
- **Previous transformation attempts** (what worked, what didn't)

## How to use this context

Every agent should:
1. **Read** the org context before producing any output
2. **Adapt** recommendations to the actual team size and budget — never propose enterprise-grade solutions to a 3-person startup without acknowledging the gap
3. **Flag** missing context that would materially change the assessment, rather than assuming
4. **Update** the context if new information emerges during the assessment

## Context quality levels

- **Full context:** All dimensions known → deep, specific assessment
- **Partial context:** Key dimensions known → assessment with stated assumptions
- **Minimal context:** Only type + size known → high-level assessment with explicit gaps flagged

Always state your assumptions when context is partial. Use this format:

```
> Assumption: [what was assumed] because [why]. If this is incorrect, the recommendation for [area] may change.
```
