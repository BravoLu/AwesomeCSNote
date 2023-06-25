# Kubernetes

![image-20230403163414239](C:\Users\bravolu\AppData\Roaming\Typora\typora-user-images\image-20230403163414239.png)

## Control Plane Components

### kube-apiserver

* exposes the Kubernetes API.
* scale horizontally by deploying more instances.

### kube-scheduler

### kube-controller-manager

### cloud-controller-manager

## Node Components

Node components run on every node, maintaining running pods and providing the Kubernetes runtime environment.

### kubelet

### kube-proxy

for network.

### Addons

### DNS

## Nodes

* virtual or physical machine
* run the pod.
* managed by control plane.
* composed of three parts: 1. kubelet 2. container runtime 3. kube-proxy

### status

1. Addresses
   * HostName
   * ExternalIP/InternalIP
2. Conditions
   * describes the status of all Running.
3. Capacity and Allocatable
4. Info

## Reference 

1. https://kubernetes.io/docs/home/