pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Package') {
            steps {
                sh '''
                mkdir -p artifacts
                zip -r artifacts/calculator.zip . \
                  -x "node_modules/*" ".git/*"
                '''
            }
        }

        stage('Upload to JFrog') {
            steps {
                sh '''
                jf rt upload artifacts/calculator.zip calculator-local/
                '''
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

        always {
            archiveArtifacts artifacts: 'artifacts/*.zip', fingerprint: true
        }
    }
}