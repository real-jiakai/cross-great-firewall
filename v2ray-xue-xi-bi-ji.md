# 1⃣ v2ray学习笔记

1、http协议主要用于网站，vmess协议主要用于代理我们发出的http请求。

2、v2ray是一个网络工具，它原创并支持vmess协议，同时也支持shadowsocks、trojan等代理协议。

3、vmess依赖于系统时间，请确保使用v2ray的系统UTC时间误差在90s以内，与时区无关。

4、安装流程

```bash
# 安装v2ray
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh) --version v4.45.2
```

```bash
# 查看v2ray状态
systemctl status v2ray
# 允许v2ray开机自启
systemctl enable v2ray
# 启动v2ray
systemctl start v2ray
```

```bash
# 编辑v2ray配置文件
vim /usr/local/etc/v2ray/config.json

{
  "inbounds": [
    {
      "port": 8388, 
      "protocol": "vmess",    
      "settings": {
        "clients": [
          {
            "id": "544ef226-63fb-4ab6-9209-3809b2a5e5abc",  
            "alterId": 0
          }
        ]
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "freedom",  
      "settings": {}
    }
  ]
}
# 重启v2ray
systemctl restart v2ray
```

```bash
# arch linux安装acme脚本
pacman -S cron
# 安装acme脚本
curl https://get.acme.sh | sh -s email=gujiakai28@gmail.com
# 切换ca机构
acme.sh --set-default-ca --server letsencrypt
# dns模式申请证书
acme.sh --issue --dns dns_cf -d v1.fucgcfpwck.top
# 安装证书
acme.sh --install-cert -d v1.fucgcfpwck.top --ecc --key-file  /usr/local/etc/v2ray/server.key  --fullchain-file /usr/local/etc/v2ray/server.crt
# 修改v2ray配置文件
vim /usr/local/etc/v2ray/config.json

{
    "inbounds": [
        {
            "port": 8389,
            "protocol": "vmess",
            "settings": {
                "clients": [
                    {
                        "id": "544ef226-63fb-4ab6-9209-3809b2a5e5abc",
                        "alterId": 0
                    }
                ]
            },
            "streamSettings": {
                "network": "tcp",
                "security": "tls",
                "tlsSettings": {
                    "certificates": [
                        {
                            "certificateFile": "/usr/local/etc/v2ray/server.crt",
                            "keyFile": "/usr/local/etc/v2ray/server.key"
                        }
                    ]
                }
            }
        }
    ],
    "outbounds": [
        {
            "protocol": "freedom",
            "settings": {}
        }
    ]
}
# 重启v2ray
systemctl restart v2ray
# 编辑v2ray的系统服务配置文件
vim  /etc/systemd/system/v2ray.service

# 将user=nobody删除
# 重新加载systemd守护进程
systemctl daemon-reload
# 启动v2ray
systemctl start v2ray

# 将network改为ws
"network": "ws",
# 重启v2ray
systemctl restart v2ray
# 查看v2ray状态
systemctl status v2ray
```

```bash
# 安装nginx
pacman -S nginx
# 启动nginx
systemctl start nginx
# 允许nginx开机自启
systemctl enable nginx

# 配置nginx，可参考：https://bulianglin.com/archives/guide.html
# 重新加载nginx服务配置
systemctl reload nginx 
# 查看nginx状态
systemctl status nginx

# 重新配置v2ray
"wsSettings": {
   "path": "/ray"
 }
# 重启v2ray
systemctl restart v2ray
```
