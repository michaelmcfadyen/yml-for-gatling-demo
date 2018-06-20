## Yml For Gatling Demo Project

This project demonstrates the two ways you can use [yml-for-gatling](https://github.com/michaelmcfadyen/yml-for-gatling).

### 1. Directly using the jar

Firstly build [yml-for-gatling](https://github.com/michaelmcfadyen/yml-for-gatling) as a jar and install in your repo of
choice using `mvn clean [package/install/deploy]` depending on where you want to push the jar to.

When executing the jar two system properties must be passed in
    
    - gatling.base.url - base url of target systmem (http://localhost:8080)
    - gatling.yml.file - relative path to the yml file describing the gatling simulation (./example.yml)
    
The complete command for this project would be
    
         java -Dgatling.yml.file=./example.yml -Dgatling.base.url=http://localhost:8080 -jar yml-for-gatling-1.0.0.jar
         
### 2. Using maven

Firstly, add a pom to your project with a dependency on yml-for-gatling. 

    <dependency>
        <groupId>io.mcfadyen.gatling</groupId>
        <artifactId>yml-for-gatling</artifactId>
        <version>VERSION</version>
    </dependency>
    
Also, add the maven shade plugin to build your test as a fat jar and ensure the mainClass is as follows
    
    <mainClass>io.mcfadyen.gatling.Engine</mainClass>
    
Include any and all of your simulation config files under src/main/resources.

Now build the jar using 
    
    mvn clean package
    
When executing the jar two system properties must be passed in
    
    - gatling.base.url - base url of target systmem (http://localhost:8080)
    - gatling.yml.file - classpath of the yml file describing the gatling simulation (example.yml)

The complete command for this project would be
    
    mvn clean package
    java -Dgatling.yml.file=example.yml -Dgatling.base.url=http://localhost:8080 -jar target/yml-for-gatling-demo-1.0-SNAPSHOT.jar
