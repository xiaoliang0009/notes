# Linux 配置 v2ray代理

* 先安装 v2ray

> 官方文档：[https://www.v2ray.com](https://www.v2ray.com)
>
> 执行：`bash <(curl -L -s https://install.direct/go.sh)` 安装 v2ray
>
> * `/usr/bin/v2ray/v2ray`：V2Ray 程序
> * `/usr/bin/v2ray/v2ctl`：V2Ray 工具
> * `/etc/v2ray/config.json`：配置文件
> * `/usr/bin/v2ray/geoip.dat`：IP 数据文件
> * `/usr/bin/v2ray/geosite.dat`：域名数据文件

* 设置代理

```text
# 开启代理, v2ray 默认端口:10808
export http_proxy="socks5://127.0.0.1:10808"
export https_proxy="socks5://127.0.0.1:10808"

# 关闭代理
unset http_proxy
unset https_proxy
```

* 其他

> 1、查看 v2ray 状态 `systemctl [status|restart|stop...] v2ray`
>
> 2、替换其他的服务地址只需要替换`/etc/v2ray/config.json` 然后执行 `systemctl restart v2ray`
>
> 3、如何生成配置文件，用windows 的 v2rayN 或其他客户端工具来导出

