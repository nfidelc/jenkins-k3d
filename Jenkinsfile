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
              - "300"
          - name: busybox1-34
            image: busybox:1.34
            args:
              - sleep
              - "300"
        '''
    }
  }
  stages {
    stage('Run busybox') {
      steps {
        container('busybox') {
          sh 'date'
          sh 'echo "Hello Simatupang. Today is Tuesday...semangat berkarya" > hello.txt'
          sh 'pwd'
          sh 'ls -ltra'
        }
        container('busybox1-34') {
          sh 'date'
          sh 'pwd'
          sh 'cat hello.txt'
          sh 'ls -ltra'
          sh 'uname -a;sleep 120'
          sh 'date'
        }
      }
    }
  }
}
