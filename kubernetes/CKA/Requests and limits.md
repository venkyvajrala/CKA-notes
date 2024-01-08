

- used for limiting resources(cpu,memory) a pod can use on a node 
- container level
- when limit>requests for memory , if some pod needs memory then k8s will kick the pod which is using more than requested
- always prefer requests=limit for memory. follow this article for the reason: [What Everyone Should Know About Kubernetes Memory Limits, OOMKilled Pods, and Pizza Parties | Robusta](https://home.robusta.dev/blog/kubernetes-memory-limit)
- 1 cpu equivalent can be different in different cloud providers. Ex: AWS= 1vcpu , GCP = 1 GCP core

#### **Memory representation** 

- **M** (megabyte) = 1,000,000 bytes
- **Mi** (mebibyte) = 1,048,576 bytes (2^20 bytes)
- **G** (gigabyte) = 1,000,000,000 bytes
- **Gi** (gibibyte) = 1,073,741,824 bytes (2^30 bytes)

```yaml
resources:
  requests:
    memory: 512Mi  # Requests 512 mebibytes (536,870,912 bytes) of memory
  limits:
    memory: 1Gi    # Limits memory usage to 1 gibibyte (1,073,741,824 bytes)

```

#### CPU representation

 CPU requests and limits use millicores (m), which are fractions of a core (1000m = 1 full core).


#### Resource quotas
When several users or teams share a cluster with a fixed number of nodes, there is a concern that one team could use more than its fair share of resources.

Resource quotas are a tool for administrators to address this concern.
- resource quotas give for a namespace
```
apiVersion: v1
kind: ResourceQuota
spec:
	hard:
	requests.cpu:4
	requests.memory: 4Gi
	limits.cpu:
	limits.memory:
```



#### LimitRange

- pods that are created after or updated after this resource are impacted
- this works for limiting how much a single object can use within a namespace while [[Requests and limits#Resource quotas]] used for limiting an entire namespace

```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: cpu-resource-constraint
spec:
  limits:
  - default: # this section defines default limits
      cpu: 500m
    defaultRequest: # this section defines default requests
      cpu: 500m
    max: # max and min define the limit range
      cpu: "1"
    min:
      cpu: 100m
    type: Container
```



