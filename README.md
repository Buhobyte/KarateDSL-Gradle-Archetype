# Arquetipo KarateDSL v1.2.0 - Gradle

Proyecto Gradle Base para Karate framework
## Herramientas

1. KarateDSL v1.2.0
2. JavaJDK 17
3. karate-junit5 v1.2.0
4. VScode 1.67
    4.1. KarateRunner

## Inicio

1.	Contruir proyecto y descargar dependencias
```sh
gradle build
```
2.	Usar gradlew localmente
```sh
gradle wrapper
./gradlew clean test -Dkarate.options="--tags @users"
```