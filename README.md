# docker-env

## 简介
常用开发环境 docker 配置，线上环境请斟酌使用。

## 使用

1. 克隆项目  
```git clone git@github.com:One2r/docker-env.git```  

2. ```cd docker-env```

2. 编译镜像  
    - PHP 镜像  
    ```docker build --force-rm=true -f ./dockerfiles/php/7.4-dockerfile . -t php:my-7.4-fpm```
    - jupyterhub 镜像  
    ```docker build --force-rm=true -f ./dockerfiles/jupyterhub-dockerfile . -t jupyterhub:my-jupyterhub```
    - openresty waf 镜像   
    ```docker build --force-rm=true -f ./dockerfiles/gateway-dockerfile . -t openresty:gateway```
    - redis with plugin 镜像   
    ```docker build --force-rm=true -f ./dockerfiles/redis-dockerfile . -t redis:6-with-plugin```

3. 创建容器网络   
```docker network create --subnet=192.168.1.0/24 dev```   

4. ```cp .ENV.example .ENV```，编辑 ```.ENV```，修改数据目录和工作代码目录

5. 启动 lnmp compose  
```docker compose -f ./lnmp-docker-compose.yml up```

6. 启动 skywalking compose  
```docker compose -f ./skywalking-docker-compose.yml up```

7. 执行 php cli   
```
docker exec -it 97cfa2be2b0c /bin/bash 
cd /www/
php run
```

99. 其他 
- ELK 使用 ```git@github.com:deviantony/docker-elk.git``` 项目
