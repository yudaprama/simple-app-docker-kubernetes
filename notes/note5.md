# The example Pod YAML file

```
kubectl get nodes
kubectl create -f pod.yml
kubectl get pods
kubectl describe pods
```

# The example Replicaton Controller YAML file

```
kubectl get pods -o wide
kubectl get pods/hello-pod
kubectl get pods --all-namespaces
```

```
kubectl delete pods/hello-pod
```

```
kubectl create -f rc.yml
kubectl get rc -o wide
kubectl describe rc
kubectl apply -f rc.yml
```

```
kubectl get rc
kubectl get pods
```


## Sample Pod YAML file used in example (called pod.yml):

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: hello-pod
spec:
  containers:
  - name: hello-ctr
    image: yuda/docker-ci:latest
    ports:
    - containerPort: 8080
```
	
## Sample Replication Controller YAML file used in example (called rc.yml):

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: hello-rc
spec:
  replicas: 10
  selector:
    app: hello-world
  template:
    metadata:
      labels:
        app: hello-world
    spec:
      containers:
      - name: hello-ctr
        image: yuda/docker-ci:latest
        ports:
        - containerPort: 8080
```