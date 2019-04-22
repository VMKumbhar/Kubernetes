1. Create a directory 
```
$ mkdir docker-python && cd docker-python
```
2. Create Dockerfile 
3. Create a Python file as index.py
4. Create Docker Image
```
$ docker build -t python-app:v1 .
$ docker images
```
5. To test the image(optional)
```  
$ docker run python-app:v1 
```
6. Push image to docker hub
```
$ docker tag python-app:v1 username/python-app:v1
$ docker push username/python-app:v1
```
7. Deploy minicube cluster
```
$ minikube start 
$ minikube cluster-info
$ kubectl get namespaces/pods/deployments
```
8. Create deployment.yaml that creates namespace named *development* and deployment for our app
``` 
   $ kubectl create -f deployment.yaml
   $ kubectl get deployments -n development
```
9. Create service.yaml with type LoadBalancer
```
$ kubectl create -f service.yaml
$ kubectl get svc -n development
$ curl http://IP:5000
```
