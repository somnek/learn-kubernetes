

# get secret
`kubectl` get secret {release-name} -o yaml | awk -F ': ' '/password/{print $2}' | base64 -d; echo`

# watch
`kubectl get pods -w`

# port forwarding
`kubectl port-forward --namespace {namespace} svc/{service} 5055:80` # 5055 is the local port, 80 is the remote port
# expose service (copilot wrote this)
`kubectl expose --namespace {namespace} svc/{service} --type=NodePort`
# logs pog
`kubectl logs -n {foo-namespace} {pod-name}`

# describe pod
`kubectl describe pod -n rasa-namespace foo`

# get namespaces / service 
* can pass `--all` to show all
`kubectl get namespace`
`kubectl get service`

# create namespace
`kubectl create namespace foo`

# stop
`minikube stop`

# ssh inside pod
`mk ssh`

# check resource of control plane components
`k get all -n ${kube-system}`

# show all pods
`kubectl get pods -A`

# rollout
* restart the whole thing (all pods get resets)
`kubectl rollout restart deploy foo`

# delete node (non-default nodes i.e not name == `minikube`)
`minikube delete -p ${foo}`

# delete pods
* note that self healing will occur (take times), regardless of how many pods is up
* you can `ctrl - c` to terminate, won't affect anything since the request
  is already sent to `kubeapi`, it waits only because if someone wants to write
  a scripts (which the waits will be helpful)
`kubectl delete pod foo-3fff2l234lh-sadfw`

# delete pods (deployment)
* intant (don't have to pass the whole pod name)
`kubectl delete deployments.apps foo`

# delete (multi)
* pods in single namespace
	kubectl delete --all pods --namespace=foo
* deployments (delete all pods attached with the deployments in namespace)
	kubectl delete --all deployments --namespace=foo
* all with namespaces
	kubectl delete --all namespaces

# kubectl new pods pods (fast way to spin up a pod)
* by providing any command `-- ` (e.g `sleep`), prevent crash backloop
`kubectl create deploy foo --image=ubuntu -- ${infinite command here}`
	or
* example of infinite command
-- sleep 100
-- tail -f /dev/null

# list all pods
`kubectl get pods A` / `kubectl get po -A`

# start minikube choose driver, (docker by default)
* without passing -p flag, it creates node with name `minikube`, 
  which when do `minikube delete` will be deleted automatically
* while nodes that created with -p flag can be deleted with `minikube delete -p ${foo}`
`minikube start --driver=virtualbox -p foo`

# start multiple node:
`minikube start --driver=virtualbox --nodes 2 -p foo`

#  to set default driver:
`minikube config set driver virtualbox`

# show profiles
`minikube profile list`

# delete a local kubernetes cluster
* it removes all assiciated files/vm
`minikube delete`

# get cluster infos
`kubectl cluster-info --context kind-single`

# get services
`kubectl get services`

# inspect to yaml
`kubectl get po -n {namespace} -o yaml > test.md`



## helm
-----------------
* list all releases
`helm list -A`

* list repos
`helm repo list`

## kind
-----------------
- stands for Kubernetes-in-Docker

* create (name & config is optional)
`kind create cluster --name {foo} --config {test.yaml}`

* delete cluster
`kind delete cluster --name {foo}`

* get all cluster
`kind get clusters`







## Commands Notes
------------------
# minikube vs kubectl
* `kubectl`: interaction with K through `API`
* access the kubernetes cluster `control plane` inside `minikube`
* also `minikube` comes with `kubectl`

* if pods with name followed by random alphanum, it is deployment
	e.g. coredns-74ffldkjl-iimxz



