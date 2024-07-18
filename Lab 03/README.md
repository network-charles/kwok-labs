# Install Prometheus

## Let's get started with kwokctl
kwokctl -c exec.yml create cluster --prometheus-port 9090

## Create grafana dashboard with prometheus data source
docker run -d --name=grafana -p 3000:3000 docker.io/grafana/grafana:9.4.7

See [docs](https://kwok.sigs.k8s.io/docs/examples/prometheus/) for more details.

## Access grafana
http://localhost:3000
On the login page, enter admin for username and password.
Import dashboard via grafana.com code 16248 on Grafana.

## Access prometheus
http://localhost:9090

## Create nodes
kwokctl scale node --replicas 2

## Apply a deployment
kubectl apply -f deployment.yml

## Exec into the pod
kubectl exec deployment/cluster-exec-deployment -- sh

## Delete the cluster
kwokctl delete cluster

## Delete Grafana Container
docker stop <container-id>
docker rm  <container-id>

## That's all, enjoy it
clear
