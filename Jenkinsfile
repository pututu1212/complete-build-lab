
pipeline {
    agent any

    environment {
        PATH = "C:\\Program Files\\Apache Maven\\apache-maven-3.9.16\\bin;C:\\Program Files\\Git\\cmd;C:\\Program Files\\Docker\\Docker\\resources\\bin;${env.PATH}"
    }

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
