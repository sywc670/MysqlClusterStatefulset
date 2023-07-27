## 使用方法

在kind集群中
```shell
kubectl apply -f ./
```

使用rook插件
```shell
git clone --single-branch --branch v1.12.0 https://github.com/rook/rook.git
cd rook/deploy/examples
kubectl create -f crds.yaml -f common.yaml -f operator.yaml
kubectl create -f cluster.yaml
cd ../../..
# 修改使用的storageclass
kubectl apply -f ./
```

## 测试mysql集群是否正常运行

kubectl run mysql-client --image=mysql:5.7 -i --rm --restart=Never --\
  mysql -h mysql-0.mysql -uroot -e'
CREATE DATABASE test;
CREATE TABLE test.messages (message VARCHAR(250));
DESCRIBE test.messages;
'

## 参考

[深入理解StatefulSet](https://time.geekbang.org/column/article/41217)

[k8s运行mysql主从架构](https://www.cnblogs.com/wangguishe/p/17027398.html)

[MysqlCluster](https://github.com/Ivanqi/K8sClusterApplication/tree/main/MysqlCluster)