# 初始化数据库
> 使用临时容器初始化数据库:

#### 初始化kong数据库
```
docker run --rm \
     -e "KONG_DATABASE=postgres" \
     -e "KONG_PG_HOST=xxx.xxx.xxx.xxx" \ //postgres的ip
     -e "KONG_PG_PORT=5432" \  //postgres的端口
	 -e "KONG_PG_USER=kong"  \
    -e "KONG_PG_DATABASE=kong" \
    -e "KONG_PG_PASSWORD=kong" \
     kong:1.1.2-alpine kong migrations bootstrap
```

#### 初始化konga数据库
```
docker run --rm pantsel/konga:0.14.1 -c prepare -a postgres -u postgresql://kong:kong@xxx.xxx.xxx.xxx:5432/konga
```