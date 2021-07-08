pipeline {
  agent any
  environment{
    DOCKER_TAG = getDockerTag()
  }
  stages{
    stage('Build Docker Image'){
      steps{
        sh "sudo ocker build . -t padmarajmanne108/nodeapp:${DOCKER_TAG}"
      }
    }
  }
}

def getDockerTag(){
  def tag = sh script: 'git rev-parse HEAD', returnStdout: true
  return tag
}
