pipeline {
    agent any

    stages {
        stage('Deploy to kubernates') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8D5DF4C94264608D89FEAC36121F842B.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
             }
         }    
            
            
        stage('verify Deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://8D5DF4C94264608D89FEAC36121F842B.gr7.us-east-1.eks.amazonaws.com']]) {
                   sh "kubectl get all -n webapps"
               }
            }
        }
    }
}
