# 安装

## centos 和 docker 安装

可参考: [centos 笔记](https://laolang2016.github.io/2024/09/15/centos-note/)


## nginx 的四个版本

Nginx开源版（官方免费开源版本）
[http://nginx.org/](http://nginx.org/)

Nginx plus 商业版（付费版，在上版本基础上加了一些功能）
[https://www.nginx.com](https://www.nginx.com)

openresty（nginx+lua完美整合）
[http://openresty.org/cn/](http://openresty.org/cn/)

Tengine（淘宝网公布发行版本，免费开源）
[http://tengine.taobao.org](http://tengine.taobao.org)




## linux 

### docker 安装

#### 步骤

**创建目录**

```
[root@localhost docker]# tree
.
├── conf
├── html
└── log

3 directories, 0 files
[root@localhost docker]# 
```

**启动一个临时 nginx 容器**
```
docker run --name nginx -p 10002:80 -d nginx
```

**复制配置文件**
```
docker cp nginx:/etc/nginx/nginx.conf ~/program/docker/nginx/conf/nginx.conf
docker cp nginx:/etc/nginx/conf.d ~/program/docker/nginx/conf/conf.d
docker cp nginx:/usr/share/nginx/html ~/program/docker/nginx/

[root@localhost nginx]# tree
.
├── conf
│   ├── conf.d
│   │   └── default.conf
│   └── nginx.conf
├── html
│   ├── 50x.html
│   └── index.html
└── log

4 directories, 4 files
[root@localhost nginx]# 
```

**删除此临时 nginx 容器**
```
docker stop nginx
docker rm nginx
```

**重新创建 nginx 容器**
```
docker run \
-p 80:80 \
--name nginx \
-v /root/program/docker/nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
-v /root/program/docker/nginx/conf/conf.d:/etc/nginx/conf.d \
-v /root/program/docker/nginx/log:/var/log/nginx \
-v /root/program/docker/nginx/html:/usr/share/nginx/html \
-d nginx:1.26.2
```

**在宿主机访问**

![](img/z03/001.png)

#### 参考
[Docker 安装 Nginx 容器 (完整详细版)](https://blog.csdn.net/BThinker/article/details/123507820)

### 宝塔 Linux 安装

- [ ] 待完成

### 源码安装

- [ ] 待完成

## windows 安装 

- [ ] 待完成


