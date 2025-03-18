# Create a simulated metric for your pods using K8s metric-server

## Fetch default metrics usage
wget https://github.com/kubernetes-sigs/kwok/releases/download/v0.5.1/metrics-usage.yaml

## Set up Cluster
kwokctl create cluster --enable-metrics-server -c metrics-usage.yml

## Create the nodes
kwokctl scale node --replicas 2

## Apply a deployment
kubectl apply -f deployment.yml

## Wait for 45s
sleep 45

## Get metrics
kubectl top node
kubectl top pods

## Delete the cluster
kwokctl delete cluster

## That's all, enjoy it
clear
