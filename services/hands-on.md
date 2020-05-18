**How many Services exist on the system?**

```bash
kubectl get services
```

**What is the 'targetPort' configured on the 'kubernetes' service?**

```bash
kubectl describe service kubernetes
```

**How many labels are configured on the 'kubernetes' service?**

```bash
kubectl describe service kubernetes
```

**How many Deployments exist on the system now?**

```bash
kubectl get deployments
```

**What is the image used to create the pods in the deployment?**

```bash
kubectl get deployments
```

**Create a new service to access the web application using the service-definition-1.yaml file**

**Name: webapp-service; Type: NodePort; targetPort: 8080; port: 8080; nodePort: 30080; selector: simple-webapp**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: webapp-service
spec:
  type: NodePort
  ports:
    - targetPort: 8080
      port: 8080
      nodePort: 30080
  selector:
    name: simple-webapp
```
