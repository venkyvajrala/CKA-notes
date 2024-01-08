

![[Pasted image 20221208194601.png]]


- deployments are higher in hirerchy than replicaset
- if we want to apply newer versions of docker images seamlessly
- if we want to roll the change to only particular pods
- if we have multiple changes like scale up, upgrade resources,etc you may want to apply each and pause so that all changes will be roled at same time
- if we want to roll back the changes if there is an issue
- if we want to update undrlying webserver version 


```bash
kubectl create -f deployment.yml
kubectl get deployments
kubectl apply -f dpeloyment.yml
kubectl set image deployment/my-deployment nginx=nginx:1.19.1
kubectl rollout status deployment/my-deployment 
kubectl rollout history deployment/my-deployment
kubectl rollout undo deployment/my-deployment
kubectl rollout undo deployment/app --to-revision=2
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: example-deployment
spec:
  replicas: 3
  revisionHistoryLimit: 100
  selector:
    matchLabels:
      name: app
  template:
    metadata:
      labels:
        name: app
    spec:
      containers:
      - name: app
        image: learnk8s/hello:1.0.0
```


whenever you make a change to image name or anything and when you apply that change,
deployment will create new replicaset and deletes one in older and creates one in newer until all are created. 
deployment is going to hold replicaset information,like all the replicasets created as a versions
if you have 1,2,3 as versions if you want to roll back to version 2 then
it will create new version 4 and version 2 entry will be removed
1,2,3 => 1,3,4
