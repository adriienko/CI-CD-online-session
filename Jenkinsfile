pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''checkout scm
def customImage = docker.build("${registry}:${env.BUILD_ID}")'''
      }
    }

  }
  environment {
    registry = 'bogdanandriienko / cicd_worksop'
  }
}