#Redis Usage

##ubuntu 安装配置
1. install
>```
> >sudo apt-get update
> >sudo apt-get install redis-server
>```

2. start ,stop ,restart
>```
> >sudo /etc/init.d/redis-server stop
> >sudo /etc/init.d/redis-server restart
> >sudo/etc/init.d/redis-server start
>```

3. config
>```
>path :/etc/redis/redis.conf
>配置远程访问
>最简单：将 bind 127.0.0.1 改为 bind 0.0.0.0
>```

4. useful commands
>```
> >redis-cli ping
> >redis-cli config get *
> >redis-cli 
>```

## Redis pool被耗尽
1. 由于在多进程情况下，插入数据过慢，导致的拥堵
>```
>使用pipe mode 执行批量写入和读取
>```


## JedisPool 配置
>


