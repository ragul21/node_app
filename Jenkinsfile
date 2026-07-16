pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'echo "Building..."'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Tests Passed"'
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