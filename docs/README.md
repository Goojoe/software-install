# 常用软件安装

一天,我想装一个软件,搜啊搜啊,各种过时的没啥用的博客,不再维护的老教程,折腾了一天也未必能搞好

所以我整理了一些软件的安装教程,有时间正好出出视频

祝你学Linux看的开心,玩的开心

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

# 宝塔面板

## [官网教程](https://www.bt.cn/bbs/thread-19376-1-1.html)

> 安装要求：
>
> 内存：512M以上，推荐768M以上（纯面板约占系统60M内存）
>
> 硬盘：300M以上可用硬盘空间（纯面板约占20M磁盘空间）
>
> 系统：CentOS 7.1+ (Ubuntu16.04+.、Debian9.0+)，确保是干净的操作系统，没有安装过其它环境带的Apache/Nginx/php/MySQL/pgsql/gitlab/java（已有环境不可安装）
>
> 架构：x86_64（主流服务器均是此架构），ARM不完整兼容（面板环境安装慢，部分软件可能安装不上）

## Centos

```bash
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && sh install.sh
```

## Ubuntu/Deepin

```
wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh && sudo bash install.sh
```


## Debian

```
wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh && bash install.sh
```

## Fedora

```
wget -O install.sh http://download.bt.cn/install/install_6.0.sh && bash install.sh
```

## 试验性Centos/Ubuntu/Debian安装命令 独立运行环境(python3.7)

> 可能存在少量兼容性问题 不断优化中 

```bash
curl -sSO http://download.bt.cn/install/install_panel.sh && bash install_panel.sh
```

## Linux面板7.8.0升级

```
curl http://download.bt.cn/install/update6.sh|bash
```

## 备用节点

### 使用方法:

替换`http://download.bt.cn/`为下面的链接

备用节点【香港】

```
http://116.213.43.206:5880/
```

备用节点【美国】

```
http://128.1.164.196:5880/
```

> 若点击更新后没生效，请尝试重启面板服务：
>
> ```
> bt restart
> ```

# Docker

## [官网教程](https://docs.docker.com/engine/install/)

```bash
curl -sSL https://get.daocloud.io/docker | sh
# 查看版本
docker version
```
## Centos

https://www.runoob.com/docker/centos-docker-install.html

## Ubuntu

https://www.runoob.com/docker/ubuntu-docker-install.html

## Debian

https://www.runoob.com/docker/debian-docker-install.html

# Docker-compse

最新发行的版本地址：https://github.com/docker/compose/releases

```bash
curl -L https://get.daocloud.io/docker/compose/releases/download/v2.4.1/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
# 授予可执行权限
sudo chmod +x /usr/local/bin/docker-compose
# 创建软链
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
# 测试是否安装成功
docker-compose --version
# cker-compose version 1.24.1, build 4667896b
```



# Golang安装

## [菜鸟教程](https://www.runoob.com/go/go-environment.html)

## 下载安装包

安装包下载地址为：https://golang.org/dl/

中国地址：https://studygolang.com/dl

