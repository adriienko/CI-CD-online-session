pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh '''checkout scm
def customImage = docker.build("${registry}:${env.BUILD_ID}")'''
      }
    }

    stage('publish') {
      steps {
        sh '''docker.withRegistry(\'\', \'6ba44455-a886-4ccf-a7d3-2a55d5daa888\') 
{
docker.image("${registry}:${env.BUILD_ID}").push(\'latest\')
}'''
      }
    }

  }
  environment {
    registry = 'bogdanandriienko/cicd_worksop'
  }
}