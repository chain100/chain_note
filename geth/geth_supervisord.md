
* 安装supervisord
> pip install supervisor
> echo_supervisord_conf > /etc/supervisord.conf

* 修改supervisord.conf
```
[include]
files = /etc/supervisord.d/*.ini
```

* 生成 config.toml
```
geth --datadir /home/chain/geth_rinkeby --rinkeby --syncmode full 
--rpc --rpcaddr "0.0.0.0" --rpccorsdomain "*" --rpcapi "db,eth,net,web3" 
--cache=1024 --maxpeers 100 
dumpconfig > /home/chain/geth_rinkeby/config.toml

```

* 配置geth.ini

> /etc/supervisord.d/geth.ini

```
;geth_rinkeby
[program:geth_rinkeby]
directory=/home/chain/geth_rinkeby
command=/usr/local/go/bin/geth --config /home/chain/geth_rinkeby/config.toml console
autostart=true
autorestart=true
startsecs=3
user=root
redirect_stderr=true
stdout_logfile =/home/chain/geth_rinkeby/out.log
stderr_logfile =/home/chain/geth_rinkeby/out_err.log
```
启动supervisord
> supervisord -c /etc/supervisord.conf
> supervisorctl status
查看结果


