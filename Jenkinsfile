pipeline {
    agent any

    stages {

        stage('Install') {
            steps {
                sh '''
                    pwd
                    node -v
                    npm -v
                    npm install --verbose
                    echo "INSTALL FINISHED"
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    npm test
                    echo "TEST FINISHED"
                '''
            }
        }
    }
}