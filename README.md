# Arquetipo KarateDSL v1.2.0 - Gradle

Proyecto Gradle Base para Karate framework
## Herramientas

1. KarateDSL v1.2.0
2. JavaJDK 17
3. karate-junit5 v1.2.0
4. VScode 1.67
4. KarateRunner

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

## Contruido
1. Arquetipo de Maven
```sh
mvn archetype:generate \
-DarchetypeGroupId=com.intuit.karate \
-DarchetypeArtifactId=karate-archetype \
-DarchetypeVersion=1.2.0 \
-DgroupId=buhobyte \
-DartifactId=KarateDSL-Archetype-Gradle
```
2. Convertir projecto maven a Gradle
```sh
gradle init --type pom
```
3. Agregar TestExecution a build.gradle para plugins VScode Intellij
```groovy
sourceSets {
    test {
        resources {
            srcDirs = ['src/test/resources','src/test/java'] 
            // define `src/test/resources` and `src/test/java` as resource folders
            exclude '**/*.java'
        }
    }
}

test {
    useJUnitPlatform () // enable junit5 platform
}

// Necessary for plugins IntellijIdea and Vscode - TestRunner
task karateExecute(type: JavaExec) {
    classpath = sourceSets.test.runtimeClasspath
    main = System.properties.getProperty('mainClass')
}
```