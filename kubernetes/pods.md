

pod is an single instance of an application. a pod is a smallest objecy you can create on kubernetes
we don't spin up same application on same pod.

we can deploy helper containers inside a single pod whre an container is already running.
running in a pod makes it easy for us future scale up . 

kubectl run nginx --image nginx
kubectl get nodes
we can configure kubernetes to get this image from where we want 

kubectl get pods -o wide
kubectl describe pod podName
