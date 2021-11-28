pipeline {
    agent any

  // using the Timestamper plugin we can add timestamps to the console log
    options {
        timestamps()
    }
    environment {
    //Use Pipeline Utility Steps plugin to read information from pom.xml into env variables
        IMAGE = mlops-devops
        VERSION = 1.0.0
  }
    stages {
        stage('Checkout code') {
            steps {
                checkout scm
        }
    }

        stage('Build and Publish Image') {
            when {
                branch 'main'  //only run these steps on the master branch
            }
            steps {
                sh """
                docker build -t ${IMAGE} .
                docker tag ${IMAGE} ${IMAGE}:${VERSION}
                docker push ${IMAGE}:${VERSION}
                """
            }
        }
  }   
}