---
name: qa-task
description: Ejecuta QA complementario para el template Karate definitivo.
agent: QA Agent
---

Ejecuta el QA Agent para el feature indicado.

**Feature**: ${input:featureName:nombre del feature en kebab-case}

## Reglas del QA

- Referenciar tags reales
- Validar estructura por dominio
- Verificar trazabilidad entre criterios y features
- Considerar auth `bearer|oauth|login`
- Considerar `qa` como default y ambientes extra solo si la spec los define
