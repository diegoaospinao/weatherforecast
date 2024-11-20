# weatherforecast

## docker

### docker build

docker build -t weatherforecast-api .

### docker run

docker run -d -p 5000:8080 weatherforecast-api:latest

### docker publish

docker login
docker tag weatherforecast-api:latest [your-dockerhub-username]/weatherforecast-api:latest
docker push [your-dockerhub-username]/weatherforecast-api:latest

## kubernetes
