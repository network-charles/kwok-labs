# Do some performance testing using Yunikorn

# Let's get started with kwokctl!
kwokctl create cluster --prometheus-port 9090

# Create nodes
./kwok-setup.sh 5000
This command creates 5000 nodes.

# To create deployments with an interval of 10 seconds between each deployment:
./deploy-tool.sh -i 10 5 3
This command will create 5 deployments, each with 3 replicas, with a 10-second interval between each deployment.

./deploy-tool.sh -i 3 50 100
This command will create 50 deployments, each with 100 replicas

./deploy-tool.sh -d 50 100
This command will delete 50 deployments, each with 100 replicas.

# Let's have a look at the pod name again.
kubectl get pod

# Install Prometheus

## Create grafana dashboard with prometheus data source
docker run -d --name=grafana -p 3000:3000 docker.io/grafana/grafana:9.4.7

See [docs](https://kwok.sigs.k8s.io/docs/examples/prometheus/) for more details.

## Access grafana
http://localhost:3000
On the login page, enter admin for username and password.
Add prometheus data source.
Import dashboard via grafana.com code 16248 on Grafana.

## Access prometheus
http://localhost:9090

# Test Case 1: Single Application Deployment:
# Deploy 1 application with 100 pods on 2 nodes.
kubectl apply -f deployment.yml

# Measure the makespan and throughput.
Makespan = 1m30s
Throughput
KubeAPI-Server = From 21.5ms to a spike of 37ms

# Delete the cluster.
kwokctl delete cluster

# That's all, enjoy it!
clear