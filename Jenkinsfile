pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { git 'https://github.com/venkatakrishna2023-source/agile-4.git' }
        }
        stage('Docker Build') {
            steps { sh 'docker build -t your-docker-id/static-web:latest .' }
        }
        stage('Docker Push') {
    steps {
        // 'docker-hub-id' is the nickname you created in Step 1
        // 'USER' and 'PASS' are temporary nicknames for this script
        withCredentials([usernamePassword(credentialsId: 'docker-hub-id', usernameVariable: 'venkata.krishna2023@vitstudent.ac.in', passwordVariable: '#spidyJvk#15')]) {
            bat "docker login -u %USER% -p %PASS%"
            
            // Replace 'your-docker-id' with your actual Docker Hub username
            bat 'docker push venkat23mis0428/static-web:latest'
        }
    }
}
        stage('K8s Deploy') {
            steps { sh 'kubectl apply -f k8s-deployment.yaml' }
        }
    }
}