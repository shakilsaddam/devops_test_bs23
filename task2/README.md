# Kubernetes Cluster Setup

This repo cantains required instructions and scripts for Spinning up a Kubernetes Cluster using Vagrant and Ansible.

### Prerequisites
- VirtualBox
- Vagrant
- Ansible

After installing all the prerequisites, clone the code from git repo and go to CM directory and run the bellow command.
```
$ vagrant up
```
It will create a complete ready Kubernetes Cluster which contains 1 Master and 2 Worker Nodes. Calico network plugin for CNI will also configured automatically. Provisioning Master and Workers VMs are done by Vagrant scripts, and downloading, installing, configuring the cluster is done by Ansible scripts. Ansible script also contains the CNI setup instructions.

### Spin up cluster
```
$ vagrant up
```

### Verify on master
```
$ vagrant ssh k8s-master
$ kubectl get nodes
NAME         STATUS   ROLES                  AGE     VERSION
k8s-master   Ready    control-plane,master   5m37s   v1.20.0
node-1       Ready    <none>                 3m38s   v1.20.0
node-2       Ready    <none>                 78s     v1.20.0
```

Now, you are ready to deploy applications to the Cluster.