## trouble: 
    1. `192.168.1.1` 官网设置页面的进入

## solution
    1. hosts 端口域名映射
    2. 清除浏览器 cookie.

## 配置方法
1. 更改副路由器的`192.168.1.1` --> `192.168.1.2`
![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/221842220.png)

2. DHCP 服务器
![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/222055889.png)

3. 设置该副路由器的 wifi 密码, 和主路由保持一致. 设置完成后, 需要重新连接下刚设置过 wifi 密码的 wifi .
![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/222228955.png)

4. 设置 wds
![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/223112105.png)

5. 进入 `192.168.1.2`, 检查是否开启 wds 功能

![image](https://raw.githubusercontent.com/koneMorris1625/myGitImageRepo/develop/newLife/20210917/223255438.png)