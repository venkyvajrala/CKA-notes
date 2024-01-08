

- kubelet contains cAdvisor responsible for collecting, processing, and exporting container-related metrics which can be used in metric server
- Download deployment files of [metric](https://github.com/kubernetes-sigs/metrics-server) server and deploy

`k top node` , `k top pod` - will only work once metric server is deployed in cluster

We can export these metrics to external monitoring solutions like Datadog, new relic, Prometheus 


#### Logs:

```shell
k logs -f pod_name # to check pod logs in live
k logs -f pod_name  container_name # if multiple containers are in pod specicify container name
```

