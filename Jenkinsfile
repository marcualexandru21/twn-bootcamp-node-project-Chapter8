#!/usr/bin/env groovy

def gv  // Global variable to hold the loaded script

pipeline {
    agent any  // Run on any available agent
    tools {
        nodejs 'node-23.9'  // Use Node.js version 23.9 (ensure this is configured in Jenkins)
    }

  /*  stages {
        stage("init") {
            steps {
                script {
                    // Load the Groovy script from the workspace
                    gv = load "script.groovy"
                }
            }
      */  }

        stage("First Step") {
            steps {
                script {
                    echo 'Acum ruleaza primul pas din pipeline'  // Echo a message
                }
            }
        }

}