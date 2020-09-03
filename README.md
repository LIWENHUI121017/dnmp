用的别人配置好的docker修改了一些自己需要的

具体参考：

https://github.com/duiying/Docker-LNMP

运行命令：

```shell
$ docker-compose up -d
```

进入cgi容器，也就是放php的容器

```shell
$ docker exec -it cgi bash	
```

切换到gcc 7版本scl enable devtoolset-7，在dockerfile构建镜像的时候已经安装好gcc 7版本了

详情可以查看  /docker/files/cgi/Dockerfile

```shell
$ scl enable devtoolset-7 bash
```

运行安装是swoole的命令，装的是最新的

```shell
$ wget https://github.com/swoole/swoole-src/archive/master.tar.gz &&\
	tar -zxvf master.tar.gz &&\
	cd swoole-src-master &&\
	phpize &&\
	./configure &&\
	make && make install &&\
	sed -i '$a \\n[swoole]\nextension=swoole.so' /etc/php.ini &&\
cd ../ && rm -rf master.tar.gz swoole-src-master
```

查看swoole是否已经安装好了(查看是否有swoole)

```shell
$ php -m

[PHP Modules]
...
SPL
sqlite3
standard
swoole
...
Zend OPcache
zip
zlib

[Zend Modules]
Zend OPcache
```

