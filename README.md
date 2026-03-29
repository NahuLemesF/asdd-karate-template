# ASDD — Template Definitivo para Karate

Framework de automatización asistida por IA para convertir `requirements.md` en un proyecto Karate funcional siguiendo un baseline estable y reusable entre proyectos.

```text
Requerimiento → Spec de Automatización → Scaffold Maven/Karate → Features por dominio → QA Assets
```

## Baseline del template

Este template queda aterrizado a estas decisiones:

- **Build tool:** Maven
- **Java:** 17
- **Karate:** 1.5.2
- **Tipo de automatización:** API-first
- **Organización:** por dominio funcional
- **Runners:** uno por dominio
- **Tags:** `@smoke`, `@regression`, `@negative`, `@auth`, `@contract`, `@wip`
- **Ambiente por defecto:** `qa`
- **Ambientes adicionales:** opcionales, solo si el proyecto o el requerimiento los piden explícitamente
- **Auth configurable:** `bearer`, `oauth`, `login`

## Qué genera ASDD

Si el repo destino no tiene estructura Karate, el framework debe poder generar:

- `pom.xml`
- `mvnw`
- `mvnw.cmd`
- `.mvn/wrapper/**`
- `karate-config.js`
- `src/test/java/<base-package-path>/runners/*.java`
- `src/test/resources/features/**`
- `src/test/resources/data/**`
- `src/test/resources/helpers/**`
- `src/test/resources/schemas/**`

Y, además:

- specs en `.github/specs/`
- artefactos QA en `docs/output/qa/`

## Flujo

### Opción A — Orquestación completa

```text
/asdd-orchestrate nombre-feature
```

### Opción B — Paso a paso

```text
/generate-spec nombre-feature
```

Apruebas la spec:

```yaml
status: APPROVED
```

Luego:

```text
/implement-karate nombre-feature
/qa-task nombre-feature
```

> Sin `status: APPROVED` no se crea ni modifica automatización Karate.

## Convenciones del proyecto generado

```text
.
├── pom.xml
├── mvnw
├── mvnw.cmd
├── .mvn/
│   └── wrapper/
├── karate-config.js
├── src/
│   └── test/
│       ├── java/
│       │   └── <base-package-path>/
│       │       └── runners/
│       │           ├── <Domain>Runner.java
│       │           └── <AnotherDomain>Runner.java
│       └── resources/
│           ├── features/
│           │   ├── <dominio>/
│           │   │   ├── <flujo-a>.feature
│           │   │   ├── <flujo-b>.feature
│           │   │   └── <flujo-c>.feature
│           │   └── <otro-dominio>/
│           ├── data/
│           │   ├── <dominio>/
│           │   └── <otro-dominio>/
│           ├── helpers/
│           │   ├── auth/
│           │   └── common.js
│           └── schemas/
│               ├── <dominio>/
│               └── <otro-dominio>/
└── .github/
```

## Ejecución esperada

```text
./mvnw test
./mvnw test -Dkarate.env=qa
./mvnw test -Dkarate.options="--tags @smoke"
```

## Documentación clave

- `.github/README.md`
- `.github/AGENTS.md`
- `.github/copilot-instructions.md`
- `.github/instructions/karate.instructions.md`
- `.github/specs/README.md`

## Nota sobre la versión de Karate

El template queda pinneado en **Karate 1.5.2**. Según las notas oficiales de **v1.5.0**, desde esa serie Karate requiere **Java 17** y el Maven `group-id` cambió de `com.intuit.karate` a `io.karatelabs`, mientras los imports Java siguen en `com.intuit.karate.*` en la serie `1.5.x`. Fuente oficial:

- https://github.com/karatelabs/karate/releases
