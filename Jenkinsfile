pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '''-p 3000:3000
--dns=114.114.114.114'''
    }

  }
  stages {
    stage('build') {
      steps {
        sh '''npm --registry https://registry.npm.taobao.org
npm config set registry https://registry.npm.taobao.org
npm config get registry
npm install'''
      }
    }

    stage('test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }

    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }

  }
}