pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'disney', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://63512A08DEE68099AD7BED67C19453AB.gr7.us-east-1.eks.amazonaws.com'
                ]]) {
                    sh 'kubectl apply -f deployment-service.yml' // our main branch file
                } 
            }
        }

        stage('Verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'disney', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://63512A08DEE68099AD7BED67C19453AB.gr7.us-east-1.eks.amazonaws.com'
                ]]) {
                    sh 'kubectl get svc -n webapps'
                } 
            }
        }
    }
}