## 云尚发卡

专门为个人或小型企业提供在线售卡，订单处理系统。

## RUN

```
wget https://raw.githubusercontent.com/Baiyuetribe/ysfaka/master/docker-compose.yml
docker-compose up -d
```

运行结束后，访问域名或者ip即可进入。默认root密码`Passw0rd` .

![Snipas9](https://ws3.sinaimg.cn/large/007rd8E4ly1g1uiag7w1pj30mo0fj403.jpg)

## 运行示例：

```yaml
version: '2'
services:
    nginx:
        image: "baiyuetribe/ysfaka:nginx"
        ports:
            - "80:80"
        networks:
            - frontend
        depends_on:
            - php
    php:
        image: "baiyuetribe/ysfaka:php"
        networks:
            - frontend
            - backend
        depends_on:
            - mysql
    mysql:
        image: mysql:5.7
        volumes:
            - mysql-data:/var/lib/mysql
        environment:
            TZ: 'Asia/Shanghai'
            MYSQL_ROOT_PASSWORD: Passw0rd
        command: ['mysqld', '--character-set-server=utf8']
        networks:
            - backend
volumes:
    mysql-data:

networks:
    frontend:
    backend:
```

[![Try in PWD](https://github.com/play-with-docker/stacks/raw/cff22438cb4195ace27f9b15784bbb497047afa7/assets/images/button.png)](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/Baiyuetribe/ysfaka/master/docker-compose.yml)

运行结束后，访问域名或者ip即可进入。默认root密码`Passw0rd` .

## 其他说明

#### 停止运行

```
docker-composer down
```


### demo地址：[http://fk.phpke.cn](http://fk.phpke.cn)
原作地址：https://github.com/assimon/ysfaka
