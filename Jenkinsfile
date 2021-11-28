pipeline {
    agent {
    dockerfile {
        filename 'Dockerfile'
        registryUrl 'jrgreggdevops/mlops-devops'
        registryCredentialsId 'dockerhub_id'
        reuseNode true
    }
    stages {
        stage('Build Image') {
            steps {
                sh 'python --version'
                sh 'python train-lda.py'
                sh 'python train-nn.py'
            }    
        }
    }
}