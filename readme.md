# k8n

- minikube commends
<https://github.com/adv4000/k8s-lessons>

```sh
# create local cluster
minikube start --nodes 3 -p k8-ant
kubectl get nodes
kubectl label node <node name> node-role.kubernetes.io/worker=worker
kubectl label nodes k8-ant-m02 role=worker
minikube status -p k8-ant

# - expected output
# ```sh
# k8-ant
# type: Control Plane
# host: Running
# kubelet: Running
# apiserver: Running
# kubeconfig: Configured

# k8-ant-m02
# type: Worker
# host: Running
# kubelet: Running

# k8-ant-m03
# type: Worker
# host: Running
# kubelet: Running
# ```

minikube -p=k8-ant addons enable metrics-server && \
minikube -p=k8-ant addons enable ingress && \
minikube -p=k8-ant addons enable dashboard && \
minikube -p=k8-ant addons list


## work with local cluster nodes

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

## mini kube loadBalancer

- <https://minikube.sigs.k8s.io/docs/handbook/accessing/>

```sh
# create tunnel first
minikube tunnel

# create service
kubectl expose deployment app-v1 --type=LoadBalancer --port=8000 --target-port=8000
```
