
labels are like filters price, location,etc

we can filter pods using labels as below
```shell
k get pods —selector=env=prod —selector=app=db —selector
```

annotations are information holders: informative contacts , build version,etc

