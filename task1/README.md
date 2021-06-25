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


## Installing and Configuring Jenkins CI/CD Environment
To install Jenkins on Docker, you need to to `jenkins-docker` directory and execute the below command:
```
docker-compose up -d
```
Jenkins now should be accessible through http://Docker-Host-IP:9090/ <br/>

You have to go throught some streight-forward steps to get the Jenkins installation done.

To achieve CI/CD for Docker and Kubernetes Deploy we need to install some required jenkins plugins such as `Kubernetes, Kubernetes Credentials, Kubernetes Continuous Deploy, Docker Pipeline plugin, etc.`

After all the required plugins are installed, we will create 2 Jenkins Pipeline (one is for App1, and another is for App2) using the jenkins web UI. 

We will provide the git repo link so that all the required Jenkinsfiles or other configuration files can be consumed by Jenkins Pipeline easily.

Jenkins pipeline codes can be found respectively in `app1` and `app2` directory.