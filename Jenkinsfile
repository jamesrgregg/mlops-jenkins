pipeline {
    agent any

  // using the Timestamper plugin we can add timestamps to the console log
    options {
        timestamps()
    }
    stages {
        stage('Checkout code') {
            steps {
                checkout scm
        }
    }

        stage('Build and Publish Image') {
            when {
                branch 'master'  //only run these steps on the master branch
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
    post {
    failure {
      // notify users when the Pipeline fails
      mail to: 'james.r.gregg@cox.net',
          subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
          body: "Something is wrong with ${env.BUILD_URL}"
    }
}
}