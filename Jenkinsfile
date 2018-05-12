#!groovy

// @Library('git-modern-3.8.0@5093f89ac0057a471081ff5a5bf94c20f9acae97') _ // Has a branch
@Library('git-modern-3.8.0@ba12808d4fd5b3e3889686a75d66d72eb4a45047') _ // On master, not tip of branch
// @Library('git-modern-3.8.0@a93c04cdc93f655b04cb54fae90780bc208b2566') _ // On master, not tip of branch

// @Library('github-modern-3.8.0@a93c04cdc93f655b04cb54fae90780bc208b2566') _ // On master, not tip of branch
// @Library('github-modern-3.8.0') _ // On master, tip of branch

// @Library('bitbucket-modern-3.8.0@a93c04cdc93f655b04cb54fae90780bc208b2566') _ // On master, not tip of branch // works
// @Library('bitbucket-modern-3.8.0@5093f89ac0057a471081ff5a5bf94c20f9acae97') _ // Has a branch
// @Library('bitbucket-modern-3.8.0') _ // On master, tip of branch

import com.markwaite.Assert
import com.markwaite.Build

import static groovy.json.JsonOutput.*

def branch = 'JENKINS-48061-no-tag-no-branch'
def repo = 'https://github.com/MarkEWaite/hello-world-plugin'

import java.util.Random
def random = new Random()

def implementations = [ 'git', 'jgit', 'jgitapache' ]
/* Randomize order of implementations */
Collections.shuffle(implementations, random)

def tasks = [ : ]

def checkout_result = [ : ]

def first = ""

for (int i = 0; i < implementations.size(); ++i) {
  def gitImplementation = implementations[i]
  tasks[gitImplementation] = {
    node {
      stage("Check ${gitImplementation}") {
        def implementation = gitImplementation == "git" ? "Default" : gitImplementation
        checkout([$class: 'GitSCM',
                  branches: [[name: branch]],
                  browser: [$class: 'GithubWeb', repoUrl: repo],
                  extensions: [
                    [$class: 'CloneOption', honorRefspec: true, noTags: true],
                  ],
                  gitTool: implementation,
                  userRemoteConfigs: [[refspec: "+refs/heads/${branch}:refs/remotes/origin/${branch}", url: repo]]
                 ]
                )

        /* Call the ant build. */
        def my_step = new com.markwaite.Build()
        my_step.ant 'info'
        def my_check = new com.markwaite.Assert()
        my_check.logContains('.*user dir is .*', 'Ant output missing user dir report')
      }
    }
  }
}

parallel(tasks)
