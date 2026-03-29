---
name: performance-analyzer
description: Define estrategias de performance para suites basadas en Karate + Gatling.
argument-hint: "<nombre-feature | nombre-proyecto>"
---

# Performance Analyzer

## Objetivo

Planificar performance cuando la spec tenga SLAs o el usuario lo pida explícitamente.

## Tipos de prueba

- **Load**: carga esperada
- **Stress**: punto de quiebre
- **Spike**: picos abruptos
- **Soak**: resistencia prolongada

## Entregable

Genera `docs/output/qa/<feature>-performance.md`:

```markdown
# Plan de Performance — [Feature]

## SLAs
| Métrica | Objetivo |
|---------|----------|
| P95 | < 800 ms |
| Error rate | < 1% |

## Estrategia
- Base funcional cubierta con Karate
- Performance planificada con Karate + Gatling
```

## Reglas

- No mezclar performance con regresión funcional en el mismo reporte sin separación
- Documentar ambiente, datos, volumen y umbrales
