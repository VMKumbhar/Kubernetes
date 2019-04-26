pipeline {
    agent any
    environment {
        
        registry = "princysearce/python-app"
        registryCredential = 'docker_hub_login'
   
        //be sure to replace "willbla" with your own Docker Hub username
        DOCKER_IMAGE_NAME = "princysearce/python-app:v2"
    }
    stages {
        stage('Build image') {
            app = docker.build("searce-playground/python", "./python/")
        }
        stage('Push image') {
            docker.withRegistry('https://gcr.io', 'gcr:[searce-playground]') {
                app.push("${env.BUILD_NUMBER}")
            }
        }
    }
}

