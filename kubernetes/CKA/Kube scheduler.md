
- It's only job is to choose the perfect node for the resources to deploy
-
##### Manual scheduling 


ps -aux | grep kube-scheduler

there 2 ways to schedule pod to a node manaully
1. add nodeName: property to the pod defination

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx
spec:
  containers:
  - name: nginx
    image: nginx
  nodeName: kube-01
```

3. Use binding property while sending the api call to schedule the api to kube api server



### Multiple schedulers

custom scheduler can create and deploy as default schedulers

1. Create new scheduler configuration

```yaml
apiVersion:
kind: KubeSchedulerConfiguration
profiles:
	- schedulerName: my-scheduler2
```

2. Download scheduler binary 
3. while setuing scheduler pass above config yaml path

leader elect: true if we have multiple masters


- You can specify which scheduler to use for a pod in defination file
```yaml
spec:
	schedulerName: "custom-scheduler-name"
	containers:
```
- You can use events to check which scheduler scheduled a particular pod
```shell
kubectl get events -o wide to get who scheduled
```



#### scheduler profiles

scheduling queue
sorted by priority
Priority sort

scheduler performs different actions before scheduling a pod to node . 

1. It filter the nodes which will suffice the pod requirements and also based on node characteristics
2. After filtering it gives scoring to each node based on available resources(cpu,memory) , affinity, taints, image locality , etc
3. Node which get higher score will be selected and pod will be binded to the node

 **pre-filter -> filtering -> post-filter -> pre-score -> score -> post-score -> pre-bind -> bind -> post-bind**
  

```yaml
apiVersion:
kind: KubeSchedulerConfiguration
profiles:
	- schedulerName: name
	  plugins:
		  score:
			  disabled:
				- name: TaintToleration
			  enabled:
				- name: custompluginA
				- name: custompluginB

	- schedulerName: anotherName
	  preScore:
	  score:

```