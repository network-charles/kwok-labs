# Simulate pod create

## Create Kind cluster
kind create cluster --config kind.yml

## Variable preparation

### KWOK repository
KWOK_REPO=kubernetes-sigs/kwok

### Get latest
KWOK_LATEST_RELEASE=$(curl "https://api.github.com/repos/${KWOK_REPO}/releases/latest" | jq -r '.tag_name')

## Deploy kwok and set up custom resource definitions (CRDs)
kubectl apply -f "https://github.com/${KWOK_REPO}/releases/download/${KWOK_LATEST_RELEASE}/kwok.yaml"

## Set up default custom resources (CRs) of stages (required) 
kubectl apply -f "https://github.com/${KWOK_REPO}/releases/download/${KWOK_LATEST_RELEASE}/stage-fast.yaml"

## Apply a stage and a pod
kubectl apply -f stage.yaml
kubectl apply -f pod.yaml
watch kubectl get pod

## View stages
kwokctl kubectl get stages

## Delete the cluster
kwokctl delete cluster

## That's all, enjoy it
clear
