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

## Check for more resources

```bash
kubectl get all -A
```