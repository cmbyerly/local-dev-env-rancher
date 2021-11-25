# Local Rancher Development Environment

These are the files I use for my local rancher development.

## Prerequisites

[Best video for learning Kubernetes](https://www.youtube.com/watch?v=X48VuDVv0do)

## Instructions

1. Turn off docker
2. Install WSL2 - Debian
3. Install [rancher desktop](https://rancherdesktop.io/)
4. Helm and Kubectl is installed as part of rancher.
5. Install Portaianer

    - `kubectl get sc`
    - `helm repo add portainer https://portainer.github.io/k8s/`
    - `helm repo update`
    - `helm install --create-namespace -n portainer portainer portainer/portainer --set service.type=LoadBalancer`
    - Go to the [admin page](http://localhost:9000) to setup the portainer admin user

6. Install other services

    - `helm repo add bitnami https://charts.bitnami.com/bitnami`
    - `helm repo update`
    - `helm install mongodb bitnami/mongodb -f mongodb-values.yaml`
    - `helm install postgresql bitnami/postgresql -f postgres-values.yaml`
    - `helm install redis bitnami/redis -f redis-values.yaml`
    - `helm install elasticsearch bitnami/elasticsearch -f elastic-values.yaml`
    - `helm install rabbitmq bitnami/rabbitmq -f rabbitmq-values.yaml`
    - `helm install kibana bitnami/kibana -f kibana-values.yaml`

7. Takes about 20 minutes to spin everything up.

## Notes

- Default rabbitmq user is user and the password is in portainer.
- The other password should be available in portainer through applications.
- [Go to bitnami](https://bitnami.com/stacks/helm) if you want to expore other helm stacks from bitnami.
