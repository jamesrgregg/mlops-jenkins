pipeline { 
    environment { 
        registry = "hub.docker.com/jrgreggdevops" 
        registryCredential = 'jrgreggdevops' 
        dockerImage = 'mlops-notebook' 
    }
    agent any 
    stages { 
        stage('Cloning our Git') { 
            steps { 
                git 'https://github.com/jamesrgregg/mlops-jenkins'
            }
        } 
        stage('Building our image') { 
            steps { 
                script { 
                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 
                }
            } 
        }
        stage('Deploy our image') { 
            steps { 
                script { 
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push() 
                    }
                } 
            }
        } 
        stage('Cleaning up') { 
            steps { 
                sh "docker rmi $registry:$BUILD_NUMBER"
            }
        } 
    }
}