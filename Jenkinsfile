pipeline {
    agent any

    environment {
        CODE_DIRECTORY = "/path/to/code"
        TEST_ENV = "testing"
        PROD_ENV = "yourname_production"
        NOTIFICATION_EMAIL = "haroldpsunny@gmail.com"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetching the source code from: $CODE_DIRECTORY"
                echo "Compiling the code and generating artifacts"
                // Add actual build steps here
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests"
                echo "Running integration tests"
                // Add actual test steps here
            }
            post {
                success {
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Unit and Integration Tests Passed",
                         body: "Unit and Integration Tests have passed successfully. See attached logs for details.<br>Console Output: ${env.BUILD_URL}console",
                         mimeType: 'text/html'
                }
                failure {
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Unit and Integration Tests Failed",
                         body: "Unit and Integration Tests have failed. See attached logs for details.<br>Console Output: ${env.BUILD_URL}console",
                         mimeType: 'text/html'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Checking the quality of the code'
                // Add actual code quality check steps here
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing security scan'
                // Add actual security scan steps here
            }
            post {
                success {
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Security Scan Passed",
                         body: "Security scan completed without any issues. See attached logs for details.<br>Console Output: ${env.BUILD_URL}console",
                         mimeType: 'text/html'
                }
                failure {
                    mail to: "${env.NOTIFICATION_EMAIL}",
                         subject: "Security Scan Failed",
                         body: "Security scan has some issues. See attached logs for details.<br>Console Output: ${env.BUILD_URL}console",
                         mimeType: 'text/html'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to the $TEST_ENV environment"
                // Add actual staging deployment steps here
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging environment"
                // Add actual integration tests on staging steps here
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the code to the $PROD_ENV environment"
                // Add actual production deployment steps here
            }
        }
    }

    post {
        always {
            emailext (
                subject: "Pipeline Status: ${currentBuild.result}",
                body: '''<html>
                    <body>
                    <p>Build Status: ${currentBuild.result}</p>
                    <p>Build Number: ${currentBuild.number}</p>
                    <p>Console Output: <a href="${env.BUILD_URL}console">${env.BUILD_URL}console</a></p>
                    </body>
                    </html>''',
                to: 'haroldpsunny@gmail.com',
                from: 'jenkins@example.com',
                replyTo: 'jenkins@example.com',
                mimeType: 'text/html'
            )
        }
    }
}