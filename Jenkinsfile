#!/usr/bin/env groovy

library identifier: 'jsl-ex-ch8@master', retriever:modernSCM(
[$class: 'GitSCMSource' ,
remote: 'https://github.com/marcualexandru21/jsl-ex-ch8.git' ,
credentialsId: 'github-credentials-ex-ch8-with-token'
])

env.IMAGE_NAME = "mbradu/ex-ch8-twn:nodejs-app-"
env.CREDENTIALS_ID_DOCKER_HUB = "dockerhub-credentials-token"
env.CREDENTIALS_ID_GITHUB = "github-credentials-ex-ch8-with-token"
env.NAME = "bradu"
env.EMAIL = "marcualexandru21@gmail.com"
env.REMOTE_URL = "github.com/marcualexandru21/twn-bootcamp-node-project-Chapter8.git"
env.PUSH_BRANCH_NAME = "master"

pipeline {
    agent any
    tools {
        nodejs 'node-23.9'
    }

    stages {

        stage("npm install") {
            steps {
                script {
                    sh 'cd app'
                    sh 'npm install'
                }
            }
        }

        stage("increment version and get version") {
            steps {
                script {
                   sh 'npm version patch'
                   def version = sh(script: 'npm pkg get version', returnStdout: true).trim()
                   def bar = "-"
                   IMAGE_NAME = "${IMAGE_NAME}${version}${bar}${BUILD_NUMBER}"
                }
            }
        }

        stage("Build docker image") {
            steps {
                script {
                   buildDockerImage "${IMAGE_NAME}"
                }
            }
        }

        stage("Docker hub login") {
            steps {
                script {
                   dockerHubLogin "${CREDENTIALS_ID_DOCKER_HUB}"
                }
            }
        }

        stage("Push to docker hub") {
            steps {
                script {
                   dockerPushImage "${IMAGE_NAME}"
                }
            }
        }

        stage("config name and email") {
            steps {
                script {
                   configNameAndEmail "${NAME}" "${EMAIL}"
                }
            }
        }

        stage("Set Remote URL") {
            steps {
                script {
                   setRemoteURL "${REMOTE_URL}" "${CREDENTIALS_ID_GITHUB}"
                }
            }
        }

        stage("Push to Remote URL") {
            steps {
                script {
                   addCommitAndPushChanges "${PUSH_BRANCH_NAME}"
                }
            }
        }

    }

}
