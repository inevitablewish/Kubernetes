How to access Cloud managed Kubernetes Cluster from local computer.

Ensure you are connected with EKS Cluster using the following AWS Command

`	`aws eks --region example\_region update-kubeconfig --name cluster\_name

1. Ensuring you have access to Cloud Environment in general and can use the keys to establish connection with cloud environment.
1. Access the Environment’s CloudShell and use the following command

kubectl edit -n kube-system configmap/aws-auth

1. This will open a manifest which requires to be updated


1. The above highlighted information is required to be added and saved.
1. Once done, you can test it by listing the cluster nodes from local computer (Ensuring KUbectl is already installed on local computer)

kubectl get nodes.
