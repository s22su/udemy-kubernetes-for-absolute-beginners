# Hands on

**How many Deployments exist on the system now?**

```bash
kubectl get all
# OR
kubectl get deployment
```

**How many ReplicaSets exist on the system now?**

```bash
kubectl get replicaset
```

**What is the image used to create the pods in the new deployment?**

```bash
kubectl get deployment -o wide
```

**Create a new Deployment using the 'deployment-definition-1.yaml' file located at /root/**

```bash
kubectl create -f deployment-definition-1.yaml
# Error from server (BadRequest): error when creating "deployment-definition-1.yaml": deployment in version "v1" cannot
# be handled as a Deployment: no kind "deployment" is registered for version "apps/v1"
# in scheme "k8s.io/kubernetes/pkg/api/legacyscheme/scheme.go:30"

# change "deployment" -> "Deployment"
kubectl create -f deployment-definition-1.yaml
```

**Create a new Deployment with the below attributes using your own deployment definition file**

**Name: httpd-frontend; Replicas: 3; Image: httpd:2.4-alpine**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: httpd-frontend
  labels:
    name: httpd-frontend
spec:
  replicas: 3
  template:
    metadata:
      name: myfrontend
      labels:
        app: myfrontend
    spec:
      containers:
        - name: http-server
          image: httpd:2.4-alpine
  selector:
    matchLabels:
      app: myfrontend
```

```bash
kubectl create -f my-deployment.yml
```

# Rollout-Update-Rollback

## Status

```bash
kubectl rollout status deployment/myapp-deployment
```

## History

```bash
kubectl rollout history deployment/myapp-deployment
```

## Strategies

### Recreate (not default)

Destorys all current instances and deploy new instances. App is inaccessible to users.

### Rolling update (default)

Take down the older version and bring up newer version one by one.

## Apply

```bash
kubectl apply -f deployment-definition.yml
```

```bash
# only updates deplyment, file will be not changed
kubectl set image deployment/myapp-deplyment nginx=nginx:1.9.1
```

## Rollback

```bash
kubectl rollout undo deployment/myapp-deployment
```
