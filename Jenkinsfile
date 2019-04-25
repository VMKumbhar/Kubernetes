pipeline {
    agent any
    environment {
        
        registry = "princysearce/python-app"
        registryCredential = 'docker_hub_login'
   
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
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') 
                    {
                      
                        sh 'sudo docker login -u princysearce -p Princy8296'
                        sh 'sudo docker tag test princysearce/test'
                        sh 'sudo docker push princysearce/test'

                      
                    }
                }
            }
        }
    }
}

