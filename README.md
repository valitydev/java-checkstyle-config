# java-checkstyle-config
Our check style config based on Google style

Usage example:

```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-checkstyle-plugin</artifactId>
  <version>3.1.2</version>
  <dependencies>
    <dependency>
      <groupId>com.puppycrawl.tools</groupId>
      <artifactId>checkstyle</artifactId>
      <version>8.41</version>
    </dependency>
  </dependencies>
  <executions>
    <execution>
      <id>validate</id>
      <phase>validate</phase>
      <configuration>
        <configLocation>${checkstyle.config.path}</configLocation>
        <encoding>UTF-8</encoding>
        <failsOnError>true</failsOnError>
        <consoleOutput>true</consoleOutput>
        <violationSeverity>warning</violationSeverity>
        <includeTestSourceDirectory>true</includeTestSourceDirectory>
        <suppressionsLocation>${checkstyle.config.suppressions.path}</suppressionsLocation>
      </configuration>
      <goals>
        <goal>check</goal>
      </goals>
    </execution>
  </executions>
</plugin>
```

### SuppressWarnings examples

First path — override `${checkstyle.config.suppressions.path}` in project with `checkstyle-suppressions.xml` file and fill with your filters

pom.xml:
```xml
<properties>
    <checkstyle.config.suppressions.path>./src/main/resources/checkstyle/checkstyle-suppressions.xml</checkstyle.config.suppressions.path>
</properties>
```

checkstyle-suppressions.xml:
```xml
<?xml version="1.0"?>

<!DOCTYPE suppressions PUBLIC
        "-//Checkstyle//DTD SuppressionFilter Configuration 1.0//EN"
        "https://checkstyle.org/dtds/suppressions_1_0.dtd">

<suppressions>
        <suppress checks="LineLength"
                  files="AppConfig.java"
                  lines="0-9999"/>
</suppressions>
```

Other path — use `@SuppressWarnings`:
```java 
@SuppressWarnings({"checkstyle:%module_name%", "checkstyle:%module_name%""})
``` 

Example:
```java 
@SuppressWarnings({"checkstyle:parametername", "checkstyle:localvariablename"})
``` 
