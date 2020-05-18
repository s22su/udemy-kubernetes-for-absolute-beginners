```bash
kubectl create -f .
kubectl get services
# get external IP of voting-service and result-service and go to http://<external IP>
```

**NB! Some services might not work straight away as some service might not be ready and pods need to be deleted
for that service (they will start automatically).**
