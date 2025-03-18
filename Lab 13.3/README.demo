# Scheduling Pods with Taints and Tolerations

## Create cluster
kwokctl create cluster

## View clusters
kwokctl get clusters

## Deploy node
kubectl apply -f node.yaml

## Taint all nodes
kubectl taint nodes node kwok.x-k8s.io/node=fake:NoSchedule

## Deploy a pod without toleration and observe
kubectl apply -f no-toleration-pod.yaml

NAME                READY   STATUS    RESTARTS   AGE
no-toleration-pod   0/1     Pending   0          4s

The pod is stuck in a pending state.

## Deploy a pod with toleration and observe
kubectl apply -f with-toleration-pod.yaml

NAME                    READY   STATUS    RESTARTS   AGE
with-toleration-pod     1/1     Running   0          2s

The pod is in a running state.

## Delete the cluster
kwokctl delete cluster
