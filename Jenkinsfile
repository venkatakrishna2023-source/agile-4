pipeline {
    agent any
    environment {
        
        DOCKER_USER = 'venkat23mis0428'
        IMAGE_NAME = 'static-web'
    }
    stages {
        stage('Checkout') {
            steps {
                // Uses the branch and URL configured in the Jenkins Job UI
                checkout scm
            }
        }
        stage('Docker Build') {
            steps {
                bat "docker build -t %DOCKER_USER%/%IMAGE_NAME%:latest ."
            }
        }
        stage('Docker Push') {
            steps {
                // Uses the 'docker-hub-id' you created in Manage Jenkins > Credentials
                withCredentials([usernamePassword(credentialsId: 'docker-hub-id', usernameVariable: 'venkata.krishna2023@vitstudent.ac.in', passwordVariable: '#spidyJvk#15')]) {
                    bat "docker login -u %USER% -p %PASS%"
                    bat "docker push %DOCKER_USER%/%IMAGE_NAME%:latest"
                }
            }
        }
        stage('K8s Deploy') {
            steps {
                bat "kubectl apply -f k8s-deployment.yaml"
            }
        }
    }
}
