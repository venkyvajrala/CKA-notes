


#### **Node selector:**
We can have node filtering using labels. [[Kube scheduler]] will take this into consideration while selecting nodes
Limitations: It can have only `or` conditions and `not` conditions

```yaml
nodeSelector:
	size: large
```


#### node affinity

```yaml
affinity:
	nodeAffinity:
		requiredDuringSchedulingIgnoreDuringExecution:
			nodeSelectorTerms:
				- matchExpressions:
					- key: size
					  values: 
						- large
					   operator : In
```


```
affinity:
	nodeAffinity:
		requiredDuringSchedulingIgnoreDuringExecution:
			nodeSelectorTerms:
				- matchExpressions:
					- key: size
					  values: 
						- small
					   operator : NotIn
```

```
affinity:
	nodeAffinity:
		requiredDuringSchedulingIgnoreDuringExecution:
			nodeSelectorTerms:
				- matchExpressions:
					- key: size
					   operator : Exists
```


**supported affinities keys:**
requiredDuringSchedulingIgnoredDuringExecution
preferredDuringSchedulingIgnoredDuringExecution

**plan to bring new affinity:**
requiredDuringSchedulingrequiredDuringExecution