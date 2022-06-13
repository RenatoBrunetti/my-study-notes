# Kubernetes Replicaset
[main](../../README.md) | [devops](../README.md) | [kubernetes](README.md) | [replicaset](Replicaset.md)

## About Replicaset
Replicaset is a set of instructions to ensure the properly pods definitions during the execution.

---

## Replicaset Requirements:

### 1. Create a replicaset manifest file
```sh
touch replicaset.yaml
```

### 2. Set a replicaset manifest file
```yaml
#replicaset.yaml

apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: myfristreplicaset
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

## Replicaset Commands
```sh
# Check all api-resources information
kubectl api-resources

# Check only Replicaset api-resources information
kubectl api-resources | grep replicaset

# Apply the pod definitions
kubectl apply -f replicaset.yaml

# List all replicaset
kubectl get replicaset

# Delete a replicaset by manifest
kubectl delete -f replicaset.yaml
```
