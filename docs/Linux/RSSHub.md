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