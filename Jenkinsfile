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
                echo 'Creamos'
                sh "kubectl apply -f https://raw.githubusercontent.com/ceciliacalero/kubedeploy/master/ngnix-deployment.yml" 
                 echo 'esperamos 30 sg y borramos'
                  sleep 30
                sh "kubectl delete service my-service"
                sh " kubectl delete deployment nginx-deployment"
              
            }
        }
    }
    }
}

