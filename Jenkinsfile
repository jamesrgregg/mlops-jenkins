pipeline {
    agent { dockerfile true }
    stages {
        stage('Build') {
            steps {
                sh 'python --version'
                sh 'git --version'
            }
        stage('Train Model') {
            steps {
                sh 'python train.lda.py'
                sh 'python train.nn.py'
            }    
        }
    }
}