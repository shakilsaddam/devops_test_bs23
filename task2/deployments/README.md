kubernetes-dashboard-deployment.yml is downloaded from https://raw.githubusercontent.com/kubernetes/dashboard/master/aio/deploy/recommended.yaml that contains all the required commands to deploy kubernetes dashboard.
Service part is slightly changed to enable NodePort so that we can access the Dashboard from outside of the Cluster. After the deployment is completed you can access it using https://<node-ip>:<nodeport>

kubernetes-metric-server.yml is downloaded from https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml contains required steps to deploy Kubenetes Metric Server. 

**dashboard-admin.yml** contains **Service Account** roles and cluster role binding codes..

Get the admin token using the command below. This is used during logging into Kubenetes Dashboard.
```
kubectl get secret -n kubernetes-dashboard $(kubectl get serviceaccount admin-user -n kubernetes-dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode
```


