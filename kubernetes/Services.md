

Kubernetes Services enable communication betwenn various components within and outside of network


![[Pasted image 20221210163727.png]]

The service in fact like a virtual server running on Node and it has it's own Ip called Cluster IP. we call the port running on it simply port.
***Nodeport:***
 It is going to listen for a particular port on node and forward those requests to particular port on pod . as the name suggests .
 like Deployment , Replicaset , Service is also a component which we can deploy on top of them.
 Service also going to run on a port . 
 Valid range: 3000 - 32767
 

```yaml
apiVersion: v1
kind: Service
metadata:
	name: app-service
spec:
	type: NodePort
	ports:
		- port: 8080
		  TargetPort: 8080
		  NodePort: 3888
	selector:
		app: webapp
```

only port is mandatory, targetport,nodeport are optional, if you don't give them target port will be same as port and nodeport will be randomly picked from valid range.

![[Pasted image 20221210165028.png]]
 It could be multi pod, multi node , anything service will target all of them. So, we don't have to make any additional config changes to access other nodes.
 It sends requests all the nodes , it uses random algorithm 


ClusterIP:
it enables communication internally between service like set of frontend servers to set of backend servers


LoadBalancer:
The third type is a LoadBalancer, were it provisions a load balancer for our service in supported cloud providers. A good example of that would be to distribute load across different web servers
![[Pasted image 20221210170156.png]]


frontend applications are accessing backend using clusterIP. we exposed frontend application to external users using NodePort but now users have multiple node ip's they can use to access frontend application. We can't tell them to use any one. In these case we can configure a loadbalance to round robbin this ip address and assign dns host for this load balancer like myapp.com so that users can use this name to accesss load balancer.
We don't have to do this manually on cloud platforms kubernetes automatically levarages cloud support loadbalancer and creates one for us.


```yaml
apiVersion: v1
kind: Service
metadata:
	name: app-service
spec:
	type: LoadBalancer
	ports:
		- port: 8080
		  TargetPort: 8080
	selector:
		app: webapp
		type: frontend
```



![[Pasted image 20221220113537.png]]