## 拷贝sql

```bash
docker cp mydata_mytable.sql mysql:/mydata_mytable.sql
```

将sql文件拷贝到docker容器中。

## 登录容器

```bash
docker exec -it mysql bash
```

登录docker容器查看，sql文件是否成功考入了容器。

## 导入sql

到这里一步，就是mysql的正常导入使用了。

```bash
$ mysql -u root -p  -D mydatabase 
$ source mydata_mytable.sql
```