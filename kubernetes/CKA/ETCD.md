
- ETCD is a key value storage for Kubernetes.
- It will store state data, metadata, configuration of Kubernetes cluster. 
- Default port = 2379
- [[Kube api server]] is the only component which directly communicates with ETCD  


#### Commands

ETCDCTL command line api  V3 is the latest one.

```bash
ETCDCTL_API=3 etcdctl version # Get version

ETCDCTL_API=3 etcdctl put key1 value1 # Add key value to store

ETCDCTL_API=3 etcdctl get key1 # get value of key

ETCDCTL_API=3 etcdctl snapshot save # create snapshot

ETCDCTL_API=3 etcdctl endpoint health # check endpoint health
```


If you want to directly execute command and get the output from etcd pod , you can use `exec` command as shown below

```bash
kubectl exec etcd-master \
  -n kube-system \
  -- sh -c "ETCDCTL_API=3 etcdctl version \
  --cacert=/etc/kubernetes/pki/etcd/ca.crt \
  --cert=/etc/kubernetes/pki/etcd/server.crt \
  --key=/etc/kubernetes/pki/etcd/server.key"
```


  
### Installation:

- Download binary 
- Provide Certificates details
- Give listener details : $ip: $port
- If you have multiple etcdctl pods across nodes specify them using `intial_cluster_controller`

