![build badge](https://github.com/m1ad3n/maven-kickstart/actions/workflows/maven.yml/badge.svg)
# Maven Kickstart

This is a basic setup for a Java application using Maven. It includes the necessary configuration for:

- Running the application using the exec-maven-plugin
- Running tests with JUnit 5

### Project Structure

This project follows a standard Maven directory structure:

```
.
├── pom.xml               # Maven configuration file
└── src
    ├── main
    │   └── java          # Java source code
    └── test
        └── java          # Test classes
```

### Maven Configuration

The pom.xml contains configurations for the following:

##### exec-maven-plugin
 To run the Java application, we use the exec:java plugin. You can execute the application directly from Maven using the following command:
```
mvn exec:java
```
Ensure that the main class is defined in the pom.xml like this:
```xml
<plugin>
    <groupId>org.codehaus.mojo</groupId>
    <artifactId>exec-maven-plugin</artifactId>
    <version>3.5.0</version>
    <configuration>
        <mainClass>com.example.Main</mainClass> <!-- Replace with your main class -->
    </configuration>
</plugin>
```

##### JUnit 5 Configuration

The project is set up to run tests with JUnit 5. The configuration in pom.xml ensures JUnit 5 is used for testing.
```xml
<dependencies>
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter</artifactId>
        <version>5.11.3</version>
        <scope>test</scope>
    </dependency>
</dependencies>
```

Additionally, configure the maven-surefire-plugin to use JUnit 5:
```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>3.5.2</version>
            <configuration>
                <suiteXmlFiles>
                    <suiteXmlFile>src/test/resources/testng.xml</suiteXmlFile>
                </suiteXmlFiles>
            </configuration>
        </plugin>
    </plugins>
</build>
```

##### Running Tests

To run your tests with JUnit 5, simply execute:
```
mvn test
```
This will run all tests located in src/test/java

### Conclusion

This setup provides a basic Maven configuration for a Java application with the ability to run the application and tests using Maven goals. You can extend it with more dependencies, plugins, or custom configurations as needed for your project.
