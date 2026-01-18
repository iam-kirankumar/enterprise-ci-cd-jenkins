pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/iam-kirankumar/enterprise-ci-cd-jenkins'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application...'
            }
        }

        stage('Unit Tests') {
            steps {
                echo 'Running unit tests...'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t sample-app:latest ./docker'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }

        stage('Health Check') {
            steps {
                sh 'sh scripts/health-check.sh'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed. Triggering rollback or alert.'
        }
        success {
            echo 'Pipeline completed successfully.'
        }
    }
}
