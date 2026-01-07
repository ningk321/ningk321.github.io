# 一鍵腳本

```
#!/bin/sh

# 检查是否为 root 用户
if [ "$(id -u)" != "0" ]; then
    echo "此脚本需要 root 权限运行，请使用 sudo 或切换到 root 用户。"
    exit 1
fi

set -e  # 遇到错误立即退出

echo "正在更新软件源并安装 v2ray..."
apk update
apk add v2ray

echo "正在切换到 /usr/local/bin 并下载最新版 v2rayA..."
cd /usr/local/bin

# 获取最新版本号（从 GitHub releases 获取）
LATEST_VERSION="2.2.5.6"   # 你可以改成更新的
FILENAME="v2raya_linux_x64_${LATEST_VERSION}"

echo "最新版本: ${LATEST_VERSION}"
echo "正在下载 ${FILENAME} ..."

wget "https://github.com/v2rayA/v2rayA/releases/download/v${LATEST_VERSION}/${FILENAME}"

# 重命名并赋予执行权限
mv "${FILENAME}" v2raya
chmod +x v2raya

echo "v2rayA 下载并安装完成。"

echo "正在创建 /etc/init.d/v2raya 服务脚本..."
cat > /etc/init.d/v2raya << 'EOF'
#!/sbin/openrc-run

name="v2rayA"
description="A web GUI client of Project V which supports VMess, VLESS, SS, SSR, Trojan, Tuic and Juicity protocols"
command="/usr/local/bin/v2raya"
error_log="/var/log/v2raya/error.log"
pidfile="/run/${RC_SVCNAME}.pid"
command_background="yes"
rc_ulimit="-n 30000"
rc_cgroup_cleanup="yes"

depend() {
    need net
    after net
}

start_pre() {
    export V2RAYA_CONFIG="/usr/local/etc/v2raya"
    export V2RAYA_LOG_FILE="/tmp/v2raya/access.log"
    if [ ! -d "/tmp/v2raya/" ]; then
        mkdir "/tmp/v2raya"
    fi
    if [ ! -d "/var/log/v2raya/" ]; then
        ln -s "/tmp/v2raya/" "/var/log/v2raya"
    fi
}
EOF

chmod +x /etc/init.d/v2raya

echo "正在安装 iptables 和 ip6tables..."
apk add iptables ip6tables

echo "正在启动 v2rayA 服务并设置开机自启..."
rc-service v2raya start
rc-update add v2raya default

echo "安装完成！"
echo "v2rayA Web 界面默认地址：http://你的服务器IP:2017"
echo "首次访问会要求设置管理员账号密码。"
echo "透明代理等高级功能可在 Web 界面中配置。"
```

[installonalpine_v2raya.sh](https://github.com/user-attachments/files/24474111/installonalpine_v2raya.sh)