# octiq-java-maven-compile-error

> Synthetic fixture for testing Octiq's GitHub import of Java projects. Not a real application.

## Scenario

A valid Maven project (no dependencies, Java 17) containing two deliberately broken source files. The failure is purely a compilation failure.

**The compile errors are intentional and must NOT be fixed.**

## What this exercises

- The red-build contract: import still completes as `ready` with `buildGreen:false`
- Parsing javac output into structured per-file, per-line errors
- `Broken.java` (line 5): `incompatible types: String cannot be converted to int`
- `AlsoBroken.java` (line 6): `cannot find symbol` (method `doesNotExist()`)

## Expected result on import

| Field | Expected |
| --- | --- |
| stack | `java` |
| build tool | `maven` |
| Java version | `17` |
| image | `maven:3.9-eclipse-temurin-17` |
| framework | `java` |
| modules | `[]` |
| final phase | `ready` |
| build green | `false` |

Expect exactly two structured errors, one per file.

## Layout

```
pom.xml
src/main/java/com/octiq/fixture/Broken.java
src/main/java/com/octiq/fixture/AlsoBroken.java
```
