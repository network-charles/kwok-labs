# Deploy kwok in a KIND Cluster

## Create Kind cluster
kind create cluster --config kind.yml

## Variable preparation
### KWOK repository
KWOK_REPO=kubernetes-sigs/kwok
### Get latest
KWOK_LATEST_RELEASE=$(curl "https://api.github.com/repos/${KWOK_REPO}/releases/latest" | jq -r '.tag_name')

## Deploy kwok and set up custom resource definitions (CRDs) #
kubectl apply -f "https://github.com/${KWOK_REPO}/releases/download/${KWOK_LATEST_RELEASE}/kwok.yaml"

## Set up default custom resources (CRs) of stages (required) 
kubectl apply -f "https://github.com/${KWOK_REPO}/releases/download/${KWOK_LATEST_RELEASE}/stage-fast.yaml"

## Create deployment and node port service
kubectl apply -f deployment.yml
kubectl apply -f service.yml
sleep 5s

## Set up default custom resources (CRs) of resource usage (optional)
kubectl apply -f "https://github.com/${KWOK_REPO}/releases/download/${KWOK_LATEST_RELEASE}/metrics-usage.yaml"

## Access the NodePort
http://localhost:30950

## Delete Kind cluster
kind delete cluster -n kind
