pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        script {
          checkout scm
          def customImage = docker.build("${registry}:${env.BUILD_ID}")
        }

      }
    }

    stage('publish') {
      steps {
        sh '''docker.withRegistry(\'\', \'dockerhub-id\') 
{
docker.image("${registry}:${env.BUILD_ID}").push(\'latest\')
}'''
        script {
          docker.withRegistry('', 'dockerhub-id')
          {
            docker.image("${registry}:${env.BUILD_ID}").push('latest')
          }
        }

      }
    }

  }
  environment {
    registry = 'bogdanandriienko/cicd_worksop'
  }
}