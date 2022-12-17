# Simple EKS created by pulumi

set up correct aws configuration
```
aws configure
```


provision a VPC and EKS in us-east-1, the process take around 15 mins please be patient
```
pulumi up
```

get the kube configuration
```
pulumi stack output kubeconfig > kubeconfig
kubectl --kubeconfig=$PWD/kubeconfig get nodes
```

if you don't want to state the kubeconfig location in every time you execute the kubeconfig command
you could convert the kubeconfig to yaml first. then copy and replace the config file in your orignial kubeconfig file "user/.kube/config" (ecommended to back up the orignial config file first before replacing.)
then you would be able to execute the kubectl without state the kubeconfig location again. 


# DEBUG
if the pulumi is state was messup. you could login the aws to delete the NAT gateway.public ip. vpc manually.
and then run pulumi refresh to sync the state between pulumi state and the cloud provider.
```
pulumi refresh
```