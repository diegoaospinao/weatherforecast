# weather forecast

## docker

### docker build

```sh
docker build -t weatherforecast-api .
```

### docker run

```sh
docker run -d -p 5000:8080 weatherforecast-api:latest
```

### docker publish to docker hub

```sh
docker login
docker tag weatherforecast-api:latest [your-dockerhub-username]/weatherforecast-api:latest
docker push [your-dockerhub-username]/weatherforecast-api:latest
```

## kubernetes

### create aks cluster

```sh
az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 1  --generate-ssh-keys
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
```

### deploy cluster to aks (using deployment)

```sh
kubectl get nodes
kubectl apply -f deployment.yaml
kubectl get services
```

## helm

### create aks cluster

```sh
az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 1  --generate-ssh-keys
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster
```

### deploy cluster to aks (using helm from local)

```sh
kubectl get nodes
helm create weatherforecast-api
helm install weatherforecast-api weatherforecast-api/
kubectl get services
```

### deploy cluster to aks (using helm from registry)

#### push chart to registry

```sh
helm package .
helm registry login [container-registry] --username [user-name] --password [password]
helm push weatherforecast-api-0.1.0.tgz oci://[container-registry]/helm
az acr repository list --name [container-registry]
```

#### install chart from registry

```sh
kubectl get nodes
helm install myhelmtest oci://[container-registry]/helm/weatherforecast-api --version 0.1.0
kubectl get services
```