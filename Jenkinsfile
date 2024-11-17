pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://19919A20565641DF9CA8FED56A611499.sk1.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                
                }
            }
        }
        stage('Verify Deployment') { 
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://19919A20565641DF9CA8FED56A611499.sk1.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
                    
            }
        }
    }
}
