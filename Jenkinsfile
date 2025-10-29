pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rohit1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://9A56EE40F7DCDE3A9ACEA20F4762E843.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-rohit1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://9A56EE40F7DCDE3A9ACEA20F4762E843.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
