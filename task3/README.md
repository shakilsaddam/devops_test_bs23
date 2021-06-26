## A Highly Available Microservices Architecture

! [Highly Available Kubernetes Cluster](https://github.com/shakilsaddam/devops_test_bs23/blob/master/task3/diagrams/HighlyAvailable-K8S-Cluster.jpeg)

The Cluster is designed to achieve Highly Available Kubernetes in one region and N availability zones. 

One master node per zone, associated with one Autoscalling Group for all zones.

One API ELB associated with one API FQDN for serving API requests.

Multiple Worker nodes per zone, associated with one Autoscalling Group for all zones.

Worker ASG associates itself with the API ELB to register its worker nodes for load distribution. When autoscaling workers, the ELB is automatically notified of new worker nodes.

### Infrastructure as a code
Terraform would be a very good option for Kubernetes Cluster Deployment and Managing Kubernetes Resources as well.


### CI/CD strategies


### Architecture Observability


### Monitoring


### Justification for Cloud Solution among On-premise, Cloud, and Hybrid.


