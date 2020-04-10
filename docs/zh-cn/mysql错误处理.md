# MySQL错误处理
---
## 一、表崩溃
![image.png](https://i.loli.net/2020/04/10/S1RhJQqXkOgVeu2.png)
## 解决方法：
```shell
myisamchk --safe-recover /data/mysql/mysql/user.MYI
```

- 后面的路径就是数据库安装时的路径，表在宿主机的绝对路径
![image.png](https://i.loli.net/2020/04/10/ROJN4U5K1eiFCGI.png)
- 然后进入数据库
```shell
mysql -uroot -p
```

![image.png](https://i.loli.net/2020/04/10/y5En8xTauUK4DYt.png)

- 此时还是不行，需要进行如下操作
```shell
repair table mysql.user;
```

- 后面为要修复的表，可以使用schema.表名，或者use 进入schema直接输入表名
![image.png](https://i.loli.net/2020/04/10/97vwacTRO2ygzVJ.png)
- 至此恢复完成
## 备注：
- 提示无法修改拥有着属性，应该是上一步使用myisamchk命令时文件所属变成了root了，于是用chown更该拥有者
```shell
chown -R /data/mysql
```



