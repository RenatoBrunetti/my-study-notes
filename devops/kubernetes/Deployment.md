# Kubernetes Deployment
[main](../../README.md) | [devops](../README.md) | [kubernetes](README.md) | [deployment](Deployment.md)

## About Deployment
Deployment is a set of instructions to ensure the properly version of replicaset and pods definitions during the execution.

---

## Deployment Requirements:

### 1. Create a deployment manifest file
```sh
touch deployment.yaml
```

### 2. Set a deployment manifest file
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

```

---

## Deployment Commands
```sh
# Check all api-resources information
kubectl api-resources

# Check only Deployment api-resources information
kubectl api-resources | grep deployment

# Apply the pod definitions
kubectl apply -f deployment.yaml

# List all deployment
kubectl get deployment
kubectl get deploy

# List rollout history
kubectl rollout history deployment <deployment_name>

# Run the rollback
kubectl rollout undo deployment <deployment_name>

# Delete a deployment by manifest
kubectl delete -f deployment.yaml
```
