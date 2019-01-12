# cka-label



## 标签的增删改查

###  pod标签查询：

```
kubectl get pods --show-labels

```

### 建立pod的时候直接加标签:

####  创建pod的时候直接把label写在yaml配置文件中


```
kubectl create -f kubia-manual-with-labels.yaml
```

####  创建pod的时候直接在命令中加上label标签

```
kubectl run alpaca-prod \ 
--image=gcr.io/kuar-demo/kuard-amd64:1 \ 
--replicas=2 \ 
--labels="ver=1,app=alpaca,env=prod"
```

### 增加一个标签：
```
kubectl label pods bar color=red

```

### 一次增加多个标签


```
kubectl label pods nginx-57867cc648-28cfc  label1=value1 label2=value2

```


###  修改label

```
kubectl label pods kubia-manual-v2 env=debug --overwrite
```


### 删除一个标签：



## 依据标签进行调度，删除等操作

### 使用label进行选择

```
kubectl get pods --selector="ver=2"
```

```
kubectl get pods -l environment=production,tier=frontend
```

```
kubectl get pods -L creation_method,env
```



```
kubectl delete pods,services -l name=myLabel
```



#  Reference

```
https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/


https://kubernetes.io/docs/concepts/cluster-administration/manage-deployment/
```



