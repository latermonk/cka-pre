
# pv pvc 

## 用户创建的 PVC 要真正被容器使用起来，就必须先和某个符合条件的 PV 进行绑定。      
##  这里要检查的条件，包括两部分：     

### 第一个条件，当然是 PV 和 PVC 的 spec 字段。比如，PV 的存储（storage）大小，就必须满足 PVC 的要求。
### 第二个条件，则是 PV 和 PVC 的 storageClassName 字段必须一样。这个机制我会在本篇文章的最后一部分专门介绍。


![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/pv-pvc-condition.png)

### 定义了之后就可以使用了

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/pv-pvc-pod.png)

### storage-Class
![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/storage-class.png)

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/storage-class-2.png)




