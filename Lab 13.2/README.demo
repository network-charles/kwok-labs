# Scheduling Pods with Affinity and Anti-Affinity

## Create cluster
kwokctl create cluster

## View clusters
kwokctl get clusters

## Deploy node
kwokctl scale node node-1 --replicas 1 --param '.allocatable.cpu="4000m"'
kwokctl scale node node-2 --replicas 1 --param '.allocatable.cpu="2000m"'

## Label node-1
kubectl label node node-1 region=us-west-2

## Deploy pods
kubectl apply -f pod.yaml

## View the node the pod is scheduled to
kubectl get pod -o wide

## Delete the cluster
kwokctl delete cluster
