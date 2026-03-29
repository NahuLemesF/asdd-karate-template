---
name: gherkin-case-generator
description: Genera escenarios Gherkin, datos de prueba y sugerencia de tags para una suite Karate.
argument-hint: "<nombre-feature>"
---

# Gherkin Case Generator

## Proceso

1. Lee la spec `.github/specs/<feature>.spec.md`
2. Identifica flujos críticos, errores y casos borde
3. Genera escenarios Gherkin con lenguaje de negocio
4. Sugiere tags Karate por escenario
5. Documenta datos de prueba sintéticos
6. Guarda en `docs/output/qa/<feature>-gherkin.md`

## Tags sugeridos

| Tipo | Tag recomendado |
|------|-----------------|
| Happy path crítico | `@smoke @regression` |
| Validación / error | `@negative` |
| Auth / permisos | `@auth @negative` |
| Caso borde | `@regression` |

## Reglas

- No usar detalles internos del framework en el Gherkin
- Datos siempre sintéticos
- Cada escenario debe poder mapearse luego a una automatización Karate
