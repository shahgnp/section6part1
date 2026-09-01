# Creating a deployment

## Create a deployment
```bash
kubectl create deployment nginx \
  --image=nginx:alpine \
  --replicas=3
```

## Verify

```bash
kubectl get deployment
kubectl get pods
```

## Scale the deployment

```bash
kubectl scale deployment nginx --replicas=5
```

## Clean up previous resources

```bash
kubectl delete deploy nginx # Notice the shorthand
```

## Do it again using declarative manifest file

Create a file with name `nginx-deployment.yaml`
```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
        - name: nginx
          image: nginx:alpine
          ports:
            - containerPort: 80
```

```bash
kubectl apply -f nginx-deployment.yaml
```
## Testing the deployment

1. List the pods
```bash
kubectl get pods
```

2. Delete a random pod
```bash
kubectl delete po <pod-name>
```

3. Check the pods again
```bash
kubectl get pods
```
## Let's update the deployment

update the previos deployment manifest `nginx-deployment.yaml`
```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
        - name: nginx
          image: nginx:1.28
          ports:
            - containerPort: 80
```

```bash
kubectl apply -f nginx-deployment.yaml
```

## Do it again

update the previos deployment manifest `nginx-deployment.yaml`
```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
        - name: nginx
          image: nginx:1.29
          ports:
            - containerPort: 80
```

```bash
kubectl apply -f nginx-deployment.yaml
```

## Deployment version

1. Checking the Deployment history
```bash
kubectl rollout history deployment/nginx
```

2. Checking the past version of deployment
```bash
kubectl rollout history deployment/nginx --revision=2
```
3. Checking the rollou status of deployment
```bash
kubectl rollout status deployment/nginx
```
4. Going back to the previous version
```bash
kubectl rollout undo deployment/nginx
```
5. Go back to a specific version
```bash
kubectl rollout undo deployment/nginx --to-revision=1
```
6. Checking the status of the deployment
```bash
kubectl rollout status deployment/nginx
kubectl get pods
```

## Check for more resources

```bash
kubectl get all -A
```