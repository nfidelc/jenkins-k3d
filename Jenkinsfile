pipeline {
  agent {
    kubernetes {
      yamlFile "jenkins-pod.yaml"
    }
  }

  stages {
    stage("Build") {
      steps {
        git url:'https://github.com/nfidelc/jenkins-k3d.git', branch:'main'
        }
    }
    stage('Apply Kubernetes Deploy') {
      withKubeConfig([credentialsId: 'config', serverUrl: 'https://192.168.56.109:6443']) {
        sh 'kubectl apply -f my-kubernetes-directory'
      }
	}
  }
  }
}