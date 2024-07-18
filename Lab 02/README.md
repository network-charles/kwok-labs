# Create an nginx deployment and exec into it

## Let's get started with kwokctl!
kwokctl -c ./exec.yml create cluster

## Create the nodes.
kwokctl scale node --replicas 2

## Apply a deployment.
kubectl apply -f deployment.yml

## Exec into the pod.
kubectl exec -it deployment/cluster-exec-deployment -- sh

## Delete the cluster.
kwokctl delete cluster

## That's all, enjoy it!
clear
