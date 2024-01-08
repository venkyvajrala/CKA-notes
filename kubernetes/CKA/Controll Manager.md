
- Kubernetes Controller Manager is responsible for maintaining desired state of the cluster
- It continuously watches for changes in [[ETCD]] through [[Kube api server]] 
- It performs remediation actions by communication with [[Kube api server]] to bring to the desired state
- There are different controllers for different purposes 
- All the default controller come as a single package
- All the controllers are enabled by default
- You can check controller settings in manifests file `/etc/kubernetes/manifests`or through process arguments using below command
```bash
ps -aux | grep -i kube-controll-manager
```

##### Core controllers:

- Job Controller
- Replication Controller
- Persistent volume controller
- Namespace Controller
- Endpoint Controller
- Deployment Controller
- Cronjob Controller
- Node controller 
	- Responsible for managing nodes
	- Watches changes every 5 seconds
	- If any node is unhealthy 
		- Waits for 40s for it to become healthy again.
		- If the node still unhealthy after 40s then pods which are part of replication will be scheduled to different nodes



