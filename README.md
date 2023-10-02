## Load Balancer Endpoint
http://a0ff404d4cdff458f9759c4a49b41a3b-1250996170.us-east-1.elb.amazonaws.com

## Kubernetes Cluster

I used AWS CloudFormation to deploy the Kubernetes Cluster.
The CloudFormation Deployment can be broken down into four Parts:
- **Networking**, to ensure new nodes can communicate with the Cluster
- **Elastic Kubernetes Service (EKS)** is used to create a Kubernetes Cluster

## CircleCi - CI/CD Pipelines

I used CircleCi to create a CI/CD Pipeline to test and deploy changes manually before they get deployed automatically to the Cluster.

## Access the Application

After the EKS-Cluster has been successfully configured using Ansible within the CI/CD Pipeline, I checked the deployment and service as follows:
```
root@DESKTOP-FJ4DGAG:~# kubectl get deployments
NAME           READY   UP-TO-DATE   AVAILABLE   AGE
capstone-dev   3/3     3            3           26m

root@DESKTOP-FJ4DGAG:~# kubectl get services
NAME           TYPE           CLUSTER-IP       EXTERNAL-IP                                                               PORT(S)        AGE
capstone-dev   LoadBalancer   10.100.100.128   a0ff404d4cdff458f9759c4a49b41a3b-1250996170.us-east-1.elb.amazonaws.com   80:31280/TCP   26m
kubernetes     ClusterIP      10.100.0.1       <none>                                                                    443/TCP        4h28m
```
## GitHub URL
https://github.com/26shine/udacity-capstone