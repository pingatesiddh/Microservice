pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://87ED6328C89F5C1F3C72802924E18A98.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://87ED6328C89F5C1F3C72802924E18A98.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
                    
            }
        }
    }
}
