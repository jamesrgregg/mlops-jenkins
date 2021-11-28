pipeline {
    agent any

  // using the Timestamper plugin we can add timestamps to the console log
    options {
        timestamps()
    }
    environment {
    //Use Pipeline Utility Steps plugin to read information from pom.xml into env variables
        registry = "jrgreggdevops/mlops-devops"
        registryCredential = 'DockerHub_ID'
        dockerImage = ''
    
        
  }
    stages {
        stage('Checkout code') {
            steps {
                checkout scm
        }
    }

        stage('Build and Tag Image') {
            when {
                branch 'main'  //only run these steps on the master branch
            }
            steps {
                script { 
                    dockerImage = docker.build registry + ":latest"
                }
            }
        }
        stage('Push Image') {
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
                sh "docker images --format 'table {{.Repository}}\t{{.Tag}}\t{{.ID}}\t{{.CreatedAt}}\t{{.Size}}'"  
                //sh "docker image prune -a --force"  
                sh "docker rmi $registry:latest"
            }
        }    
    }
}    



