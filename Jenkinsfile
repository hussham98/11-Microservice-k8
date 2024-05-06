pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://228BEE7EC1D53DFFCC3EB313190442E5.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh 'kubectl apply -f deployment-service.yml'
                }
            }
        }
        stage('Verify Kubernetes Deployment) {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://228BEE7EC1D53DFFCC3EB313190442E5.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh 'kubectl get all -n webapps'
                }
            }
        }
    }
}
