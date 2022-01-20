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