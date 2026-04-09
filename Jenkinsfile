pipeline {
    agent any
    environment {
        
        DOCKER_USER = 'venkat23mis0428'
        IMAGE_NAME = 'static-web'
    }
    stages {
        stage('Checkout') {
            steps {
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
        withCredentials([usernamePassword(credentialsId: 'docker-hub-id', usernameVariable: 'venkatakrishna2023', passwordVariable: '#spidyJvk#15')]) {
           
            bat "docker login -u %DOCKER_USER% -p %DOCKER_PASS%"
            bat "docker push %DOCKER_USER%/static-web:latest"
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
