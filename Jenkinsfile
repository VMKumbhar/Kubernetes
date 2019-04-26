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
        stage('Deploy Application') {
            steps {
                script {
                    sh("gcloud container clusters get-credentials princy-trial-cluster --zone asia-south1-a --project searce-playground")
                        
                    sh("kubectl apply -f python/deployment.yaml")
                    sh("kubectl apply -f python/service.yaml")
                    
                    // echo 'To access your environment run `kubectl proxy`'
                    echo "Then access your service via http://35.244.63.56:5000"
                    //sh("echo http://`kubectl --namespace=${namespace} get service/${feSvcName} --output=json | jq -r '.status.loadBalancer.ingress[0].ip'` > ${feSvcName}")
                }
            }
        }

    }
}

