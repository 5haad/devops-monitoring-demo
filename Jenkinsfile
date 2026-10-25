pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t myapp:${BUILD_NUMBER} .'
      }
    }
    stage('Load into Minikube') {
      steps {
        sh 'minikube image load myapp:${BUILD_NUMBER}'
      }
    }
    stage('Deploy') {
      steps {
        sh 'kubectl set image deployment/myapp myapp=myapp:${BUILD_NUMBER}'
        sh 'kubectl rollout status deployment/myapp'
      }
    }
  }
}
