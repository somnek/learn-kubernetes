# Q: what does minikube start does?
  - create 1 `K` cluster
  - create 1 `node` (can be multiple)
  - create multiple `pods` (see below)

# Q: difference between 1 & many node
  * pods created:
	  - node = 1: (7)
			+ coredns
			+ etcd
			+ api-server
			+ controller manager
			+ proxy
			+ scheduler
			+ storage
	  - node > 1:
			~ all the above
			+ proxy per node
			+ kindet per node
				(no kindnet if only 1 node)

