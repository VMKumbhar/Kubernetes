pipeline {
    agent any
    
    stages {
        stage('Build image') {
            steps {
                script {
                    app = docker.build("searce-playground/python", "./python/")
                }
            }
        }
        stage('Push image') {
            steps {
                script {        
                    docker.withRegistry('https://gcr.io', 'gcr:searce-playground') {
                        app.push("${env.BUILD_NUMBER}")
                    }
                }
            }
        }
    }
}

