
# emptyVolume 
Create busybox pod with two containers, each one will have the image busybox and will run the 'sleep 3600' command.     
Make both containers mount an emptyDir at '/etc/foo'.    

Connect to the second busybox, write the first column of '/etc/passwd' file to '/etc/foo/passwd'.    
Connect to the first busybox and write '/etc/foo/passwd' file to standard output.     
Delete pod.   


```

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: busybox
  name: busybox
spec:
  dnsPolicy: ClusterFirst
  restartPolicy: Never
  containers:
  - args:
    - /bin/sh
    - -c
    - sleep 3600
    image: busybox
    imagePullPolicy: IfNotPresent
    name: busybox
    resources: {}
    volumeMounts: 
    - name : myvolume
      mountPath: /etc/foo
  - args:
    - /bin/sh
    - -c
    - sleep 3600
    image: busybox
    name: busybox2
    resources: {}
    volumeMounts:
    - name : myvolume
      mountPath: /etc/foo
  volumes:
  - name: myvolume
    emptyDir: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Never
  
  ```
  
  
