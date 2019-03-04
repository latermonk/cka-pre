
## 问题

```
跑命令  kubectl rollout history deploy  xxx 的时候，如果版本多的话总是貌似只能看见3条历史，看不见上边几条，请问可以通过设置什么参数来显示么？   

```

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/no-history-record.png)

## 群里讨论：


```
1.
kubectl rollout history deployment --revision=版本号  即可

2.
因为你deployment的historylimit设置的就是3，只保留3条历史记录
revisionHistoryLimit 是这个作用
a.部署的时候在yaml文件里边写 



b.事后修改的话 
kubectl patch deploy nginx -p '{"spec":{"revisionHistoryLimit":100}}'


3.
看代码应该是全部返回的，replicas为0的话也会返回：
https://github.com/kubernetes/kubernetes/blob/master/pkg/kubectl/history.go#L112，是不是只剩下这几个了


```

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/revisionHistoryLimit_yaml.png)



## 接下来自己尝试，但是发现：   

有些record不见了是因为使用了 deployment undo命令    

![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/deployment_undo.png)


```
是的，undo是回滚，会将回滚的版本更新为当着版本号，并删除之前的历史记录

```


##  追问：  

追问：  
如果这条记录没有了 我uodo的时候还能跳回到这个版本么？   


```

回答：
不行，强制 --revision= x 的话，会报错： 

revision not found 

```

追问：
rollout pause ，pause掉的到底是什么？ 这个一般都用在什么场景？   

那如果我在 pause 和 resume 之间做了多次set image 的话，resume之后会一步一步执行中间的操作么？ 还是只执行 resume之前的或者是resume之后的操作。    

这个pause可以理解为 冻结了 deployment的操作了么？


```
pause掉的是滚动更新和回滚这个过程   
是的 直接执行resume之后的  
对的 以pod为粒度的暂停  
多次set image后就已经把预期的yaml模板改了  


```


