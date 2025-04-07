### 首次要求Kubernetes创建需要定义的对象
```
kubectl create -f deploy.yaml
```

### 如果需要刷新哪些对象
```
kubectl apply -f deploy.yaml
```

### 查看所有pods的信息
```
kubectl get pods
```

### 查看某个pod的详细信息
```
kubectl describe pod $POD_NAME
```

### 查看指定的pods(带上selector)
```
kubectl get pods --selector=pod=timeserver-pod
```

### 加上端口转发的功能
```
kubectl port-forward deploy/timeserver 8080:80
```
这样把本机的8080端口映射给pod的80

### 查看日志
```
kubectl logs -f deploy/timeserver
```

### 不准直接使用pod
在Kubernetes中直接使用Pod会导致以下问题：

1. 无自愈能力：Pod故障后不会自动重建
2. 无扩缩容：无法动态调整副本数量
3. 无滚动更新：无法实现零停机部署

Deployment通过ReplicaSet提供这些关键能力，是管理Pod的最佳实践。