# 300 - Creating the Cluster

## 100 - Creating the Cluster on Windows

To Do

## 200 - Creating the Cluster On Mac

The Minikube tool supports multiple versions of Kubernetes. At the time of writing, the latest version is 1.26.1, which is also the default:

```
$ minikube start
  minikube v1.26.1 on darwin 12.0 (amd64)
  Automatically selected the docker driver. Other choices: hyperkit,parallels, virtualbox, ssh, qemu2 (experimental)
  Using Docker Desktop driver with root privileges
  Starting control plane node minikube in cluster minikube
  Pulling base image ...
  Downloading Kubernetes v1.24.3 preload ...
  > preload-images-k8s-v18-v1...: 405.75 MiB / 405.75 MiB 100% 5.58 Mi
  > gcr.io/k8s-minikube/kicbase: 386.61 MiB / 386.61 MiB 100.00% 4.39 MiB p
  > gcr.io/k8s-minikube/kicbase: 0B [_________________________] ?% ? p/s 2m14s
  Creating docker container (CPUs=2, Memory=1986MB) ...
  Preparing Kubernetes v1.24.3 on Docker 20.10.17 ...
  - Generating certificates and keys ...
  - Booting up control plane ...
  - Configuring RBAC rules ...
  Verifying Kubernetes components ...
  Executing "docker container inspect minikube --format={{.State.Status}}" took an unusually long time: 2.33797457s
  Restarting the docker service may improve performance
  - Using image gcr.io/k8s-minikube/storage-provisioner:v5
  Enabled addons: default-storageclass, storage-provisioner
  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
```

Ooops, for using minikube with hyperkit (instead of docker, which is the default) we need to add a flag to the start command.

```
$ minikube stop
```
Now using the flag to create a minikube cluster using ```hyperkit``` vm driver

```
$ minikube start --vm-driver=hyperkit




```
