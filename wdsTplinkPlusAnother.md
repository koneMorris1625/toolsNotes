- [trouble & solution:](#trouble--solution)
  - [1. 若两个路由初始 LAN 口 IP 地址都是 `192.168.1.1` , 无法进入特定地址](#1-若两个路由初始-lan-口-ip-地址都是-19216811--无法进入特定地址)
  - [2. 查看天翼路由的信道等信息](#2-查看天翼路由的信道等信息)
  - [3. 副路由器时常断网, 需要重新启动](#3-副路由器时常断网-需要重新启动)
- [多个 WiFi 路由器桥接配置方法](#多个-wifi-路由器桥接配置方法)
- [config information](#config-information)

## trouble & solution: 

### 1. 若两个路由初始 LAN 口 IP 地址都是 `192.168.1.1` , 无法进入特定地址

solution: 

> 1: hosts 端口域名映射
> 2: 清除浏览器 cookie.
> 3: 更改某个路由器的 LAN 口 IP: `192.168.1.1` --> `192.168.1.2`

### 2. 查看天翼路由的信道等信息

solution:

> solution1. PC cmd: `netsh wlan show networks mode=bssid`

> > `channel` 字段

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20220221/174718767.png)

> solution2. 进入设置更全面的电信 `192.168.1.1:8080`

> > username password 通常在路由器背面

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20220221/174943661.png)

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20220221/175453676.png)

### 3. 副路由器时常断网, 需要重新启动

solution: 

> 找原因时发现每次断网时ipv4的DNS服务器地址是192.168.3.2。而网络正常的时候DNS服务器的地址是192.168.3.1。原因就在这里，**在副路由管理页面设置DHCP服务器的时候可以设置DNS服务器地址。**设置完成之后断网很少了。

> 网上很多桥接路由器的教程都是副路由关闭DHCP服务器，但是关了后会导致断网频繁和无法连接等问题。
> 下面说说桥接路由器的具体过程。
> 1. 更改副路由的IP地址。
> 若主路由的IP地址为192.168.3.1，副路由可以更改为192.168.3.2。子网掩码设置为255.255.255.0。这样可以再次进入副路由的管理页面。
> 2. 开启WDS无线桥接
> 在桥接页面找到主路由的SSID，点击后输入密码。接着把信道设置为和主路由的一样。然后设置副路由的SSID和密码。
> 3. 设置DHCP服务器
> 这一步是解决断网及无法连接等问题的关键。
> 先进入主路由的DHCP服务器设置页面，找到IP地址分配范围，我的是192.168.3.3 – 192.168.3.254. 将其改为192.168.3.3 – 192.168.3.200.
> 然后进入副路由的DHCP服务器设置页面，将IP地址分配范围改为192.168.3.201 – 192.168.3.254. 只改最后一个整数就行。
> 最后把**副路由的网关和DNS服务器设置为主路由的IP地址**，即192.168.3.1.（根据主路由的IP地址而定）
> 版权声明：本文为CSDN博主「ln2037」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。原文链接：https://blog.csdn.net/ln2037/article/details/113527537

副路由器: 

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20220221/181116835.png)

## 多个 WiFi 路由器桥接配置方法

1. 更改副路由器的`192.168.1.1` --> `192.168.1.2`

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/221842220.png)

~~2. DHCP 服务器~~

~~

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/222055889.png)

~~

3. 设置该副路由器的 wifi 密码, 和主路由保持一致. 设置完成后, 需要重新连接下刚设置过 wifi 密码的 wifi .

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/222228955.png)

> home 为例: 
> ChinaNet-m9xP
> ahjxfkg3

4. 设置 wds

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/223112105.png)

5. 进入 `192.168.1.2`, 检查是否开启 wds 功能

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/223255438.png)

## config information

hometown

> 路由方式，网关自动拨号方式上网: 账号: NC5362756 passsword: undefined
