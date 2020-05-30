#!groovy

// Don't test plugin compatibility to other Jenkins versions
// Allow failing tests to retry execution
// buildPlugin(failFast: false)

// Test plugin compatbility to pom defined version (null) and latest Jenkins weekly
// Use recommended configuration (including Java 8 and Java 11)

Random random = new Random() // Randomize which Jenkins version is selected for more testing
def use_newer_jenkins = random.nextBoolean() // Use newer Jenkins on one build but slightly older on other

// Test plugin compatibility to recommended configurations
subsetConfiguration = [ [ jdk: '8',  platform: 'windows', jenkins: null                      ],
                        // Compile with Java 8, test 2.204.6 or 2.222.1 depending on random use_newer_jenkins
                        [ jdk: '8',  platform: 'linux',   jenkins: !use_newer_jenkins ? '2.204.6' : '2.222.1', javaLevel: '8' ],
                        // Compile with Java 11, test the Jenkins version that Java 8 did *not* test
                        [ jdk: '11', platform: 'linux',   jenkins:  use_newer_jenkins ? '2.204.6' : '2.222.1', javaLevel: '8' ]
                      ]

buildPlugin(configurations: subsetConfiguration, failFast: false)

// See https://github.com/jenkins-infra/pipeline-library/blob/master/README.adoc
// for detailed description of the arguments available with buildPlugin
