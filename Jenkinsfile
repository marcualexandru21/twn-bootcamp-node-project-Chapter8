#!/user/bin/env groovy

def gv

pipeline {
    agent any
    tools {
        node 'node-23.9'
    }

    stages {

        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }

        stage("First Step") {
            steps {
                script {
                    echo 'Acum ruleaza primul pas din pipeline'
                }
            }
        }


        stage("build jar") {
            steps {
                script{

                }
            }
        }

        stage("build the docker image") {
            steps {
                script{

                }
            }
        }

        stage("deploy app") {
            steps {
                script{

                }
            }
        }

        stage('commit version update') {
            steps {
                script {

                }
            }
        }

    }

}