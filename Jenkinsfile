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
      steps{
           withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerhubpwd')]) {
               sh "docker login -U padmarajmanne108 -p ${dockerhubpwd}"
               sh "docker push padmarajmanne108/nodeapp:${DOCKER_TAG}"
      }
     }
    }
  }
}

def getDockerTag(){
  def tag = sh script: 'git rev-parse HEAD', returnStdout: true
  return tag
}
