
# SVC  

svc的集中实现方式：    

## ClusterIP   

ClusterIP 主要用于集群内部的访问，当集群内部访问 service 的时候，可以通过 cluster : port 访问。
如果需要集群外部访问，需要用 kube-proxy 进行端口映射。    

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/cluster_ip_internal.png)

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/01_ClusterIP.png)



## NodePort   
这种方式很好理解， 就是在 每台宿主机上开放相应的端口，然后访问的时候，由主机转给相应的 service 

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/02_NodePort.png)


## Loadbalencer
云厂商相关，先把用一个负载均衡把流量发给主机，然后再转发到相应的 service

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/03_LoadBalancer.png)


##  Ingress     
![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/04_Ingress.png)
