pipeline {
  agent any
  environment{
    DOCKER_TAG = getDockerTag()
  }
  stages{
    stage('Build Docker Image'){
      steps{
        sh " docker build . -t padmarajmanne108/nodeapp:${DOCKER_TAG}"
      }
    }
    stage('Docker Push'){
      withCredentials([string(credentialsId: 'docker-pwd', variable: 'docker-pwd')]) {
           sh "docker login -U padmarajmanne108 -p ${docker-pwd}"
           sh "docker push padmarajmanne108/nodeapp:${DOCKER_TAG}"
      }
    }
  }
}

def getDockerTag(){
  def tag = sh script: 'git rev-parse HEAD', returnStdout: true
  return tag
}
