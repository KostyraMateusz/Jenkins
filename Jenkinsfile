pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/KostyraMateusz/Jenkins'
            }
        }

        stage('Build') {
            steps {
                sh './mvnw clean install'
            }
        }

        stage('Test') {
            steps {
                sh './mvnw test'
            }
        }
    }
}