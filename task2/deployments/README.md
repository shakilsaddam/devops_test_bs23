## Deploying Kubernetes Dashboard and Metric Server

kubernetes-dashboard-deployment.yml contains all the required commands to deploy kubernetes dashboard. This file is actually available at Kubernetes repo.
`Service` part is slightly changed to enable `NodePort` so that we can access the Dashboard from outside of the Cluster. After the deployment is completed you can access it using <https://Node-IP:nodePort>

kubernetes-metric-server.yml file contains required steps to deploy Kubenetes Metric Server. 

**dashboard-admin.yml** contains **Service Account** roles and cluster role binding codes..

To access the Kubernetes it needs a secured token to initialize the service.
To get the admin token we can use the following command. This is used during logging into Kubenetes Dashboard.
```
kubectl get secret -n kubernetes-dashboard $(kubectl get serviceaccount admin-user -n kubernetes-dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
```

