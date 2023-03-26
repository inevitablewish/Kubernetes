How to access Cloud managed Kubernetes Cluster from local computer.

Ensure you are connected with EKS Cluster using the following AWS Command

`	`aws eks --region example\_region update-kubeconfig --name cluster\_name

1. Ensuring you have access to Cloud Environment in general and can use the keys to establish connection with cloud environment.
1. Access the Environment’s CloudShell and use the following command

kubectl edit -n kube-system configmap/aws-auth

1. This will open a manifest which requires to be updated
'''
apiVersion: v1
data:
  mapRoles: |
    - groups:
      - system:bootstrappers
      - system:nodes
      rolearn: arn:aws:iam::AWS ACCOUNT ID:role/mohsin-AmazonEKSNodeRole
      username: system:node:{{EC2PrivateDNSName}}
  mapusers: |
    - userarn: ARN of user created the cluseter
      username: mohsin
      groups:
        - system:masters
  mapAccounts: |
    - "AWS ACCOUNT NUMBER"
kind: ConfigMap
metadata:
  creationTimestamp: "2023-03-25T03:14:14Z"
  name: aws-auth
  namespace: kube-system
  resourceVersion: "27434"
  uid: XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
  '''

1. The above highlighted information is required to be added and saved.
1. Once done, you can test it by listing the cluster nodes from local computer (Ensuring KUbectl is already installed on local computer)

kubectl get nodes.
