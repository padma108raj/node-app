pipeline {
  agent any
  stages{
    stage('Build Docker Image'){
      steps{
        sh "docker build . -t padmarajmanne108/myflask:tagname
      }
    }
  }
}

def getDockerTag(){
  def tag = sh script: 'git rev-parse HEAD', retrunStdout: true
  return tag
}
