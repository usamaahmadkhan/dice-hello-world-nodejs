pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t umermunirrr/test-node-app .'
      }
    }
    stage('Test') {
      steps {
        sh 'docker container rm -f node'
        sh 'docker container run -p 8001:8080 --name node -d umermunirrr/test-node-app'
        sh 'curl -I http://localhost:8001'
      }
    }
    stage('Publish') {
      steps {
          sh 'echo Umer'
        }
      }
    }
}
