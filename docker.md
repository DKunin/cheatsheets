# Docker

## Docker deamon

```
eval $(minikube docker-env)
```

## Run image

```console
    docker run --name hello_world ubuntu echo "Hello, world\!"
```

## List images
```console
    docker images | grep -v gcr
```

## Show logs for image
```console
    docker logs %containerid
```

## Show docker containers
```console
    docker ps -a|grep -v gcr
```

## Remove docker container
```console
    docker rm (name|id)
```

## Dockerfile
```
    FROM ubuntu
    RUN echo "Hello world!"
```

## Docker build image from file
```console
    docker build -t (NAME) ./
```

## Connect to container
```console
    docker exec -i -t 665b4a1e17b6 /bin/bash
```

## Docker remove image
```console
    docker rm -i (NAME)
```


## Docker interactive mode

```console
    docker run --rm -it ubuntu
    ---
          --rm                          Automatically remove the container when it exits
      -i, --interactive                 Keep STDIN open even if not attached
      -t, --tty                         Allocate a pseudo-TTY

```

## Docker interactive mode

```console
    docker exec -it (name) /bin/bash
    docker exec -it prickly_saha /bin/bash


```
## Port forward

```console
    docker run --rm -p 8888:80(local:remote) nginx
    minikube ip
```

### Adding volume from local system

```console
    docker run --rm -v $(pwd):/usr/share/nginx/html -p 8888:80 nginx
```
## Copy file inside
```console
    docker cp index.html {container}:/usr/share/nginx/html/index.html
```

## Copy folder in dockerfile

```
FROM nginx
COPY . /usr/share/nginx/html
```

## Ignore files 

.dokerignore

## Adding tag and pushing

```
    docker tag nginx-custom nginx-custom:dkunin
    docker tag nginx-custom registry.msk.avito.ru:5000/nginx-custom:dkunin
    docker push registry.msk.avito.ru:5000/nginx-custom:dkunin
```

## Saving and sharing images

```
    docker save -o myimg.tar myimg:latest
    docker load -i myimg.tar
```

# Kubernetes

```console
    kubectl get pod --all-namespaces -o wide
    kubectl get pod -n default -o wide
    kubectl get pod -n kube-system -o wide
```

## Get pod yaml

```
    kubectl get pod -n kube-system -o yaml kube-dns-v20-
```


## Create pod

```
    kubectl create/apply -f pod.yaml
```

## Forward port

```
    kubectl port-forward hello-world 8888:80
    kubectl port-forward hello-world (local):(remote)
    // localhost
```

## Get logs 

```
kubectl logs hello-world
```
## Deployment file
```
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: hello-world-deployment
spec:
  selector:
    matchLabels:
      app: hello-world-server
  template:
    metadata:
      labels:
        app: hello-world-server
    spec:
      containers:
      - name: frontend
        image: nginx
```

## Scale deployment

```
    kubectl scale deployment --replicas 3 hello-world-deployment
```

## Service details

```
kubectl describe service hello-world-service
kubectl get -o yaml service hello-world-service
```


## Interesting links

- [Docker for devs](https://lockmedown.com/docker-4-devs-containerizing-app/)
- [Docker on Pi](https://www.raspberrypi.org/blog/docker-comes-to-raspberry-pi/)
- [Docker for ubuntu](https://docs.docker.com/engine/installation/linux/ubuntu/)
- [Docker with env variables](http://stackoverflow.com/questions/30494050/how-to-pass-environment-variables-to-docker-containers)
- [Docker save image to file](https://docs.docker.com/engine/reference/commandline/save/)
- [Docker load image from file](https://docs.docker.com/engine/reference/commandline/load/)
