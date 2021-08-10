# Shiny App on Kubernetes Example

Example R Shiny app that has been dockerized and is run using Kubernetes. Useful for deployment of R Shiny apps on Kubernetes.

File uses dockerized shiny app that can be found here:

# Getting Kubernetees to run on WSL

- install docker desktop for windows with WSL enabled
- install minikube for windows
- start docker desktop
- in PowerShell in Admin mode:
    - set default driver for minikube to docker using ```minikube config set driver docker```
    - run ```minikube start```
- copy %USERPROFILE%\.kube\config from Windows to ~/.kube/config but change directory structure to WSL to point to Windows files. You may need to do this everytime you start up docker to update the IP:port.

# To get docker image from docker hub for kubernetes cluster

image: bbcho/example_shiny_app:0.2.0 # tag is required

# Running the App

## in WSL:

```
kubectl create -f deployment.yaml
kubectl create -f loadbalancer.yaml
```

## Then in PowerShell

```
minikube service shiny-loadbalancer
```

# Other Notes

## To get Kubernetes to pull from local docker registry

https://medium.com/swlh/how-to-run-locally-built-docker-images-in-kubernetes-b28fbc32cc1d

## Getting Node IP Address

```
kubectl get nodes -o yaml
```

## Connecting to Node

Use either the internal IP that you get from the ```kubectl get nodes -o yaml``` command or the url from ```minikube service shiny-loadbalancer --url``` via powershell.

# Reference

[1] https://blog.sellorm.com/2021/04/25/shiny-app-in-docker/ <br>
[2] https://hub.docker.com/r/rocker/shiny <br>
