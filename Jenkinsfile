pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/jongsamsunduck/jen.git', branch: 'main'
      }
    }
    stage('docker build') {
      steps {
        sh '''
        sudo docker build -t 192.168.0.195:5000/eun:latest .
        sudo docker push 192.168.0.195:5000/eun:latest
        '''
      }
    }
    
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kubectl delete -f test.yml
        sleep 10
        sudo kubectl apply -f test.yml
        '''
      }
    }
    
  }
}
