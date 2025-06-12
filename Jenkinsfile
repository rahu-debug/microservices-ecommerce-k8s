pipeline {
    agent any
    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9EDF462BBB5CD1235518CF1226D4529F.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'demo-eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://9EDF462BBB5CD1235518CF1226D4529F.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
