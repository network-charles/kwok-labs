# Record and replay a cluster but save resources.

# Let's get started with kwokctl!
kwokctl create cluster

# Create an nodes.
kwokctl scale node --replicas 2

# Use context
kubectl cluster-info --context kind-kind

# Apply a deployment.
kubectl create deployment app --image=app --replicas=3

# Let's have a look at the pod name.
kubectl get pod

# Save it to cluster.yaml
kwokctl snapshot record --snapshot --path ./cluster.yaml

# Recreate cluster.
kwokctl delete cluster > /dev/null 2>&1 && kwokctl create cluster > /dev/null 2>&1

# Restore is from cluster.yaml
kwokctl snapshot replay --snapshot --path ./cluster.yaml

# Let's have a look at the pod name again.
kubectl get pod

# Delete the cluster.
kwokctl delete cluster

# That's all, enjoy it!
clear