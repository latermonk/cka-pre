
# PV - PVC - Vlome   


职责分工：

运维人员创建pv    
开发人员创建pvc    

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/pvc-definition.png)




========





    PVC 描述的，是 Pod 想要使用的持久化存储的属性，比如存储的大小、读写权限等。

    PV 描述的，则是一个具体的 Volume 的属性，比如 Volume 的类型、挂载目录、远程存储服务器地址等。

    而 StorageClass 的作用，则是充当 PV 的模板。并且，只有同属于一个 StorageClass 的 PV 和 PVC，才可以绑定在一起。


![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/pv-pvc-volume-explain.png)



