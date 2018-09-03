#!/usr/bin/env groovy

node ('master') {

    environment {
        DEV = 'Development'
        PROD = 'Production'
    }
    stages {
        stage('Preparation') {
            steps {
                script {
                    echo "Environment " + ENV
                }
                echo ENV1
                echo ENV2
            }
        }
        stage('Build') {
            steps {
                sh "echo ${ENV1} and ${ENV2}"
            }
        }
        // more stages...
    }
}

