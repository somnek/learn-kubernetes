# vm vs container
* vm does `not` shares the same os/kernel/hardware
* container shares the same os/kernel/hardware

# Virtualization: 
* allows to run multiple VMs on single CPU
* core concept of kube: disposable virtual machines 
	- you should not save anything when container when its running
	- it wll be dispose

# Containers:
* share OS
* therefore the containers considered lightweight.
* best way to think of container is think of it as an Application
* its not a machine, its an app with set of tools

# Kubernetes:
* more like a Framework than a Application
* Main idea: ensure that theres no downtime,
	- if 1 down, another needs to start
	- at the end of the day, whole thing is just and api
* provides:
	- service discovery & load balancing:
		- expose container using DNS / IP
	- storage orchetration:
		- ! container doesn not have storage in it!	
		- never store anything there, mount instead
	- can automate Kubernetes to create new containers:
		- for deployment/remove existing containers & adopt their resources
		- to new container.
	- self-healing:
	    - restart containers that fail
	- secret & conf management:
		- by default it stores in base64, doesn not store secrets encrypted on disk.
	