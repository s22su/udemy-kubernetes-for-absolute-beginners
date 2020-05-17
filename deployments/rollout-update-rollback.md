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
