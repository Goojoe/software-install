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
>

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