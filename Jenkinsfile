pipeline{
  agent any
  environment{
   DOCKER_TAG = getDockerTag()
 }
  stages{
    stage("Build Docker Image"){
      steps{
        sh "docker build . -t padmarajmanne108/nodeapp:${DOCKER_TAG}"
      }
    }
    stage("Push Docker Image"){
        steps{
           withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerpwd')]) {
               sh "docker login -u padmarajmanne108 -p ${dockerpwd}"
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
