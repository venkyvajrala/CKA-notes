

 #### Entrypoint


```Dockerfile
FROM ubuntu:latest
ENTRYPOINT [“sleep”]
```

```shell
docker run ubuntu-sleeper 10 # sleep 10 append arguments
docker run ubuntu-sleeper # error as no arguments specified
```


#### command

```Dockerfile
FROM ubuntu:latest
COMMAND [“sleep”,”10”]
```

  
```shell
docker run ubuntu-sleeper 10 # 10 error
docker run ubuntu-sleeper sleep 100 # sleep 100 entire command replace
```


#### Both
```Dockerfile
FROM ubuntu:latest
COMMAND [”10”]
ENTRYPOINT [“sleep”]
```


```shell
docker run ubuntu-sleeper #sleep 10
docker run ubuntu-sleeper 50 # sleep 50 
docker run —entrypoint sleep2.0 ubuntu-sleeper 10 # sleep2.0 10
```

  
- entrypoint => command in [[kubernetes]]
- command => args in [[kubernetes]]

```yaml

kind:
apiVersion:
metadata:
spec:
containers:
	- image: ubuntu-sleeper
	  name: ubuntu-sleeper
	  command: [“sleeper2.0”]
	  args: [“10”]
```
