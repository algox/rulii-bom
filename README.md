[rulii-bom Maven Central]:https://central.sonatype.com/artifact/org.rulii/rulii-bom
[Apache 2.0 License]:https://opensource.org/licenses/Apache-2.0

# _rulii-bom_
**One version to import for the whole rulii family** <br/>
<sub> _rulii_ &middot; _rulii-spring_ &middot; _rulii-bean-validation_ &middot; _rulii-explorer_ &middot; _Maven and Gradle_ </sub>

---

[![License](https://img.shields.io/badge/license-Apache%202.0-orange.svg)][Apache 2.0 License]
[![Maven Central Version](https://img.shields.io/maven-central/v/org.rulii/rulii-bom)][rulii-bom Maven Central]
![Build](https://github.com/algox/rulii-bom/actions/workflows/maven.yml/badge.svg)

---

**📖 rulii documentation at [rulii.com](https://rulii.com)** &middot; **🧪 Sample projects at [rulii-samples](https://github.com/algox/rulii-samples)**

---

## What is it?

A Maven Bill of Materials (BOM) for the [rulii](https://github.com/algox/rulii) rule engine and its companion
libraries. The libraries release on their own schedules, so a project that uses two or more of them has to find
a set of versions that work together. The BOM publishes that set. Import it once, then declare the rulii
artifacts you use without a version.

## Managed artifacts

| Artifact | What it is | Version in BOM 2.2.0 |
|---|---|---|
| `org.rulii:rulii` | The rule engine | 2.2.0 |
| `org.rulii:rulii-spring` | Spring and Spring Boot integration | 2.2.0 |
| `org.rulii:rulii-bean-validation` | Jakarta Bean Validation provider backed by rulii | 1.0.0 |
| `org.rulii:rulii-explorer-core` | Rule explorer model and services | 1.1.0 |
| `org.rulii:rulii-explorer-ui` | Rule explorer web UI | 1.1.0 |
| `org.rulii:rulii-explorer-spring-boot-starter` | Spring Boot starter for the explorer | 1.1.0 |

Only rulii artifacts are managed. Spring, Jakarta, Janino and GraalJS versions are left to your project or to
the Spring Boot BOM, so importing this BOM never conflicts with another one.

## Getting started

### Maven

```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.rulii</groupId>
            <artifactId>rulii-bom</artifactId>
            <version>2.2.0</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>

<dependencies>
    <dependency>
        <groupId>org.rulii</groupId>
        <artifactId>rulii</artifactId>
    </dependency>
    <dependency>
        <groupId>org.rulii</groupId>
        <artifactId>rulii-spring</artifactId>
    </dependency>
</dependencies>
```

### Gradle

```kotlin
dependencies {
    implementation(platform("org.rulii:rulii-bom:2.2.0"))
    implementation("org.rulii:rulii")
    implementation("org.rulii:rulii-spring")
}
```

### Spring Boot

Keep the Spring Boot BOM (or the Boot parent) as you have it and add this one next to it. The two manage
disjoint sets of artifacts.

## Versioning

The BOM version follows the rulii core version it pins: BOM `2.2.0` pins `rulii` `2.2.0`. When a companion
library releases without a core release, the BOM re-releases with a fourth segment against the same core:
`2.2.0.1`, `2.2.0.2`, and so on. Always use the latest BOM for your rulii line.

## Building

```bash
# Validate the pom and resolve every managed artifact from Maven Central
mvn verify -P check-managed
```

## License

Apache License, Version 2.0. See [LICENSE](LICENSE).
