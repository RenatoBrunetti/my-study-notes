# Kubernetes Pod
[main](../../README.md) | [devops](../README.md) | [kubernetes](README.md) | [pod](Pod.md)

## About Pod
Pod is the smallest part of a cluster.
It's where we create and run the containers.

Inside a pod we can have multiple containers that share the same network address, ip and filesystem.

---

⚠️ It's not properly to use multiple contexts for each pod.

Never set a pod with an API, a database and a web client frontend for example. You should set a pod for only an API, another pod for only a database and another pod for only a web client frontend.

---

## Pod Usage

- WEB_CLIENT_POD
  - nginx
- WEB_DATABASE_POD
  - postgres
  - log service (sidecar pattern)
- WEB_API_POD
  - node

---

## Pod Requirements:

### 1. Create a pod manifest file
```sh
touch pod.yaml
```

### 2. Set a pod manifest file
```yaml
#pod.yaml

apiVersion: v1
kind: Pod
metadata:
  name: myfirstpod
  labels:
    app: blue
spec:
  containers:
    - name: web
      image: nginx
      ports:
        - containerPort: 80
```

---

## Pod Commands
```sh
# Check all api-resources information
kubectl api-resources

# Check only Pod api-resources information
kubectl api-resources | grep pod

# Apply the pod definitions
kubectl apply -f pod.yaml

# List all pods
kubectl get pods

# List more info for all pods
kubectl get pods -o wide

# List pod description
kubectl describe pod <pod_name>

# Watch pod list
watch 'kubectl get pods'

# Set manually a port for a pod
kubectl port-forward pod/<pod_name> 8080:80

# Delete a pod by name
kubectl delete pod <pod_name>

# Delete a pod by filename
kubectl delete pod <pod_filename>

# Delete a pod by manifest
kubectl delete -f pod.yaml

# Select a pod by label
kubectl get pods -l <label_key>=<label_value>
```
