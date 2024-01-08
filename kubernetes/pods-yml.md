


we can look what pods are here [[pods]]

| resource   | api     |
| ---------- | ------- |
| Service    | v1      |
| ReplicaSet | apps/v1 |
| Deployment | apps/v1 |
| Pod        | v1      | 

metadata accepts = name , labels only
labels can have any number of labels


```yaml
apiVersion:
kind:
metadata:

spec:
```

```yaml
apiVersion: v1
kind: Pod
metadata:
	name: myapp-pod
	labels:
		app: myapp
		type: front-end
spec:
	containers:
	  - name: nginx-container
	    image: nginx

```

kubectl get pods -o wide

kubectl run redis --image=redis123 --dry-run=client -o yml > redis.yml