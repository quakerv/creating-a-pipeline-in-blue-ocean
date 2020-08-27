pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('build') {
      steps {
        sh '''npm config get registry
npm config set registry https://registry.npm.taobao.org
npm install'''
      }
    }

  }
}