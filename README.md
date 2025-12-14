# traefik

## Prerequisites:

Linux amd64 Ubuntu 22.04.5 LTS (Jammy Jellyfish)

1. Install minikube:
```
curl -LO https://github.com/kubernetes/minikube/releases/download/v1.36.0/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```
Verify installation:
```
minikube version
```


2. Install kubectl:
```
curl -LO "https://dl.k8s.io/release/v1.34.1/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/kubectl
```
- Verify installation:
```
kubectl version
```

3. Install helm

```
curl -LO https://get.helm.sh/helm-v3.19.2-linux-amd64.tar.gz
tar -zxvf helm-v3.19.2-linux-amd64.tar.gz
sudo mv linux-amd64/helm /usr/local/bin/helm
```

## Installation:


1. Start a minikube cluster:

```
minikube start -p test-traefik --kubernetes-version=v1.33.0 --cpus=4 --memory=4096
```

2. Check the nodes:
```
kubectl get nodes
```

3. Activate profile of minikube:
```

minikube profile list

minikube profile test-traefik



```


5. 
```
helm repo add traefik https://traefik.github.io/charts

helm search repo traefik

helm show values traefik/traefik --version 37.4.0 > values.yaml

helm upgrade --install traefik traefik/traefik --version 37.4.0 --namespace traefik --create-namespace --values values.yaml


```

6. Get the IP of the LoadBalancer and go to http://<ip-load-balancer>/api



- Delete minikube:
```
minikube delete -p test-traefik
```