![image-20220120233928831](https://img.goojoe.cc/2022/01/20/gp2lNDJj.png)

### 快速下载

```bash
wget https://studygolang.com/dl/golang/go1.17.6.linux-amd64.tar.gz
#x86_64
```

> 下载其他同理`wget`+`空格`+`安装包链接`
>
> 如果没有wget
>
> Centos
>
> `yum install wget`
>
> Ubuntu/Debian
>
> `apt install wget`

## 安装

1、下载二进制包：go1.17.6.linux-amd64.tar.gz

2、将下载的二进制包解压至 /usr/local目录

```
tar -C /usr/local -xzf go1.17.6.linux-amd64.tar.gz
```

> **注意!**版本是会一直变的,所以请将1.17.6替换为你的安装版本

## 添加环境变量

`~/.bash_profile`:当前用户变量

`/etc/profile`:所以用户全局环境变量,下面的教程以此为例子

```bash
vi /etc/profile
```

[vi编辑器教程](https://www.runoob.com/linux/linux-vim.html),你也可以直接SFTP编辑

- 添加

```profile
export PATH=$PATH:/usr/local/go/bin
```

### 刷新环境变量配置文件

```
source /etc/profile
```



# Nodejs

## [官网](https://nodejs.org/en/)

## Centos

```bash
sudo yum update #更新yum包管理器

sudo yum -y install curl #安装curl

curl -fsSL https://rpm.nodesource.com/setup_16.x | sudo bash - #下载rpm包

sudo yum install -y nodejs #安装nodejs

node -v #查看nodejs版本

npm -v #查看npm版本
```

> 装不上请更新epel仓库，参见[华为云epel镜像](https://support.huaweicloud.com/ecs_faq/ecs_faq_1007.html)

## Debian/Ubuntu

```bash
sudo apt update #更新apt包管理器

curl -sL https://deb.nodesource.com/setup_16.x | sudo bash - #下载deb包

cat /etc/apt/sources.list.d/nodesource.list #验证nodejs存储库是否添加

sudo apt -y install nodejs #安装nodejs

node -v #查看nodejs版本

npm -v #查看npm版本
```

# RSShub服务器部署

[我的博客](https://goojoe.cc/23.html)

[影子屋参考](https://blog.bgme.me/posts/how-to-install-rsshub/#nodejs)

[RSShub官方文档](https://docs.rsshub.app/)

## 视频教程

- [打破信息茧房，RSShub搭建教程](https://www.bilibili.com/video/BV1VR4y1g7qm)

## 1.环境配置

### 1.nodejs

> 编译安装容易报错,所以采用rpm,deb包安装

[Nodejs安装](Linux\Nodejs.md)

### 2.yarn

> npm也是经常报错，所以我选yarn

- 1.安装

```bash
npm install -g yarn --registry=https://registry.npm.taobao.org #npm使用淘宝源安装yarn

yarn config set registry https://registry.npm.taobao.org -g #更换淘宝源镜像

yarn config set sass_binary_site http://cdn.npm.taobao.org/dist/node-sass -g

yarn -v #查看yarn版本
```

## 2.安装RSShub

### 1.安装git

```bash
apt install -y git #debian/ubuntu

yum install -y git #centos
```

### 2.克隆仓库

> 网站运行目录克隆

```bash
git clone https://github.com/DIYgod/RSSHub.git #官方github仓库

#其他的github镜像
git clone https://gitclone.com/github.com/DIYgod/RSSHub.git
git clone https://github.com.cnpmjs.org/DIYgod/RSSHub.git
```

### 3.服务部署

- 安装服务

```bash
npm ci --production #npm

yarn install --production #yarn
```

- 启动

```bash
npm start #npm

yarn start #yarn

#或使用 PM2(opens new window)
pm2 start lib/index.js --name rsshub
```

### 4.访问

访问

```bash
http://<ip或域名>:1200
```

即可

### 5.反向代理

ip:端口而且不带https总归

- 不好看

- 不好用

- 不安全的

    所以使用宝塔来Nginx反向代理

配置好你的域名>>设置>>反向代理

![image-20211226223855631](https://img.goojoe.cc/2021/12/26/u7CDEdzi.png)

### 6.使用方法

将rsshub.app域名替换为你自己的即可

## 3.开机自启动

```bash
vim /etc/systemd/system/rsshub.service
```

> 没有vim就把vim换成vi或者使用SFTP工具到`/etc/systemd/system/`创建`rsshub.service`文件并编辑

vim使用方法

`i`键进入编辑模式

`ESC键`+`:`+`wq`:保存并退出

`ESC键`+`:`+`q!`:强制退出（不保存）

`Shift`+`insert`:粘贴

> `insert`一般在退格键的右边

- 代码

```text
[Unit]
Description=Rsshub
After=network.target
Wants=network.target

[Service]
Type=simple
#下面的改为你的网站目录，宝塔默认网站在/www/wwwroot/你的域名,例子:/www/wwwroot/rsshub.goojoe.cc
WorkingDirectory=<!!!你的网站目录!!!>
ExecStart=/bin/bash -c 'yarn start'
Restart=on-failure
#User=rsshub #User和Group可以忽略，配置需要权限问题,删掉#号注释即可开启
#Group=rsshub

[Install]
WantedBy=multi-user.target
```

1. 执行命令

```bash
systemctl daemon-reload          #重载Systemd脚本
systemctl enable rsshub.service  #开机自启动
systemctl status rsshub.service  #查看状态
```

2.常用systemd命令

```bash
systemctl daemon-reload          #重载Systemd脚本
systemctl enable rsshub.service  #开机自启动
systemctl disable rsshub.service #关闭开机自启动
systemctl start rsshub.service   #启动
systemctl stop rsshub.service    #停止
systemctl status rsshub.service  #查看状态
```

## 4.其他

配置文件在`lib/config.js`

[配置文档](https://docs.rsshub.app/install/#pei-zhi)

完成以上安装后，可以生成大多数网站的RSS，但部分RSS需要单独配置后方可生成，如 [pixiv](https://accounts.pixiv.net/signup)、[disqus](https://disqus.com/api/applications/)、[twitter](https://apps.twitter.com/)、[youtube](https://console.developers.google.com/)、[telegram](https://telegram.org/blog/bot-revolution)、[github](https://github.com/settings/tokens)

下面将以 pixiv 为例介绍相应的配置方法。

- systemd配置文件

手动部署直接修改 systemd service 文件，在 `Environment` 中加入所需环境变量即可。可添加多个变量，变量之间使用空格分隔开来。

```text
[Unit]
Description=Rsshub
After=network.target
Wants=network.target

[Service]
Type=simple
WorkingDirectory=/www/wwwroot/rsshub.goojoe.cc
ExecStart=/bin/bash -c 'yarn start'
Environment=PORT=1200 CACHE_TYPE=memory CACHE_EXPIRE=600 LISTEN_INADDR_ANY=0 PIXIV_USERNAME=user PIXIV_PASSWORD=password
Restart=on-failure
#User=rsshub #User和Group可以忽略，配置需要注意权限问题,删掉#号注释即可开启
#Group=rsshub

[Install]
WantedBy=multi-user.target
```

## 协议

> CC BY-SA 4.0
>
> 署名-相同方式共享（BY-SA）：使用者可以对本创作进行转载、节选、混编、二次创作，可以将其运用于商业用途，唯须署名作者，并且采用本创作的内容必须同样采用本协议进行授权
