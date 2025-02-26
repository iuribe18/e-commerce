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
                    serverUrl: 'https://2E847A9D342BCCAF904DA1D9CF11CA28.gr7.us-east-1.eks.amazonaws.com'
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
                    serverUrl: 'https://2E847A9D342BCCAF904DA1D9CF11CA28.gr7.us-east-1.eks.amazonaws.com'
                ]]) {
                    sh 'kubectl get svc -n webapps'
                } 
            }
        }
    }
}
