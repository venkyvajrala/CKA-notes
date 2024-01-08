
replication controlle is older , replicasets is new one

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
	name: myapp-rc
	labels:
	app: myapp
	type: front-end
spec:
	template:
		metadata:
			name: myapp=pod
			labels:
				app: myapp
				type: front-end
		spec:
			containers:
				- name: nginx-container
				- image: nginx
	replicas: 3
		
```



replication controlle is older , replicasets is new one

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
	name: myapp-replicaset
	labels:
	app: myapp
	type: front-end
spec:
	template:
		metadata:
			name: myapp=pod
			labels:
				app: myapp
				type: front-end
		spec:
			containers:
				- name: nginx-container
				- image: nginx
	replicas: 3
	selector: 
		matchLabels:
			type: front-end
		
```

different = apiVersion, kind,selector
replicaset can manage pods which are created without replicaset using selector
if replicas 3 are already created then it wont create new one as it is the desired state
if anyone fails it uses template section config to create new one

if we want update replica :
1. update yml file
	kubectl replace -f replicaset-defination.yml
2. kubectl scale --replicas=6 -f replicaset-defination.yml
3. kubectl scale --replicas=6 replicaset myreplicaset
if you dont update file , even though you used 2,3 approaches it wont update the file

kubectl create -f filename.yml
kubectl get replicaset
kubectl delete replicaset name
