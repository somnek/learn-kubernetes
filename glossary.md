# service
* load balance request to one of selected pods, refer to link below for diagram
refer to : [https://www.youtube.com/watch?v=NPFbYpb0I7w](Kubernetes Ingress in 5 min)


## `container runtime`:
- software that responsible for running `containers`.

## `Deployment:
- tool that mages the perfomance and specifies desired behaviour of a `pod`.
- use to communicate what we want from an app. `Kube` then create the desired `state` of the app.

## `Cluster`:
- bunch of `Nodes` run `container`ized apps. More lightweigh than vm.

## `Node`: 
- name of the machine running kube worker software
- kubelet + k-proxy + container runtime

## `Container`: 
- lightweight & portable exe image contains software & dependencies

## `Pod`: 
- the thing that run, the one that rebooted, set of running `containers`
- the smallest unit

## `Kubelet`: 
- runs on every node, make sure `containers`s are running in `Pods`

## `Operator`:
- extends the existing `Kube API` (like *HELM*)

## `kube-proxy`:
- microservice that represents node on the machine


## state:
- ???

