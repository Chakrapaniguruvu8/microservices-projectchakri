pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-chakri1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://C0BA38F3B5C14D3A4DDF48E58F515570.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-chakri1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://C0BA38F3B5C14D3A4DDF48E58F515570.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
