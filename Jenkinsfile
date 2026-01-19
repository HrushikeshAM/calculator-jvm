pipeline {
    agent any

    tools {
        maven 'Maven'      // must match Jenkins tool name
        jdk 'JDK'          // must match Jenkins tool name
    }

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

    post {

        success {
            emailext(
                subject: "SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                Build SUCCESSFUL ✅

                Job: ${env.JOB_NAME}
                Build Number: ${env.BUILD_NUMBER}
                Build URL: ${env.BUILD_URL}
                """,
                recipientProviders: [developers()]
            )
        }

        failure {
            emailext(
                subject: "FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                Build FAILED ❌

                Job: ${env.JOB_NAME}
                Build Number: ${env.BUILD_NUMBER}
                Build URL: ${env.BUILD_URL}

                Please check the console output.
                """,
                recipientProviders: [developers()]
            )
        }

        always {
            echo 'Pipeline finished.'
        }
    }
}
