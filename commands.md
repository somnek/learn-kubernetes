# rollout
* restart the whole thing (all pods get resets)
`kubectl rollout restart deploy foo`

# delete pods
* note that self healing will occur (take times), regardless of how many pods is up
* you can `ctrl - c` to terminate, won't affect anything since the request
  is already sent to `kubeapi`, it waits only because if someone wants to write
  a scripts (which the waits will be helpful)
`kubectl delete pod foo-3fff2l234lh-sadfw`

# delete pods (deployment)
* intant (don't have to pass the whole pod name)
`kubectl delete deployments.apps foo`

# kubectl new pods pods (fast way to spin up a pod)
* by providing any command `-- ` (e.g `sleep`), prevent crash backloop
`kubectl create deploy foo --image ubuntu -- sleep 100`

# list all pods
`kubectl get pods`

# start minikube choose driver, (docker by default)
`minikube start --driver=virtualbox`

#  to set default driver:
`minikube config set driver virtualbox`

# show profiles
`minikube profile list`

# delete a local kubernetes cluster
* it removes all assiciated files/vm
`minikube delete`


## Commands Notes
------------------
# minikube vs kubectl
* `kubectl` used to access the kubernetes cluster `control plane` inside `minikube`
* also `minikube` comes with `kubectl`

