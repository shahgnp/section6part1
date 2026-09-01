# Setting up your first Kubernetes cluster


## Installing k3d on WSL

```bash
curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```

## Creating your first cluster

```bash
k3d cluster create dev-cluster   --agents 2   -p "30000-30010:30000-30010@server:0"
```

## Check the k3d

```bash
docker ps
```

## Install Kubectl

```bash
sudo snap install kubectl --classic
```

## Check your cluster

```bash
kubectl get nodes
```
