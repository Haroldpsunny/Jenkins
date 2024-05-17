pipeline {
    agent any

    environment {
        CODE_DIRECTORY = "/path/to/code"  // Directory where the source code is located
        TEST_ENV = "testing"  // Environment for testing
        PROD_ENV = "yourname_production"  // Production environment
        NOTIFICATION_EMAIL = "haroldpsunny@gmail.com"  // Email for notifications
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from: $CODE_DIRECTORY"
                echo "Compiling the code and generating artifacts"
                // Here you would add steps to fetch, compile, and package your code.
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
                // Add steps to execute unit and integration tests.
            }
            post {
                success {
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Unit and Integration Tests Passed",
                         body: """Unit and Integration Tests have passed successfully. 
                                 See attached logs for details.<br>
                                 Console Output: ${env.BUILD_URL}console""",
                         mimeType: 'text/html'
                }
                failure {
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Unit and Integration Tests Failed",
                         body: """Unit and Integration Tests have failed. 
                                 See attached logs for details.<br>
                                 Console Output: ${env.BUILD_URL}console""",
                         mimeType: 'text/html'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Checking the quality of the code'
                // Steps to perform code quality checks, e.g., using SonarQube.
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan'
                // Steps to perform security scans, e.g., using a tool like OWASP Dependency Check.
            }
            post {
                success {
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Security Scan Passed",
                         body: """Security scan completed without any issues. 
                                 See attached logs for details.<br>
                                 Console Output: ${env.BUILD_URL}console""",
                         mimeType: 'text/html'
                }
                failure {
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Security Scan Failed",
                         body: """Security scan has some issues. 
                                 See attached logs for details.<br>
                                 Console Output: ${env.BUILD_URL}console""",
                         mimeType: 'text/html'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to the $TEST_ENV environment"
                // Add steps for deploying the application to the staging environment.
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging environment"
                // Steps to run integration tests on the staging environment to ensure the deployment is successful.
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the $PROD_ENV environment"
                // Add steps for deploying the application to the production environment.
            }
        }
    }

    post {
        always {
            emailext (
                subject: "Pipeline Status: ${currentBuild.result}",
               
                to: 'haroldpsunny@gmail.com',
                from: 'jenkins@example.com',
                replyTo: 'jenkins@example.com',
                mimeType: 'text/html'
            )
        }
    }
}
