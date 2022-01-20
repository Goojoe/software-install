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



