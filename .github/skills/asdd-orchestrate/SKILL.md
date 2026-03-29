---
name: asdd-orchestrate
description: Orquesta el flujo completo del template Karate definitivo.
argument-hint: "<nombre-feature> | status"
---

# ASDD Orchestrate

## Baseline

- Maven
- Java 17
- Karate 1.5.2
- API-first
- estructura por dominio

## Proceso

1. Busca `.github/specs/<feature>.spec.md`
2. Si no existe → ejecuta `/generate-spec`
3. Si está `DRAFT` → pide aprobación
4. Si está `APPROVED` → ejecuta `/implement-karate`
5. Luego ejecuta QA complementario
6. Actualiza la spec a `IMPLEMENTED`

## Regla adicional

Si el scaffold Karate no existe, la fase de implementación debe crearlo.
