pipeline {
agent any
environment {
registryCredential = 'usama-credentials'
}
stages {
stage('Build') {
steps {
sh 'docker build -t usamaahmadkhan/test-node-app .'
}
}
stage('Test') {
steps {
sh 'docker container rm -f node || true'
sh 'docker container run -p 8001:8080 --name node -d usamaahmadkhan/test-node-app'
sh 'curl -I http://localhost:8001'
}
}
stage('Publish') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
sh 'docker push usamaahmadkhan/test-node-app:latest'
}
}
}
}
}
}
