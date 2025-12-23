# Kubernetes PoC v1 Java
This is a simple "Hello World" PoC deployed on local using Kubernetes (kind)  

## Dependencies
1. Docker
2. Kubernetes CLI (kubectl)
3. Java 21
4. kind
5. Maven (Spring Web)

## Clone the PoC
```bash
  git clone https://github.com/Tabish-NonStop/poc-v1-java.git
```

## Create the docker image
From the project root (where Dockerfile exists):  
```bash
  docker build -t poc-v1-java:1.0 .
```

## Create the kind cluster
```bash
kind create cluster
```

## Load the PoC docker image in to the kind cluster
```bash
  kind load docker-image poc-v1-java:1.0
```

## Deploy to Kubernetes
```bash
  kubectl apply -f kubernetes/k8s.yaml
```

## Forward the ports
```bash
  kubectl port-forward svc/poc-v1-java-svc 8080:80
```

## Test 
```bash
curl http://localhost:8080/v1/message
```

Expected Response Content: Hello World
