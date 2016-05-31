# 集成SSH的Docker

## 目的

在服务器上运行一个支持SSH的Docker容器，便于开放给其他人使用，又不会污染服务器自身的文件系统。

## Dockerfile

Dockerfile内安装`openssh-server`。
创建默认用户`admin`，密码是`123456789`。
**登陆后请立即使用`passwd`修改为强密码。**

## Build Docker

`build_docker.sh`内容如下：

```
sudo docker build -t etworker/basic_image .
```

执行后生成`etworker/basic_image`的image。

## Run Docker

`run_docker.sh`内容如下：

```
sudo docker run -d --name basic -v $PWD:/work/ -p 8220:80 -p 8221:8221 -p 8222:22 -p 8223:443 -p 8224:8224 -p 8225:8225 etworker/basic_image
```

所以端口映射如下：

Docker容器暴露出6个端口，除了8022做ssh端口外，其他随意使用。

8220 - 80   (建议做web服务端口)
8221 - 8021
8222 - 22   (已用做ssh)
8223 - 443
8224 - 8024
8225 - 8025

举例来说，如果在docker内创建了一个service，端口是80，那么从外面访问的地址就是：<外部IP>:8020

