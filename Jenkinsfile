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
                withCredentials([file(credentialsId: "${searce-playground}", variable: 'JENKINSGCLOUDCREDENTIAL')])
                script {
                    
                    sh 'gcloud auth activate-service-account --key-file=${JENKINSGCLOUDCREDENTIAL}'
                    sh 'sudo gcloud auth configure-docker'   
                    sh 'sudo docker push gcr.io/searce-playground/python'

                      
                    }
                }
            }
        }
    }


