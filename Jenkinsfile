pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Maven Build & Test') {
            steps {
                sh "./mvnw clean test"
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh "./mvnw sonar:sonar"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t poc7 ."
            }
        }
    }
}