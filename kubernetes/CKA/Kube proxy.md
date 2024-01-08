
- It enables pod networking across nodes

- Always use services whenever possible as ip's will change when pod is recreated
- It creates rules in node iptables to enable communication
- [[Services]] are not [[pods]] or containers . They are just virtual resources
- When you create service you are just creating some rules in node routing 
- This node routings are updated by [[Kube proxy]] 
- It is deployed as [[Daemonset]] - means every node will have a one kube-proxy pod

service_name.namespace.svc.local