# Remote的技术选型
<!-- *************************
# -*- coding:utf-8 -*-
# author: WangLin <276293337@qq.com>
# filename: Remote的技术选型.md
# description: TODO
# create date: 2016-01-28 08:59:45
************************** -->

### Remote
* 定义
    
        服务器信息的远程推送，推送到指定的客户端，不管客户端是开启状态 or 后台状态 or 关闭状态，都可以实时提醒

### 推送技术的评估
##### Android平台
* Google官方提高的**GCM**
    * 存在问题
        1. Android很多被手机厂商定制化，厂商可能会去掉GCM服务。
        + Android 2.2到3.0之间需要安装Google Store并设置Google帐号。
        + 由于国内2G和移动3G的NAT超时时间都小于GCM心跳时间(28分钟)，TCP长连接必然无法保活，每次都要等28分钟心跳失败重连后才能收到Push。
        + 某些运营商可能限制了5228端口，移动3G/2G下，发现几乎无法连接上GCM服务器，也就无法获得GCM通知，WhatsApp放后台10分钟后，经常很长时间都收不到Push消息。
* 第三方技术
    * 根据项目采用的语言类型进行考虑，推荐使用腾讯的信鸽
    * 参考连接：[Android推送SDK哪家好][url1]

##### IOS平台
* Apple官方提高的**APNS**
* 越狱的IOS平台，可以采用第三方平台，具体选型参考Android的技术选型

##### WP平台
* Windows官方提供的**MPNS**
* 其他平台暂无了解

### 总结
* AppStore平台，采用APNS
* IOS和Android平台，采用第三平台采用腾讯的信鸽


[url1]:https://www.zhihu.com/question/22354498

-------

Copyright 2016 WangLin
