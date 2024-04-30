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
        success {
            emailext(
                to: 'kundanmarri1@gmail.com',
                subject: "SUCCESS: Stage Completed - ${currentBuild.fullDisplayName}",
                body: "The stage completed successfully.",
                attachLog: true
            )
        }
        failure {
            emailext(
                to: 'kundanmarri1@gmail.com',
                subject: "FAILURE: Stage Failed - ${currentBuild.fullDisplayName}",
                body: "The stage failed. Check the attached logs for more details.",
                attachLog: true
            )
        }
    }
}
