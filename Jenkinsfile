pipeline {
  agent any
  stages {
    stage('git scm update') {
      steps {
        git url: 'https://github.com/jitoo/jen.git', branch: 'main'
      }
    }
    stage('docker build') {
      steps {
        sh '''
        sudo docker build -t rapa.iptime.org:5000/mynginx:jisoo .
        sudo docker push rapa.iptime.org:5000/mynginx:jisoo
        '''
      }
    }
    
    stage('deploy k8s') {
      steps {
        sh '''
        sudo kubectl apply -f test.yml
        '''
      }
    }
    
  }
}
