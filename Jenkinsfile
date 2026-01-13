pipeline {
    agent any

    stages {
        stage('Clean') {
            steps {
                echo 'Cleaning...'
                bat 'mvn clean'
            }
        }

        stage('Compile') {
            steps {
                echo 'Compiling...'
                bat 'mvn compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging...'
                bat 'mvn package'
            }
        }

        stage('Verify') {
            steps {
                echo 'Verifying...'
                bat 'mvn verify'
            }
        }

        stage('Install') {
            steps {
                echo 'Installing...'
                bat 'mvn install'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                bat 'mvn deploy'
            }
        }
    }
}
