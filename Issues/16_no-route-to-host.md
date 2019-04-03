# k8s集群故障排错指南  

https://zhuanlan.zhihu.com/p/34722886  




###  发现以下问题

```
Error from server: Get https://10.254.21.3:10250/containerLogs/default/busybox/busybox: dial tcp 10.254.21.3:10250: connect: no route to host

```


### 思考

```
感觉上是云服务器上的有些端口的限制 ？ 


```


### daemon重启命令

```
systemctl daemon-reload
systemctl restart kubelet


```



### 组件状态查询命令

```
kubectl get componentstatus  

```


###  swap命令

```
cat /proc/swaps


swapoff -a 



```


####  排除故障   

##### 因为swap分区没有关闭 导致kubelet无法正常启动 




![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/issue1601-normal.png)
![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/issue1602-abnormal.png)
![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/issue1603-kubelet-not-start-dueto-swap.png)

<img src="https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/issue1603-kubelet-not-start-dueto-swap.png"  height="330" width="995">


### 参考：
https://kubernetes.io/docs/setup/independent/install-kubeadm/


http://www.bubuko.com/infodetail-2496107.html
