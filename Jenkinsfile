pipeline {
    agent { dockerfile true }
    stages {
        stage('Build Image') {
            steps {
                sh 'python train-lda.py'
                sh 'python train-nn.py'
            }    
        }
    }
}