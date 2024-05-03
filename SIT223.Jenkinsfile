pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git 'https://github.com/username/repository.git'
            }
        }
        stage('Build') {
            steps {
                // Build code using Maven
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy code (example: to AWS EC2)
                sh 'ssh user@server "deploy_script.sh"'
            }
        }
    }
    
    post {
        success {
            // Send email notification on success
            emailext(
                to: 'youremail@example.com',
                subject: "Pipeline Success - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The pipeline ${env.JOB_NAME} #${env.BUILD_NUMBER} completed successfully."
            )
        }
        failure {
            // Send email notification on failure
            emailext(
                to: 'youremail@example.com',
                subject: "Pipeline Failure - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The pipeline ${env.JOB_NAME} #${env.BUILD_NUMBER} failed. Please check the logs for details.",
                attachLog: true
            )
        }
    }
}
