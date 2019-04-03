# storage


![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/s01.png)
![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/s02.png)
![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/s03.png)


## emptyDir

### 创建带emptyDir的Pod

edir.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: test-pd
spec:
  containers:
  - image: redis
    name: test-container
    volumeMounts:
    - mountPath: /cache
      name: cache-volume
  volumes:
  - name: cache-volume
    emptyDir: {}
```


```
k apply -f edir.yaml

```


```
k describe po test-pd 
```

```
 k exec -it test-pd -- /bin/sh 
```


 
 



# 1

# 2

# 3

# 参考
http://newto.me/k8s-storage-architecture/
