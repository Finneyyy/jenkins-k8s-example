pipeline {
  agent any
  stages {
/*
    stage('Install CLIs') {
      steps {
        sh "sudo chmod +x *.sh"
        sh "./install-cli.sh"
        sh "./install-eksctl.sh"
        sh "./install-kubectl.sh"
      }
    }
*/
    stage('Configure kubectl') {
      steps {
        sh "aws eks --region eu-west-2 update-kubeconfig --name exerciseCluster"
      }
    }
    stage('Deploy manifests') {
      steps {
        sh "kubectl apply -f back.yml"
        sh "kubectl apply -f front.yml"
        sh "kubectl get services"
      }
    }
  }
}
