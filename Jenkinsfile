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
                      
                       sh 'sudo docker tag python-app:v2 gcr.io/searce-playground/python-app:v2'
                     
                       sh 'sudo docker push gcr.io/searce-playground/python:v3'

                      
                    }
                }
            }
        }
    }
}

