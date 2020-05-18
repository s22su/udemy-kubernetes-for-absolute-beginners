**How many PODs exist on the system?**

```bash
kubectl get pods
```

**How many ReplicaSets exist on the system?**

```bash
kubectl get replicaset
```

**What is the image used to create the pods in the new-replica-set?**

```bash
kubectl get replicaset -o wide
```

**Create a ReplicaSet using the 'replicaset-definition-1.yaml' file located at /root/**

**There is an issue with the file, so fix it.**

```bash
kubectl create -f replicaset-definition-1.yaml

# error: unable to recognize "replicaset-definition-1.yaml": no matches for kind "ReplicaSet" in version "v1"
# change v1 -> apps/v1

kubectl create -f replicaset-definition-1.yaml
```

**Fix the issue in the replicaset-definition-2.yaml file and create a ReplicaSet using it.**

```bash
kubectl create -f replicaset-definition-2.yaml

# The ReplicaSet "replicaset-2" is invalid: spec.template.metadata.labels:
# Invalid value: map[string]string{"tier":"nginx"}: `selector` does not match template `labels`

# change frontend -> nginx

kubectl create -f replicaset-definition-2.yaml
```

**Delete the two newly created ReplicaSets - replicaset-1 and replicaset-2**

```bash
kubectl delete replicaset replicaset-1
kubectl delete replicaset replicaset-2
```

**Fix the original replica set 'new-replica-set' to use the correct 'busybox' image**

**Either delete and re-create the ReplicaSet or Update the existing ReplicSet and then delete all PODs,
so new ones with the correct image will be created.**

```bash
kubectl edit replicaset new-replica-set
kubectl delete pods -l name=busybox-pod
```

**Scale the ReplicaSet to 5 PODs**

```bash
kubectl scale replicaset new-replica-set --replicas=5
```

**Now scale the ReplicaSet down to 2 PODs**

```bash
kubectl edit replicaset new-replica-set
```
