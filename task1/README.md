## Project Overview and Step by Step Instructions

### Building Docker Images
Firstly, latest laravel project is cloned and modified as per the requirement. `Dockerfile` has all the required instructions to containarize the application. By executing following commands 2 docker images are created.
```
docker build -t shakilsaddam/laravel-app1 <Dockerfile_Dir>
docker build -t shakilsaddam/laravel-app2 <Dockerfile_Dir>
```

### Pushing Docker Images to Docker Hub
Create 2 repo in Docker Hub named laravel-app1, and laravel-app2 
```
docker login
docker push shakilsaddam/laravel-app1
docker push shakilsaddam/laravel-app2
```

You can find those Docker Images: <br/>
App1: https://hub.docker.com/repository/docker/shakilsaddam/laravel-app1 <br/>

App2: https://hub.docker.com/repository/docker/shakilsaddam/laravel-app2

`app1/deploy` directory contains kubernetes deployment and service yaml files.

## Deploying Applications to Minikube a lightweight distribution of Kubernetes. <br/>

Prerequisites: <br/>
1. Docker for Mac
2. VirtualBox
3. kubectl - easy installation `brew install kubectl` on Macos

Now, Install Minikube.

After the installation is completed use the follwing commands to create a Cluster (1 Master, 2 Worker)
```
minikube start --nodes 3 -p multinode-demo
```
It will take a few minutes to spin up the cluster. Now the cluster is ready to deploy applications. You can simply create the deployment and services into the cluster by executing the follwing commands for both App1 and App2:
```
kubectl create -f app1/deploy/deploy-definition.yml
kubectl create -f app1/deploy/service-definition.yml
```
Now the applications are live and can be accessed through <http://Node-IP:NodePort>




You can access this app using <Docker-Host-IP:3000>