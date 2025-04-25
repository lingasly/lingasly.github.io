大学校园里宽带都不会很高，大一刚来的时候就办理校园卡（100兆），也是校园里宿舍最大网速。由于电信运营商赠送的路由器是上个世纪的产物，经常断流，而且还需要手动重启才能恢复。因此就购买了新的路由器（其实是二手的）。

**小米mini路由器**
![淘宝价格](https://cdn.jsdelivr.net/gh/lingasly/img@main/image/taobao_20250425.webp)

小米路由器 mini搭载MT7620A处理器，配备USB 2.0接口。
ROM：16MB SPI Flash; RAM:128MB DDR2；主频：580Mhz单核，支持2.4G和5G两种频段。
虽然网口都是100M，但大学网速最大也是100M，所以刚刚好，价格也便宜。

二年前小米mini路由器就是20左右，现在也差不多，但现在更推荐加点小钱上小米r3g。配置更好，而且还是usb3.0，可以实现轻nas使用。


**小米mini路由器装ddnsto步骤**

1. 路由器刷成padavan
如果不会刷的可以去bilibili看视频刷，手把手教学，手残党也学得会。[bilibili教学](https://www.bilibili.com/video/BV1qV411j7P8)
如果路由器刷成openwrt的话，可以直接在软件包里下载挺方便。但刷openwrt觉得路由器日常负载高，内存占用也高些，可能是内核版本高的原因，碰到多人上网也会卡顿。所以我选择刷padavan系统，padavan系统是由hanwckf仓库编译，我编译仅仅只有基本功能，不含插件~~aria2、adbyby~~。由于仓库里并不包含ddnsto插件，只能自己手动添加。需要固件可以在博客后面链接下载。
![padavan系统](https://cdn.jsdelivr.net/gh/lingasly/img@main/image/20250425213928341.webp)

2. 使用putty连接路由器
IP地址：192.168.2.1
账号、密码：admin
![](https://cdn.jsdelivr.net/gh/lingasly/img@main/image/20250425214303540.webp)
 
3. 下载ddnsto二进制文件

```cd /etc/storage```

```vi ddnsto.sh```

```
#!/bin/sh

wget --no-check-certificate https://fw0.koolcenter.com/binary/ddnsto/linux/mipsel/ddnsto -O /tmp/ddnsto
chmod 777 /tmp/ddnsto
/tmp/ddnsto -u 91370692-f868-48c3-a8d1-834fc6625e31 -d
````
保存

4. 将ddnsto.sh文件保存在闪存
浏览器登陆192.168.2.1
![](https://cdn.jsdelivr.net/gh/lingasly/img@main/image/20250425222220744.webp)

5. 设置开机自启动
`/etc/storage/uu/ddnsto.sh`
![](https://cdn.jsdelivr.net/gh/lingasly/img@main/image/20250425221743360.webp)

6. [padavan固件链接](https://wwxe.lanzoub.com/imx112m2zd5a)
密码：g2k5