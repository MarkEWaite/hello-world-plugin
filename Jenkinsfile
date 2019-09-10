#!groovy

// Test plugin compatbility to pom defined version (null)
// Allow failing tests to retry execution
// Run checkstyle and save the output, mark unstable on any checkstyle warning
// Run spotbugs and save the output, mark unstable on any spotbugs warning
// build recommended configurations
subsetConfiguration = [ [ jdk: '8',  platform: 'windows', jenkins: null ],
                        [ jdk: '11', platform: 'linux',   jenkins: null ],
                      ]

buildPlugin(configurations: subsetConfiguration,
            failFast: false,
            checkstyle:[run:true, unstableTotalAll: '0', archive:true],
            findbugs:  [run:true, unstableTotalAll: '0'              ])

// See https://github.com/jenkins-infra/pipeline-library/blob/master/README.adoc
// for detailed description of the arguments available with buildPlugin
