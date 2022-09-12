maven-resources
===============
This repo hosts shared Maven resources useful for configuring builds in a common manner.

maven-checkstyle-plugin
=======================
This directory hosts a shared [Maven Checkstyle Plugin](https://maven.apache.org/plugins/maven-checkstyle-plugin/index.html)
configuration, [imanage_checks.xml](maven-checkstyle-plugin/imanage_checks.xml). This configuration is
publicly accessible via the following URL, which can be used as the value of
[configLocation](https://maven.apache.org/plugins/maven-checkstyle-plugin/check-mojo.html#configLocation),
or as the URL of a configuration file in the IntelliJ checkstyle plugin.

    https://raw.githubusercontent.com/iManageDave/maven-resources/master/maven-checkstyle-plugin/imanage_checks.xml

Also, a shared [suppressions filter](https://maven.apache.org/plugins/maven-checkstyle-plugin/examples/suppressions-filter.html),
[checkstyle-suppressions.xml](maven-checkstyle-plugin/checkstyle-suppressions.xml), is available for
excluding Dagger generated sources. The more desirable [&lt;excludes&gt;](https://maven.apache.org/plugins/maven-checkstyle-plugin/check-mojo.html#excludes)
did not work despite hours of trying.

    https://raw.githubusercontent.com/iManageDave/maven-resources/master/maven-checkstyle-plugin/checkstyle-suppressions.xml

An example `pom.xml` snippet using these configurations follows.

    <project>
        ...
        <build>
            <pluginManagement>
                <plugins>
                    ...
                    <plugin>
                        <groupId>org.apache.maven.plugins</groupId>
                        <artifactId>maven-checkstyle-plugin</artifactId>
                        <version>3.2.0</version>
                    </plugin>
                    ...
                </plugins>
            </pluginManagement>

            <plugins>
                ...
                <plugin>
                    <groupId>org.apache.maven.plugins</groupId>
                    <artifactId>maven-checkstyle-plugin</artifactId>
                    <configuration>
                        <configLocation>https://raw.githubusercontent.com/iManageDave/maven-resources/master/maven-checkstyle-plugin/imanage_checks.xml</configLocation>
                        <linkXRef>false</linkXRef>
                        <suppressionsLocation>https://raw.githubusercontent.com/iManageDave/maven-resources/master/maven-checkstyle-plugin/checkstyle-suppressions.xml</suppressionsLocation>
                    </configuration>
                    <dependencies>
                        <dependency>
                            <groupId>com.puppycrawl.tools</groupId>
                            <artifactId>checkstyle</artifactId>
                            <version>10.3.3</version>
                        </dependency>
                    </dependencies>
                </plugin>
                ...
            </plugins>
        </build>
    </project>

versions-maven-plugin
=====================
This directory hosts a shared [Versions Maven Plugin](http://www.mojohaus.org/versions-maven-plugin/index.html)
[rule set](https://www.mojohaus.org/versions-maven-plugin/version-rules.html),
[rules.xml](versions-maven-plugin/rules.xml).  This rule set is publicly accessible via the following
URL.

    https://raw.githubusercontent.com/iManageDave/maven-resources/master/versions-maven-plugin/rules.xml

An example `pom.xml` snippet using this rule set follows.

    <project>
        ...
        <properties>
            ...
            <maven.version.rules>https://raw.githubusercontent.com/iManageDave/maven-resources/master/versions-maven-plugin/rules.xml</maven.version.rules>
            ...
        </properties>
        ...
        <build>
            <pluginManagement>
                <plugins>
                    ...
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>versions-maven-plugin</artifactId>
                        <version>2.11.0</version>
                    </plugin>
                    ...
                </plugins>
            </pluginManagement>
            ...
            <plugins>
                ...
                <plugin>
                    <groupId>org.codehaus.mojo</groupId>
                    <artifactId>versions-maven-plugin</artifactId>
                    <executions>
                        <execution>
                            <id>display-dependency-updates</id>
                            <phase>compile</phase>
                            <goals>
                                <goal>display-dependency-updates</goal>
                                <goal>display-plugin-updates</goal>
                            </goals>
                        </execution>
                    </executions>
                </plugin>
                ...
            </plugins>
        </build>
    </project>
