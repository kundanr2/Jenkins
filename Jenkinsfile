pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven as the build automation tool.'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests using JUnit and Mockito.'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube to ensure it meets industry standards.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing a security scan using OWASP Dependency Check.'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to a staging server (AWS EC2 instance).'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on the staging environment to ensure functionality.'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to a production server (AWS EC2 instance).'
            }
        }
    }

    post {
        always {
            emailext(
                mimeType: 'text/html',
                to: 'kundanmarri1@gmail.com',
                subject: "Jenkins Pipeline Status: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                    <html>
                        <body>
                            <h1>Pipeline Completion Report</h1>
                            <p><strong>Build:</strong> ${env.JOB_NAME} #${env.BUILD_NUMBER}</p>
                            <p><strong>Status:</strong> ${currentBuild.currentResult}</p>
                            <p><strong>Build URL:</strong> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                        </body>
                    </html>
                """,
                attachLog: true
            )
        }
        failure {
            emailext(
                mimeType: 'text/html',
                to: 'kundanmarri1@gmail.com',
                subject: "FAILURE in Pipeline: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: """
                    <html>
                        <body>
                            <h1>Pipeline Failure Report</h1>
                            <p><strong>Build:</strong> ${env.JOB_NAME} #${env.BUILD_NUMBER}</p>
                            <p><strong>Status:</strong> ${currentBuild.currentResult}</p>
                            <p><strong>Build URL:</strong> <a href="${env.BUILD_URL}">${env.BUILD_URL}</a></p>
                        </body>
                    </html>
                """,
                attachLog: true
            )
        }
    }
}
