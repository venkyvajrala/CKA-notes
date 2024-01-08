
Node - is machine which can be virtual or physical machine which is having kubernetes installation . it is a worker machine where applications are deployed . minions in the past called.
cluster - set of nodes - sharing load , failure cases handle
master - how the nodes monitored, how we know how many machines are ,etc. failed node to new node ,etc. master is another node installed kubernetes configured as master
![[Screenshot 2022-12-08 at 12.51.37 PM.png]]




Kubernetes components - when we say we installed ,it will install below components
![[Pasted image 20221208125535.png]]

api server - point of communication cli, api , etc
etcd - key value storage where it stores information about master,slaves,slots,etc
scheduler - responsible for adding new nodes created as to the cluster
controller - brain - responsible for creating new nodes whenever there is failure
container run time - docker ,etc
kubelet - agent runs on each node.making sure nodes are running as expected on cluster
