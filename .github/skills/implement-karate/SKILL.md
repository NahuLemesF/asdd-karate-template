---
name: implement-karate
description: Bootstrapea o implementa un proyecto Karate sobre Maven + Java 17 organizado por dominio.
argument-hint: "<nombre-feature>"
---

# Implement Karate

## Baseline del template

- Maven
- Java 17
- Karate 1.5.2
- API-first
- runners por dominio

## Prerequisitos

1. Leer `.github/specs/<feature>.spec.md`
2. Leer `.github/instructions/karate.instructions.md`
3. Revisar si ya existe scaffold Karate

## Si el scaffold no existe

El scaffold base ya está pre-built en el repo template. Verifica que estos archivos existan:

- `pom.xml` — con `<testResources>` para `src/test/java` excluyendo `**/*.java`
- `mvnw`, `mvnw.cmd`, `.mvn/wrapper/maven-wrapper.properties`
- `src/test/java/karate-config.js`
- `src/test/java/logback-test.xml`
- `src/test/java/<base-package-path>/` — package placeholder
- `src/test/resources/helpers/auth/` — auth.feature, oauth.feature, login.feature
- `src/test/resources/helpers/common.js`
- `src/test/resources/data/`
- `src/test/resources/schemas/`

Si faltan, generarlos siguiendo la estructura del archetype oficial de Karate.

## Orden recomendado

```text
Verificar scaffold Maven (ya pre-built)
→ Ajustar package/groupId si necesario
→ config (karate-config.js ya en src/test/java/)
→ auth/common helpers (ya en src/test/resources/helpers/)
→ data files en src/test/resources/data/<dominio>/
→ schemas en src/test/resources/schemas/<dominio>/
→ features + runner del dominio en src/test/java/<package>/<dominio>/
```

## Convenciones

- Organización por dominio
- **Runner y features viven en la misma carpeta**: `src/test/java/<package>/<dominio>/`
- El runner usa `Karate.run().relativeTo(getClass())` para descubrir features
- Package del runner: `[base.package].[dominio]` (no `.runners`)
- `karate-config.js` vive en `src/test/java/`, NO en la raíz
- Tags estándar del template
- Auth configurable: `bearer`, `oauth`, `login`
- Env por defecto: `qa`
- Envs adicionales: solo si el requirement o el proyecto los necesitan
- Para Karate `1.5.x`, `pom.xml` debe usar `io.karatelabs:karate-junit5`
- Los imports Java pueden seguir en `com.intuit.karate.*` en la serie `1.5.x`
- `pom.xml` debe incluir `<testResources>` con `src/test/java` excluyendo `**/*.java`

## Regla obligatoria de wrapper

- Si el proyecto no tiene `mvnw`, `mvnw.cmd` y `.mvn/wrapper/`, debes generarlos.
- Preferir Maven Wrapper estándar en vez de inventar scripts manuales.
- El proyecto debe quedar ejecutable con `./mvnw test`.

## Restricciones

- No escribir código de producto
- No convertir el template en multi-stack
