This plugin is written for the [Jenkins plugin tutorial](http://wiki.jenkins-ci.org/display/JENKINS/Plugin+tutorial).
It's only useful as an example, and no other practical use.
This branch was used for a webinar with Capital One.

# Quick install

`mvn -Dmaven.test.skip=true -DskipTests=true clean install`

# Quick run

```
rm -rf work/plugins
mvn -Dmaven.test.skip=true -DskipTests=true clean hpi:run
```

# Run tests with coverage reporting

```
mvn -P enable-jacoco clean test jacoco:report
```

# Run spotbugs with gui

```
mvn clean compile spotbugs:spotbugs spotbugs:gui
```
