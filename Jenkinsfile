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
                bat './mvnw clean install'
            }
        }

        stage('Run') {
            steps {
                bat 'start /B ./mvnw spring-boot:run'
            }
        }

        stage('Test') {
            steps {
                bat './mvnw test'
                stash includes: 'target/surefire-reports/*.xml', name: 'test-results'
            }
        }

        stage('Test Results') {
            steps {
                unstash 'test-results'
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}
