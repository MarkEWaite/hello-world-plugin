#!groovy

// Don't test plugin compatibility to other Jenkins versions
// Allow failing tests to retry execution
// buildPlugin(failFast: false)

// Test plugin compatbility to pom defined version (null) and latest Jenkins weekly
// Use recommended configuration (including Java 8 and Java 11)
buildPlugin(configurations: buildPlugin.recommendedConfigurations(), failFast: false)

// See https://github.com/jenkins-infra/pipeline-library/blob/master/README.adoc
// for detailed description of the arguments available with buildPlugin
