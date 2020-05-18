**NB! Doesn't fully work because of [this](https://github.com/dockersamples/example-voting-app/issues/162#issuecomment-613201534).**

```bash
kubectl create -f voting-app-pod.yml
kubectl create -f voting-app-service.yml
kubectl create -f redis-pod.yml
kubectl create -f redis-service.yml
kubectl create -f postgres-pod.yml
kubectl create -f postgres-service.yml
kubectl create -f result-app-pod.yml
kubectl create -f result-app-service.yml
```

Get IP:

```bash
kubectl get services
# get external IP of voting-service and result-service and go to http://<external IP>
```
