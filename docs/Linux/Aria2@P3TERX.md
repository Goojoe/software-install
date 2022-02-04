# Aria2一键安装管理脚本 增强版

## [Github](https://github.com/P3TERX/aria2.sh)

## 系统要求

CentOS 6+ / Debian 6+ / Ubuntu 14.04+

### 架构支持

x86_64 / i386 / ARM64 / ARM32v7 / ARM32v6

## 使用说明

* 为了确保能正常使用，请先安装基础组件`wget`、`curl`、`ca-certificates`，以 Debian 为例子：

    > CentOS替换`apt`为`yum`即可
```
apt install wget curl ca-certificates
```

* 下载脚本
```
wget -N git.io/aria2.sh && chmod +x aria2.sh
```

* 运行脚本
```
./aria2.sh
```

* 选择你要执行的选项

```bash
 Aria2 一键安装管理脚本 增强版 [v2.7.4] by P3TERX.COM
 
  0. 升级脚本
 ———————————————————————
  1. 安装 Aria2
  2. 更新 Aria2
  3. 卸载 Aria2
 ———————————————————————
  4. 启动 Aria2
  5. 停止 Aria2
  6. 重启 Aria2
 ———————————————————————
  7. 修改 配置
  8. 查看 配置
  9. 查看 日志
 10. 清空 日志
 ———————————————————————
 11. 手动更新 BT-Tracker
 12. 自动更新 BT-Tracker
 ———————————————————————

 Aria2 状态: 已安装 | 已启动

 自动更新 BT-Tracker: 已开启

 请输入数字 [0-12]:
```

如果你卡住了或者是其他原因装不上，可以使用代理脚本

使用以下脚本,by[听风](https://cxjiang.top/2018/08/18/rclone-googledrive/)

代理配置脚本
在`/etc/profile/`最底部添加以下配置,全用户生效

```
# proxy list
 function proxyoff(){
     unset http_proxy
     unset https_proxy
     unset socks5_proxy
     echo -e "已关闭代理"
 }

 function proxyon() {
     export no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com"
     export http_proxy="127.0.0.1:1080"    #此处改为自己的http代理端口
     export https_proxy=$http_proxy
     export socks5_proxy="127.0.0.1:1081"  #此处改为自己的socks代理端口
     echo -e "已开启代理"
 }
```
![](https://img.goojoe.cc/2022/02/02/VVOTo2Df.webp)
修改好配置文件中的代理IP和端口后,输入
```bash
#刷新环境变量配置文件
source /etc/profile
# 开启代理
proxyon
```
`proxyoff`可以关闭代理
使用export查看是否成功
```bash
export -p
```
![](https://img.goojoe.cc/2022/02/02/CLiSzn9j.webp)

>  这样就是成功的。我这个服务器是在家里的所以才是192.168.2.2

## 其他操作

启动：`/etc/init.d/aria2 start` | `service aria2 start`

停止：`/etc/init.d/aria2 stop` | `service aria2 stop`

重启：`/etc/init.d/aria2 restart` | `service aria2 restart`

查看状态：`/etc/init.d/aria2 status` | `service aria2 status`

配置文件路径：`/root/.aria2c/aria2.conf` （配置文件有中文注释，若语言设置有问题会导致中文乱码）

默认下载目录：`/root/downloads`

RPC 密钥：随机生成，可使用选项`7. 修改 配置文件`自定义

## Lisence
[MIT](https://github.com/P3TERX/aria2.sh/blob/master/LICENSE) © Toyo x P3TERX