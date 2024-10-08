# Record and replay a cluster without saving resources.

# Let's get started with kwokctl!
kwokctl create cluster

# Record it to recording.yaml
kwokctl snapshot record --path ./recording.yaml &

# Record some change.
kwokctl scale node --replicas 2
kubectl cluster-info --context kwok-kwok
kubectl create deployment app --image=app --replicas=3
kubectl delete deployment app
kwokctl scale node --replicas 0

# Finish the record.
pkill kwokctl

# Recreate cluster.
kwokctl delete cluster > /dev/null 2>&1 && kwokctl create cluster > /dev/null 2>&1

# Let's have a look at the resource change.
kubectl get node --watch &
kubectl get deployment --watch &
kubectl get pod --watch &

# Replay it from cluster.yaml
kwokctl snapshot replay --path recording.yaml

# Delete the cluster.
kwokctl delete cluster

# That's all, enjoy it!
clear