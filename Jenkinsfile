pipeline {
  agent any

  environment {
    KUBECONFIG = credentials('kubeconfig') // Assumes you have a Kubernetes configuration file stored as a Jenkins credential
    CHART_NAME = 'my-chart'
    RELEASE_NAME = 'guestbook-2.0'
    NAMESPACE = 'my-guestbook'
  }

  //stages {
    //stage('Checkout') {
      //steps {
        //checkout scm
      //}
    //}
   stages{
        stage('Git checkout'){
            steps{
                git credentialsId: 'github_token_access', url: 'https://github.com/ngengecharity/guestbook.git'
            }
        }  


       stage('Helm Install') {
           steps {
           sh "helm upgrade --namespace $NAMESPACE $RELEASE_NAME v1/guestbook"
        //sh "helm install --namespace helm-guestbook myguestbook helm101/guestbook/"
           }
       }
    }   
}

    // stage('Helm Test') {
    //   steps {
//         sh "helm test $RELEASE_NAME --namespace $NAMESPACE"
//       }
//     }

//     stage('Helm Cleanup') {
//       steps {
//         sh "helm delete $RELEASE_NAME --namespace $NAMESPACE"
//       }
//     }
//   }