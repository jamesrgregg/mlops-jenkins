pipeline {
    agent { dockerfile true }
    stages {
        stage('Build Image') {
            steps {
                sh 'python --version'
                sh 'git --version'
                sh 'docker images'
            }    
        }
    }
}