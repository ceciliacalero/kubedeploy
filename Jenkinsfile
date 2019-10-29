pipeline {
    agent {
      kubernetes {
        defaultContainer 'pod'
        yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    label: pod
spec:
  containers:
  - name: kubectl
    image: 'lachlanevenson/k8s-kubectl:v1.8.8'
    command:
    - cat
    tty: true
"""
        }
    }
    stages{
     stage('Build') {
      steps{
       container('kubectl'){
                echo 'dddd'
                sh "kubectl apply -f https://raw.githubusercontent.com/ceciliacalero/kubedeploy/master/ngnix-deployment.yml" 
              
            }
        }
    }
    }
}

