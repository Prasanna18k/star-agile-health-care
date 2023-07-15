pipeline {
  agent any
  tools {
    maven '3.6.3'
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('image') {
      steps {
       checkout scm
         echo 'Starting to build docker image'

                script {
                    def customImage = docker.build("my-image:${env.BUILD_ID}")
                    customImage.push()
                }
      }
    }
  }
}
