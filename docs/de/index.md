---
template: home_de.html
---

<!-- Placeholder to make the page render -->

<div class="mdx-grid-container" markdown>
<div class="mdx-grid-wrapper mdx-grid-size" markdown>
<div class="mdx-grid-child" markdown>
## Loslegen

JDA wird über MavenCentral verteilt und ermöglicht dir eine einfache Einbindung in dein Java-Projekt durch den Dependency Manager deiner Wahl.
</div>
<div class="mdx-grid-child" markdown>
## Konfiguration

=== "Maven"
    ```xml
    <dependency>
      <groupId>net.dv8tion</groupId>
      <artifactId>JDA</artifactId>
      <version>VERSION</version>
    </dependency>
    ```

=== "Maven (No Audio)"
    ```xml
    <dependency>
      <groupId>net.dv8tion</groupId>
      <artifactId>JDA</artifactId>
      <version>VERSION</version>
      <exclusions>
        <exclusion>
          <groupId>club.minnced</groupId>
          <artifactId>opus-java</artifactId>
        </exclusion>
      </exclusions>
    </dependency>
    ```

=== "Gradle"
    ```groovy
    repositories {
      mavenCentral()
    }
    
    dependencies {
      implementation("net.dv8tion:JDA:VERSION")
    }
    ```

=== "Gradle (No Audio)"
    ```groovy
    repositories {
      mavenCentral()
    }
    
    dependencies {
      implementation("net.dv8tion:JDA:VERSION") {
        exclude module: 'opus-java'
      }
    }
    ```

</div>
</div>
</div>
