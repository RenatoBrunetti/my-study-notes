# Kubernetes Service
[main](../../README.md) | [devops](../README.md) | [kubernetes](README.md) | [service](Service.md)

## About Service
Service is a set of instructions to define the deployment rules and strategy.

---

## Service Types
### ClusterIp
This service doesn't provide an external access.

[ POD ] -> [ SERVICE ] -> [ PODS ]

### NodePort
This service provides and external access through a default range of ports.

[ PORT ACCESS ] -> [ SERVICE ] -> [ POD ] -> [ SERVICE ] -> [ PODS ]

### LoadBalancer
This service provides and external access through an IP number. This service type is often used by cloud providers.

[ USER ] -> [ LOADBALANCER ] -> [ SERVICE ] -> [ POD ] -> [ SERVICE ] -> [ PODS ]

---

## Services Requirements:

### 1. Open the deployment manifest file
```sh
cat deployment.yaml
```

### 2. Set a service settings in the deployment manifest file
```yaml
#deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: myfirstdeployment
spec:
  replicas: 10
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
        - name: web
          image: nginx
          ports:
            - containerPort: 80

---
# Service settings is right here:

apiVersion: v1
kind: Service
metadata:
  name: service-web
spec:
  selector:
    app: web
  ports:
    - protocol: TCP
      port: 80
      nodePort: 30000
  type: NodePort

```

---

## Deployment Commands
```sh
# List all deployment
kubectl get services
```
