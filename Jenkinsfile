#!groovy

// Don't test plugin compatibility to other Jenkins versions
// Allow failing tests to retry execution
// buildPlugin(failFast: false)

// Test plugin compatbility to pom defined version (null)
// Allow failing tests to retry execution
// Run checkstyle and save the output, mark unstable on any checkstyle warning
// Run spotbugs and save the output, mark unstable on any spotbugs warning
// build recommended configurations
subsetConfiguration = [ [ jdk: '8',  platform: 'windows', jenkins: null ],
                        [ jdk: '11', platform: 'linux',   jenkins: null ],
                      ]

buildPlugin(configurations: subsetConfiguration, failFast: false, checkstyle: true, findbugs: true)

// See https://github.com/jenkins-infra/pipeline-library/blob/master/README.adoc
// for detailed description of the arguments available with buildPlugin
