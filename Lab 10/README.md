# Create a pod lifecycle

## Let's get started with kwokctl!
kwokctl create cluster

## Create the nodes
kwokctl scale node --replicas 2

## Apply a deployment
kubectl apply -f fake-pod-stages.yaml

## Delete the cluster
kwokctl delete cluster

## That's all, enjoy it
clear
