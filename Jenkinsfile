pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'BabyBoss-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://4DD0BAE5D125B5A192A3BE018491A9B3.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                    
                }
            }
        }
        
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'BabyBoss-EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://4DD0BAE5D125B5A192A3BE018491A9B3.gr7.us-east-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}

