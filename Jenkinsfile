pipeline {
    agent any

    environment {
        ARTIFACT_NAME = "calculator.zip"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Verify Environment') {
            steps {
                sh '''
                    node -v
                    npm -v
                '''
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

        stage('Package') {
            steps {
                sh '''
                    mkdir -p artifacts

                    zip -r artifacts/${ARTIFACT_NAME} . \
                    -x "node_modules/*" \
                       ".git/*" \
                       "artifacts/*"
                '''
            }
        }

        stage('Upload Artifact') {
            steps {
                sh '''
                    jf rt upload artifacts/${ARTIFACT_NAME} calculator-local/
                '''
            }
        }
    }

    post {

        success {
            echo "Pipeline Successful ✅"
        }

        failure {
            echo "Pipeline Failed ❌"
        }

        always {
            archiveArtifacts artifacts: 'artifacts/*.zip', fingerprint: true
        }
    }
}