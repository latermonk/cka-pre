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


### 参考：
https://kubernetes.io/docs/setup/independent/install-kubeadm/


http://www.bubuko.com/infodetail-2496107.html
