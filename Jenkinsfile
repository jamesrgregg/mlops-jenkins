pipeline {
    agent { dockerfile true 
         additionalBuildArgs '-t mlops-nb'
         }
    stages {
        stage('Build Image') {
            steps {
                sh 'python train-lda.py'
                sh 'python train-nn.py'
            }    
        }
    }
}