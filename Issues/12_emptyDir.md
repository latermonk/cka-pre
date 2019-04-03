# kubernetes-in-action 中的一个 emptyDir 的例子   


![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/combine-emptyDir.png)


## 1
![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/emptyDir.png)

## 2
![](https://raw.githubusercontent.com/latermonk/cka-pre/master/Issues/images/empty-pic.png)

## 3

#### fortune-pod.yaml

```
# fortune-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  name: fortune
spec:
  containers:
  - image: luksa/fortune
    name: html-generator
    volumeMounts:
    - name: html
      mountPath: /var/htdocs
  - image: nginx:alpine
    name: web-server
    volumeMounts:
    - name: html
      mountPath: /usr/share/nginx/html
      readOnly: true
    ports:
    - containerPort: 80
      protocol: TCP
  volumes:
  - name: html
    emptyDir: {}


```

# 1. 创建Pod
```
kubectl apply -f  fortune-pod.yaml
```


# 2. 打开端口转发
```
kubectl port-forward fortune 8080:80
```

# 3. 访问
```
curl http://127.0.0.1:8080
```

