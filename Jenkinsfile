pipeline {
    agent any
    environment {
        
        registry = "princysearce/python-app"
        registryCredential = 'Princy8296'
   
        //be sure to replace "willbla" with your own Docker Hub username
        DOCKER_IMAGE_NAME = "princysearce/python-app:v2"
    }
    stages {
        stage('Build') {
            steps {
                sh 'sudo docker build -t test python'
            }
        }
        stage('Push Docker Image') {
            
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') {
                        sh 'sudo docker push -t test python'
                      
                    }
                }
            }
        }
    }
}

