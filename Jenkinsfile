
pipeline {
    agent any 
    
    environment {
        ORG_NAME = "jrgreggdevops"
        APP_NAME = "mlops-devops"
        APP_VERSION = "1.0-SNAPSHOT"
        APP_CONTEXT_ROOT = "/"
        TEST_CONTAINER_NAME = "ci-${APP_NAME}-${BUILD_NUMBER}"
        PREV_CONTAINER_NAME="ci-${APP_NAME}-${currentBuild.previousBuild.number}"
    }

  stages {
    stage('Pull the Code') {
        steps {
            echo "-=- Start the Build -=-"
        }
    }
  
    stage('Build Docker image') {
        steps {
            echo "-=- build Docker image -=-"
            sh "docker build -t ${ORG_NAME}/${APP_NAME}:${APP_VERSION} -t ${ORG_NAME}/${APP_NAME}:latest ."
        }
    }

   stage('Run Docker image') {
            steps {
                echo "-=- run Docker image -=-"
            }
        }

  }
}