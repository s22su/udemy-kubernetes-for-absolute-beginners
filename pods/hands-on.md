```bash
kubectl run nginx --image=nginx
kubectl get pods -o wide
kubectl describe pod webapp
```

**What does the READY column in the output of the 'kubectl get pods' command indicate?**

> Running containers in POD / total containers in POD

**Delete the 'webapp' Pod.**

```bash
kubectl delete pod webapp
```

**Create a new pod with the name 'redis' and with the image 'redis123'
Use a pod-definition YAML file. And yes the image name is wrong!**

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: redis
spec:
  containers:
    - name: redis
      image: redis123
```

```bash
kubectl create -f redis123.yml
```

**Now fix the image on the pod to 'redis'.**

```bash
kubectl apply -f redis123.yml
```

OR

```bash
kubectl edit pod redis
```
