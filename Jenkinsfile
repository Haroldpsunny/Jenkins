pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Build the code using a build automation tool like Maven.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Run unit tests and integration tests using tools like JUnit and Selenium.'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Integrate a code analysis tool like SonarQube to analyze code quality.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Perform security scan using a tool like OWASP ZAP.'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploy the application to a staging server (e.g., AWS EC2 instance) using Jenkins Deploy Plugin.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Run integration tests on the staging environment to ensure the application functions correctly.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploy the application to a production server (e.g., AWS EC2 instance) using Ansible or Jenkins Deploy Plugin.'
            }
        }
    }

    post {
        success {
            emailext body: "The pipeline ${currentBuild.fullDisplayName} has succeeded.",
                     subject: "Pipeline Success: ${currentBuild.fullDisplayName}",
                     to: 'haroldpsunny@gmail.com',
                     mimeType: 'text/plain',
                     attachLog: true,
                     attachmentsPattern: 'logs/*.log' // Attach all log files in the 'logs' directory
        }
    
        failure {
            emailext body: "The pipeline ${currentBuild.fullDisplayName} has failed. Please check logs.",
                     subject: "Pipeline Failure: ${currentBuild.fullDisplayName}",
                     to: 'haroldpsunny@gmail.com',
                     mimeType: 'text/plain',
                     attachLog: true,
                     attachmentsPattern: 'logs/*.log' // Attach all log files in the 'logs' directory
        }
    }
}
