# 使用国外服务器自建ssr梯子开启加速bbr访问vpn搭建教程

## 什么是 ssr？

ss 是 Shadowsocks 设计的代理服务，是一种基于 socks 的加密传输，你可以自己搭建一个这样的代理服务，这样可以通过这个服务来访问那些你无法访问的网站，例如 [Google](https://www.google.com)。

而 ssr 是 ShadowsocksR 的简称，它比 ss 更加安全，是 ss 的增强版。

## 什么是 bbr 加速？

bbr 是 google 出的一种算法，他可以让网络传输的延迟降低，达到加快访问网络速度的效果。

所以，搭建 ssr，再结合 bbr，可以有效的让你轻松快速并且安全的代理访问网络。

## 搭建属于自己的 ssr+bbr VPN的准备

* [拥有一台国外的服务器](#优惠购买云服务器vultr)
* [连接服务器](#连接到你的服务器)
* [安装搭建 ssr+bbr 脚本](#安装-ssr-bbr-搭建脚本)
* [开始享受使用自己的 vpn 代理服务](#使用-ssr+bbr-服务)


## 优惠购买云服务器vultr

在搭建之前需要一台境外的云服务器，而 [vultr](https://www.vultr.com/?ref=8944093-8H) 服务商比较稳定，安全，相当于境内的阿里云。

值得说的一点是， [vultr](https://www.vultr.com/?ref=8944093-8H) 给新用户的福利相当给力，充值 10 美元就可以获取 100 美元，你可以点击 [vultr 专属赠送新用户 100 美元](https://www.vultr.com/?ref=8944093-8H) 进去抢先注册。

右上角有注册按钮，你也可以切换成中文界面：

<img width="1446" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119019442-be0cc500-b98c-11eb-895b-0d6300dce93d.png">

![](https://user-images.githubusercontent.com/84239400/119019760-0d52f580-b98d-11eb-9837-aba0990f1dfb.png)

接着使用邮箱和密码就可以注册了。

![](https://user-images.githubusercontent.com/84239400/119020042-4ee3a080-b98d-11eb-8341-bfc30f4b103c.png)

进去之后你可以看到这个页面，说明你已经通过 [vultr 专属优惠链接](https://www.vultr.com/?ref=8944093-8H) 获得了 100 美元赠送的资格：

![](https://user-images.githubusercontent.com/84239400/119020173-733f7d00-b98d-11eb-8ecc-a1afeb556fe6.png)

现在你只要选择支付宝充值 10 美元以上，就可以获得额外赠送的 100 美元。

![](https://user-images.githubusercontent.com/84239400/119020280-966a2c80-b98d-11eb-9113-8f5f0b75c5ea.png)

接下来就可以在这个平台选购云服务器了。

点击页面左边菜单栏的 「Products」进入服务器选购页面。

### Choose Server 选择服务器

选择 Cloud Compute 即可：

![](https://user-images.githubusercontent.com/84239400/119020373-af72dd80-b98d-11eb-8478-02d735b82709.png)

### Server Location

服务器的位置，可以选择美国地区，比如纽约：

![](https://user-images.githubusercontent.com/84239400/119020467-cadde880-b98d-11eb-8927-d3d837bbc20c.png)

### Server Type

服务器类型，CentOS 8 x64 系统：

<img width="1297" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119020720-198b8280-b98e-11eb-9df3-19bf5a187a1e.png">

### Server Size

内存，个人使用10G完全够用，这里选择3.5美元一个月，性价比高，注意不要选择IPv6 ONLY的，要不然无法搭建使用。

<img width="1240" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119020895-4a6bb780-b98e-11eb-9ac8-3cdd4f4397de.png">

选择完了之后，下面的其它东西都不需要填，直接点击右下角 Deploy Now 就可以了：

![](https://user-images.githubusercontent.com/84239400/119020981-68391c80-b98e-11eb-9f16-00c75de88eeb.png)

这时候你就拥有了自己的一台云服务器了：

<img width="1261" alt="VPN搭建教程" src="https://user-images.githubusercontent.com/84239400/119021075-86068180-b98e-11eb-82a9-71edb9934f23.png">


点击 Cloud Instance ，可以看到你服务器的 IP 地址和密码：

<img width="1308" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119021183-a20a2300-b98e-11eb-8ff4-7f18d3e3bb80.png">


## 连接到你的服务器

### windows 系统连接到 vultr 服务器

windows 可以下载[PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)工具。

打开之后选择 session，将你在 vultr 网上得到的服务器 ip 复制过来，输入到这里：

![](https://user-images.githubusercontent.com/84239400/119023900-037fc100-b992-11eb-85ea-525a61a69657.png)

Port 默认 22，Connection Type 选择 SSH，接着点击 Open，连接进去之后输入你云服务器的密码。

### Linux 和 MacOS 连接到 vultr 服务器

Linux 和 MacOS 可以打开终端，使用如下命令连接：

```
ssh root@xx.xx.xxx.xx
```

`xx.xx.xxx.xx`就是你的服务器上的 IP 地址。

连接进去之后输入 yes 后按回车，接着输入你云服务器的密码，即可使用云服务器。

<img width="772" alt="vpn搭建教程" src="https://user-images.githubusercontent.com/84239400/119024049-32963280-b992-11eb-8c05-db6df1f7fbfa.png">

## 安装 ssr-bbr 搭建脚本

### 安装 wget 

复制如下命令到你的终端，然后回车执行安装：

```
yum install wget
```
## 安装 ssr-bbr 脚本

```
wget --no-check-certificate -O ssr-bbr.sh https://raw.githubusercontent.com/sucong426/ssr-bbr-vpn/main/ssr-bbr.sh
```

## 运行 ssr-bbr 脚本

执行如下命令：

```
chmod +x ssr-bbr.sh 
```
执行安装命令：

```
 sudo sh ssr-bbr.sh -ssr
```

### 设置你的 ssr 密码和端口

执行过程会提醒你输入 ssr 的密码：

```
Please enter password for ShadowsocksR:
```
输入你自己的密码后回车。

接着会提醒你输入 ssr 端口：

```
Please enter a port for ShadowsocksR [1-65535] 
```
随便输入一个数字回车即可。

稍等一会提示 ssr 安装成功：

```
Congratulations, ShadowsocksR server install completed!
Your Server IP        : xxx
Your Server Port      : xxx
Your Password         : xxx
Your Protocol         : xxx
Your obfs             : xxx
```
分别为属于你的 服务器ip地址，你的端口号，你的密码，你的协议，你的混淆方式。

把它们复制下来。

## 运行你的代理 ssr 服务
现在已经安装成功了，使用如下命令开启：

```
/etc/init.d/shadowsocks start
```

## 安装 bbr 加速

执行 bbr 命令：

```
 sh ssr-bbr.sh -bbr
```

稍等一会，提示按 y 重启，输入 y 回车，等待服务器重启，此时 ssr和 bbr 自动开启。

那么现在你就用了属于你自己的 ssr+bbr 服务了。


## 使用 ssr+bbr 服务

### windows 系统使用

1. 下载软件 [shadowsocks-windows](https://github.com/shadowsocks/shadowsocks-windows/releases/download/4.4.0.0/Shadowsocks-4.4.0.185.zip)
2. 解压运行，把你刚刚的ip和密码端口号和加密方式填进去，打开代理。
3. 开始访问 Google。

### Android 和 ios系统使用
1. 搜索 shadowsocks， 下载 app。
2. 打开并填写你的服务ip地址和密码等信息。
3. 开启代理访问

