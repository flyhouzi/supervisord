##安装 rice 

```shell
    go get github.com/GeertJohan/go.rice
    go get github.com/GeertJohan/go.rice/rice
```

##编译进二进制文件

```shell
    rice embed-go
    go build
```

## ssh 隧道

```shell
    ## https://www.zsythink.net/archives/2450
    ssh -f -N -L 10.10.28.1:9001:10.10.28.2:5001 root@10.10.28.2
    ssh -f -N -L 10.10.28.1:9002:10.10.28.2:5002 root@10.10.28.2

```

```shell
    #ubutun 端口转发
    vi /etc/default/ufw
    DEFAULT_FORWARD_POLICY="ACCEPT"

    vi /etc/ufw/sysctl.conf
    net/ipv4/ip_forward=1

    vi /etc/ufw/before.rules

```

```shell
*nat

:PREROUTING - [0:0]

:POSTROUTING - [0:0]

-A PREROUTING -i eth0 -p tcp --dport 5001 -j DNAT --to-destination 172.16.101.104:5001
-A POSTROUTING -s 172.16.101.104 -o eth0 -j MASQUERADE

-A PREROUTING -i eth0 -p tcp --dport 5002 -j DNAT --to-destination 172.16.101.103:5001
-A POSTROUTING -s 172.16.101.103 -o eth0 -j MASQUERADE
```