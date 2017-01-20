# Sample Node.js app running on Kubernetes

A simple Node.js application with deployment to a Kubernetes cluster running on AWS. Kube cluster set up using KOPS.

Instructions for launching the cluster:
https://kubernetes.io/docs/getting-started-guides/kops/

OPTIONAL: specify an existing AWS key pair to use for SSH access to the cluster
```
AWS_SSH_KEY={your key pair name}
```

Build the cluster configuration:
```
kops create cluster --zones=us-east-1c useast1.dev.example-kube-cluster.com
```

Create the cluster in AWS:
```
kops update cluster useast1.dev.example-kube-cluster.com --yes
```

To add a Kube UI:
```
kubectl create -f https://raw.githubusercontent.com/kubernetes/kops/master/addons/kubernetes-dashboard/v1.4.0.yaml
kubectl proxy
```
Then navigate to http://127.0.0.1:8001/ui

Delete the cluster:
```
kops delete cluster useast1.dev.example-kube-cluster.com --yes
```

To add ability to pull images from private registry:
https://kubernetes.io/docs/user-guide/images/#specifying-imagepullsecrets-on-a-pod
