#### Deploy
```
kubectl delete rc hello-rc
kubectl get pods

kubectl describe svc hello-svc

vim deploy.yml

kubectl create deployment

kubectl describe deploy hello-deploy

kubectl get rs

kubectl describe rs 
```

#### Deploy

```
kubectl apply -f deploy.yml --record

kubectl rollout status deployments hello-deploy

kubectl get deploy hello-deploy

kubectl rollout history deployments hello-deploy

kubectl get rs

kubectl describe deploy hello-deploy

kubectl rollout undo deployment hello-deploy --to-revision=1

kubectl get deploy

kubectl rollout status deployments hello-deploy
```

# Final deployment YAML file used

```yaml
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: hello-deploy
spec:
  replicas: 10
  minReadySeconds: 10
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 1
      maxSurge: 1
  template:
    metadata:
      labels:
        app: hello-world
    spec:
      containers:
      - name: hello-pod
        image: yuda/docker-ci:latest
        ports:
        - containerPort: 8080
```
