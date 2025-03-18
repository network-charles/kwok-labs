# Scheduling Pods with Resource Requests and Limits

## Create cluster
kwokctl create cluster

## View cluster
kwokctl get clusters

## Deploy node
kwokctl scale node node-1 --replicas 1 --param '.allocatable.cpu="2000m"'
kwokctl scale node node-2 --replicas 1 --param '.allocatable.cpu="4000m"'

## Deploy pods
kubectl apply -f pod-1.yaml

kubectl apply -f pod-2.yaml

## View the node the pod is scheduled to
kubectl get pod -o wide

## View node resource usage
kubectl describe nodes node-1-000000 | awk '/Allocated resources:/,/ephemeral-storage/'
kubectl describe nodes node-2-000000 | awk '/Allocated resources:/,/ephemeral-storage/'

## Delete the cluster
kwokctl delete cluster



