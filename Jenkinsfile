pipeline {
    agent { dockerfile true }
    stages {
        stage('Build') {
            steps {
                sh 'python --version'
                sh 'git --version'
            }
        }
    }
}