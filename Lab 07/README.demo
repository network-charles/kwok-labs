# Install Kind and Backup the etcd to be restored using kwokctl

## Create Kind cluster
kind create cluster --config cluster.yml

## Create deployment and node port service
kubectl apply -f deployment.yml
kubectl apply -f service.yml
sleep 5s

## Access the NodePort
http://localhost:30950

## Export External Cluster
kwokctl snapshot export --path external-snapshot.yaml --kubeconfig /home/ubuntu/.kube/config

## Restore External Cluster
kwokctl create cluster
kubectl cluster-info --context kwok-kwok
kwokctl snapshot replay --path external-snapshot.yaml --snapshot

## Delete Kind cluster
kind delete cluster -n kind

## Delete kwokctl cluster
kwokctl delete cluster

## Delete resources
clear
