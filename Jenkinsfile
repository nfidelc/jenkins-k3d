pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: busybox
            image: busybox
            args:
              - sleep
              - "3600"
        '''
    }
  }
  stages {
    stage('Run busybox') {
      steps {
        container('busybox') {
          sh 'date'
          sh 'uname -a;sleep 120'
          sh 'date'
        }
      }
    }
  }
}