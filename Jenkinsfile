#!/usr/bin/env groovy

pipeline {
    agent any
    tools {
        nodejs 'node-23.9'
    }

    stages {

        stage("First Step") {
            steps {
                script {
                   sh 'echo "Acum ruleaza primul pas din pipeline"'
                }
            }
        }

    }

}