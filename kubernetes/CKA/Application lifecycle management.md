

#### Deployment status

You can check deployment status with 
```shell
k rollout status deployment/name
```

You can check previous deployment history with below command

```
k rollout history deployname
```


### Deployment strategies

**Recrete**
- Destroys all pods and create all new with new replicaset
- This will cause downtime while deployment as we are destroying all the pods first

**RollingUpdate**

- This will create new [[ReplicaSets]] first and adds each pod in new set and removes from existing
- create new replicaset and migrate

  
##### Undo Deployment

- Destroy new [[ReplicaSets]] and brings back  older [[ReplicaSets]]

```shell
k rollout undo deployment
```


