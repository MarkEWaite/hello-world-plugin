#!groovy

// Don't test plugin compatibility to other Jenkins versions
// Allow failing tests to retry execution
// buildPlugin(failFast: false)

// Test plugin compatbility to pom defined version (null) and latest Jenkins weekly
// Allow failing tests to retry execution
// Run checkstyle and save the output, mark unstable on any checkstyle warning
// Run spotbugs and save the output, mark unstable on any spotbugs warning
// build recommended configurations
Random random = new Random() // Randomize which Jenkins version is selected for more testing
use_newer_jenkins = random.nextBoolean() // Use newer Jenkins on one build but slightly older on other
subsetConfiguration = [ [ jdk: '8',  platform: 'windows', jenkins: null                      ],
                        [ jdk: '8',  platform: 'linux',   jenkins: use_newer_jenkins ? null : '2.190', javaLevel: '8' ],
                        [ jdk: '11', platform: 'linux',   jenkins: use_newer_jenkins ? '2.190' : null, javaLevel: '8' ]
                      ]

buildPlugin(configurations: subsetConfiguration, failFast: false)

// See https://github.com/jenkins-infra/pipeline-library/blob/master/README.adoc
// for detailed description of the arguments available with buildPlugin
