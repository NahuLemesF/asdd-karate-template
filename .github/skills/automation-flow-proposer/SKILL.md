---
name: automation-flow-proposer
description: Prioriza qué flujos automatizar primero con Karate según repetitividad, impacto, estabilidad y costo manual.
argument-hint: "<nombre-feature | nombre-proyecto>"
---

# Automation Flow Proposer

## Criterios

- Repetitivo
- Estable
- Alto impacto
- Alto costo manual

## Enfoque

El framework ya está estandarizado en **Karate**. Esta skill no elige herramienta: decide **qué automatizar primero** y con qué tags o suites conviene organizarlo.

## Entregable

Genera `docs/output/qa/automation-proposal.md`:

```markdown
# Propuesta de Automatización con Karate

| Flujo | ROI | Prioridad | Suite sugerida | Tags |
|------|-----|-----------|----------------|------|
| Login API | 4/4 | P1 | smoke + regression | @smoke @auth |
```

## Reglas

- Priorizar smoke primero
- Dejar explícito qué queda para regression
- Si un flujo aún es inestable, recomendar postergarlo antes de automatizar
