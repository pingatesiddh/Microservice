pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1234', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://25B24BC0163FEDF3638B9F74E7D3E7AA.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1234', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://25B24BC0163FEDF3638B9F74E7D3E7AA.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get all -n webapps"
                }
                    
            }
        }
    }
}
