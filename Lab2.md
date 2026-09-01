# Running your first Pod on Kubernetes


## Inline command to run a pod
```bash
kubectl run nginx --image=nginx
```
*This is equivalent to `docker run nginx`*

## Check pods

```bash
kubectl get pods
```

```bash
kubectl delete po nginx # Notice the shorthand
```

## Declarative manifest file

Create a file called `nginx-pod.yaml`
```yaml
# Put a file here
```

```bash
kubectl apply -f nginx-pod.yaml
```

## Verify

```bash
kubectl get pods
```

## Describe the pod

```bash
kubectl describe po nginx
```

## Get the logs for the pod

```bash
kubetl log po nginx
```

## Check for more pods

```bash
kubectl get pods -A # why -A?
```

