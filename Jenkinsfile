pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checked out by Jenkins'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        success {
            echo 'Pipeline Passed ✅'
        }

        failure {
            echo 'Pipeline Failed ❌'
        }
    }
}