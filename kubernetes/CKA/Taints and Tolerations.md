
[[Kube scheduler]] considers [[Taints and Tolerations]] while selecting nodes

#### Taints:
**Taint** is similar to applying some restriction to nodes so that only pods which can tolerate will be able to run.
ex: Taint=blue to node


```shell
kubectl taint node node_name key=value:taint-effect
```

**taint-effect** = This tells what happens to pod that  doesn't have toleration

- NoSchedule = new pods will not be scheduled
- PreferNoSchedule = not prefers but there is no other way(no other nodes are available) will schedule
- NoExecute=new pods can’t and existing will be evicted

Ex: Adding Taint

```shell
kubectl taint node node01 app=blue:NoSchedule
```



#### Tolerations :  
- Having toleration to taints assigned to nodes
- this doesn’t tell where the pod should go 
- master: by default have taint NoSchedule

Ex: Toleration
```yaml
spec:
containers:
tolerations:
	- key: "app"
	  operator: "Equal"
	  value: "blue"
	  effect: "NoSchedule"
```


#### Untaint: 
Observe the `-` at the end. 

```
k taint node node01 spray=mortein:NoSchedule-
```


