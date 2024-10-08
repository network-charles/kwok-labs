# kwokctl etcd snapshot 

# Let's get started with kwokctl!
kwokctl create cluster

# Use context
kubectl cluster-info --context kwok-kwok

# Create the nodes.
kwokctl scale node --replicas 2

# Apply a deployment.
kubectl create deployment app --image=app --replicas=3

# Let's have a look at the pod name.
kubectl get pod

# Save it to snapshot.db
kwokctl snapshot save --path snapshot.db

# Recreate cluster
kwokctl delete cluster > /dev/null 2>&1 && kwokctl create cluster > /dev/null 2>&1

# Restore is from snapshot.db
kwokctl snapshot restore --path snapshot.db

# Let's have a look at the pod name again.
kubectl get pod

# Delete the cluster.
kwokctl delete cluster

# That's all, enjoy it!
clear