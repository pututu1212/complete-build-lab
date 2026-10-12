pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'mvn -version'
                bat 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t complete-build:1.0 .'
            }
        }

        stage('Docker Run') {
            steps {
                bat 'docker run --rm complete-build:1.0'
            }
        }
    }

    post {
        success {
            echo 'Complete Build Pipeline: SUCCESS'
        }
        failure {
            echo 'Complete Build Pipeline: FAILED - Check stage logs'
        }
    }
}
