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
         sh 'docker login -u prasannagundavarapu -p maruthi@12345'
         

                script {
                    def customImage = docker.build("my-image:${env.BUILD_ID}")
                    customImage.push()
                }
      }
    }
  }
}
