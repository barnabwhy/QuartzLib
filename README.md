zLib [![Build Status](http://jenkins.carrade.eu/job/zLib/badge/icon)](http://jenkins.carrade.eu/job/zLib/)
==========

Helper library for Bukkit plugins development.

For the `master` branch:
 - [builds available here](http://jenkins.carrade.eu/job/zLib/);
 - [JavaDoc autogenerated here](http://jenkins.carrade.eu/job/zLib/javadoc/).


### How to use this library in your plugin?

If you are using Maven to build your plugin, follow these simple steps. Currently, the zLib requires **Java 7** or later and **Bukkit 1.8.3** or later.

1. Add our Maven repository to your `pom.xml` file.
   
    ```xml
        <repository>
            <id>zDevelopers</id>
            <url>http://maven.carrade.eu/artifactory/snapshots</url>
        </repository>
    ```

2. Add the zLib as a dependency.
   
    ```xml
        <dependency>
            <groupId>fr.zcraft</groupId>
            <artifactId>zlib</artifactId>
            <version>0.99-SNAPSHOT</version>
        </dependency>
    ```
    
3. Add the shading plugin to the build. Replace **`YOUR.OWN.PACKAGE`** with your own package.
    
   ```xml
        <build>
            ...
            <plugins>
                ...
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-shade-plugin</artifactId>
                    <version>2.3</version>
                    <configuration>
                        <artifactSet>
                            <includes>
                                <include>fr.zcraft:zlib</include>
                            </includes>
                        </artifactSet>
                        <relocations>
                            <relocation>
                                <pattern>fr.zcraft.zlib</pattern>
                                <shadedPattern>YOUR.OWN.PACKAGE</shadedPattern>
                            </relocation>
                        </relocations>
                    </configuration>
                    <executions>
                        <execution>
                            <phase>package</phase>
                            <goals>
                                <goal>shade</goal>
                            </goals>
                        </execution>
                    </executions>
                </plugin>
                ...
            </plugins>
            ...
        </build>
   ```
   
4. Build your project as usual, as example with the following command from your working directory, or using an integrated tool from your IDE.
   
   ```bash
   mvn clean install
   ```
