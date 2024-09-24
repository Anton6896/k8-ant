# k8n

- minikube commends

```sh
# create local cluster
minikube start --nodes 3 -p k8-ant
kubectl label node <node name> node-role.kubernetes.io/worker=worker
kubectl label nodes <node name> role=worker
minikube status -p k8-ant

# work with local cluster nodes
minikube unpause -p k8-ant
minikube status -p k8-ant
minikube pause  -p k8-ant
```

## k8n commends

- run image as is

```sh
# create an pod
kubectl run ant-local --image=antonirr/ant-test-v1:tagname --port=8000

# deployment
kubectl create deployment ant-local --image=antonirr/ant-test-v1:tagname
```
