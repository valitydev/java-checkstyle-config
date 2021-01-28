# java-checkstyle-config
Our check style config based on Google style

Usage example:
```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-checkstyle-plugin</artifactId>
    <version>3.1.1</version>
    <executions>
        <execution>
            <id>validate</id>
            <phase>validate</phase>
            <configuration>
                <configLocation>https://raw.githubusercontent.com/rbkmoney/java-checkstyle-config/master/conf/rbkmoney_google_checkstyle.xml</configLocation>
                <encoding>UTF-8</encoding>
                <failsOnError>true</failsOnError>
                <consoleOutput>true</consoleOutput>
                <violationSeverity>warning</violationSeverity>
                <includeTestSourceDirectory>true</includeTestSourceDirectory>
            </configuration>
            <goals>
                <goal>check</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```
