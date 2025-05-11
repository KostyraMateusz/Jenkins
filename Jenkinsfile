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
		sh 'chmod +x ./mvnw'
                sh './mvnw clean install'
            }
        }

        stage('Run') {
            steps {
                sh 'nohup ./mvnw spring-boot:run &'
            }
        }

        stage('Test') {
            steps {
                sh './mvnw test'
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
