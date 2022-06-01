# Components
* clusters: when deploy Kubernetes, you get a `cluster`.
* a kube cluster consists a set of worker machines, called `nodes`
  that run containerized applications.
* every cluster = has 1 worker node
* single node (minikube/kind)
* worker node(s) host `Pods` (components of the app workload)
* `control plane`:
	- manages worker nodes & Pods in cluster of nodes
	- REST API that listen on `6443`
	- its the 🧠 of the kubernetes
	- logical grouping of buncha services
	- receives requests from the workers, and checks on their health
* `Pods`: set of running containers in cluster

# Control Plane Components
* can be run on any node/machine in the cluster
* make decisions about cluster (e.g. scheduling)
	- scheduler schedules pod
* all control plane components must be running on Kube Node (a machine with `kubelet`, etc installed).

## kube-apiserver
* kubernetes control plane that exposes Kubernetest API.
* its HUGE, about 800+ apis
* `operator` is a way to extend the API

## etcd
* a distributed key-value store for all cluster data
* gotta learn separately

## kube-scheduler
* *THE* brain the maps the `nodes`
* not only a *cron-job*, its also a match maker, finds the best place
* control plane component: that watches for newly creatd `Pods` (those that aren't assigned yet) and assign them to nodes to run on.

## kube-controller-manager
* event loop that watch everything, it runs `controller` process.
* each `controller` is separate process
* types of `controller`:
	- `Node controller`: 
  	   * noticing & responding when nodes goes down.
	- `Job controller`: 
   	   * watching for Jobs object -> create Pods to run it.
	- `Endpoints controller`: 
       * populate endpoints object (joins Services & Pods)
	- `Service Account & Token controller`: 
       * create default account & API access tokens for new namespaces.
## cloud-controller manager (GKE)
* optional ~ 

---------------------

# Node Components
* runs on every node, maintain running `Pods` & provide Kube runtime env

## kubelet
- runs on each `Nodes`, make sure `containers` running in a `Pod`.
- take sets of PodSpecs, ensure all containeers are healths & running.

## kube-proxy
- kube-proxy is a network proxy that runs on each `node` in cluster, implemnting part of Kube `Service` concept.
- `Services`: something listening UDP/TCP inside clusters network or a way to expose application running on set of `Pods` as network service.
- network rules on `Nodes`, rules that allows communicate to your `Pods`, can think of firewall that surrounds your app.

## Container Runtime
* software that responsible for running `containers`

## Addons
* app that can added to kube-system namespaces.
	- only apply to the namespace that you provide.

## DNS
* DNS is a way to resolve domain names to IP addresses.
* all Kube clusters should have `cluster DNS`
* `cluster DNS`: DNS server + servers DNS records for Kube services.
* containers started by Kube automatically include this DNS server in DNS searches.
