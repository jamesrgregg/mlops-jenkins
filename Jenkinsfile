pipeline {
    agent { dockerfile true }

    environment {
        ORG_NAME = "jrgreggdevops"
        APP_NAME = "mlops-devops"
        APP_VERSION = "1.0-SNAPSHOT"
        APP_CONTEXT_ROOT = "/"
        TEST_CONTAINER_NAME = "ci-${APP_NAME}-${BUILD_NUMBER}"
        PREV_CONTAINER_NAME="ci-${APP_NAME}-${currentBuild.previousBuild.number}"
    }
    stages {
    stage('Build Docker image') {
        steps {
            echo "-=- build Docker image -=-"
            sh "docker build -t ${ORG_NAME}/${APP_NAME}:${APP_VERSION} -t ${ORG_NAME}/${APP_NAME}:latest ."
        }
    }
    stage('Push Docker image') {
        steps {
            echo "-=- push Docker image -=-"
            sh "docker images"
            echo '-=- pushing images in next stage -=-'
        }
    }
}
}