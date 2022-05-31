# operator
* just an extension for apiserver

# how `kube-apiserver` route requests?
`kubeadm` deploys every controller as a pod in `kube-system` namespace
and the `kube-apiserver` simply routes requests to *registered* controllers/proviers/pods.
`kube-apiserver` seems to be responsible.

# ports
* 8080 for http
* 6443 for secure
- both can be change with flags (-h for help)

# kube-apiserver
- handle all api incoming request
- routes/map it for you

# etcd
- where all the data get stored (high performance `key-value` store, like redis)
- if this thing get fucked, in big trouble, it is always a good idea to do backup 
  as mentioned in doc, biggest case of db backup in history
