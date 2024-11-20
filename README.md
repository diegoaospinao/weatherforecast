# weatherforecast

## docker

### docker build

docker build -t weatherforecast-api .

### docker run

docker run -d -p 5000:8080 weatherforecast-api:latest

### docker publish to docker hub

docker login
docker tag weatherforecast-api:latest [your-dockerhub-username]/weatherforecast-api:latest
docker push [your-dockerhub-username]/weatherforecast-api:latest

## kubernetes

### crate aks cluster

az aks create --resource-group myResourceGroup --name myAKSCluster --node-count 1  --generate-ssh-keys
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster

### deploy cluster to aks

kubectl get nodes
kubectl apply -f deployment.yaml
kubectl get services