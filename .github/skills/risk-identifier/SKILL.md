---
name: risk-identifier
description: Identifica y clasifica riesgos de calidad usando la Regla ASD para priorizar cobertura Karate.
argument-hint: "<nombre-feature | nombre-proyecto>"
---

# Risk Identifier

## Regla ASD

```text
ALTO  → cobertura obligatoria en Karate
MEDIO → cobertura recomendada
BAJO  → cobertura opcional o backlog
```

## Factores de riesgo alto

- autenticación y autorización
- datos sensibles
- integraciones externas
- operaciones irreversibles
- reglas de negocio críticas
- SLAs contractuales

## Entregable

Genera `docs/output/qa/<feature>-risks.md`:

```markdown
# Matriz de Riesgos — [Feature]

| ID | Riesgo | Nivel | Cobertura Karate | Tags sugeridos |
|----|--------|-------|------------------|----------------|
| R-001 | Token inválido permite acceso | ALTO | Obligatoria | @auth @negative |
```

## Proceso

1. Leer la spec
2. Evaluar HU, escenarios y endpoints
3. Asignar nivel ASD con justificación
4. Indicar cobertura Karate esperada y tags
