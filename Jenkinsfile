pipeline {
    agent any
    environment {
        //be sure to replace "willbla" with your own Docker Hub username
        DOCKER_IMAGE_NAME = "princysearce/python-app:v2"
    }
       stages {
        stage('Build') {
            steps {
                sh 'whoami'
                sh 'sudo docker build -t test python'
            }
        }
    }
}
