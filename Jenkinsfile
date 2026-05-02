pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'shiva', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6AB920D37EFF5D8ECE36D2A1E31E8DFF.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'shiva', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://6AB920D37EFF5D8ECE36D2A1E31E8DFF.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
