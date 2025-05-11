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
	
	stage('Test Results') {
            steps {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}