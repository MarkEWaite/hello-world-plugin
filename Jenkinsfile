#!groovy

// Test plugin compatbility to pom defined version (null)
// Allow failing tests to retry execution
// Choose a different java on each platform
// Random so that both platforms will run both Java versiosn sometimes
// Intentionally not running exhaustive tests
Random random = new Random() // Randomize Java version in platform selection
choose_java = random.nextBoolean()
java_a = choose_java ? '8' : '11'
java_b = choose_java ? '11' : '8'
subsetConfiguration = [ [ jdk: java_a, platform: 'windows', jenkins: null ],
                        [ jdk: java_b, platform: 'linux',   jenkins: null ],
                      ]

buildPlugin(configurations: subsetConfiguration, failFast: false)

// See https://github.com/jenkins-infra/pipeline-library/blob/master/README.adoc
// for detailed description of the arguments available with buildPlugin
