---
layout:		post
title:		Github Pages DNS设置
date:		2015-12-20 22:38:30 +0800
categories:	Git
---

经过一系列的研究之后，我好像终于把用Github Page托管静态网页的DNS配置好了。

其实设置很简单呐，只是刚开始的时候我看网上的教程很盲目，得到的信息太混乱了，我现在也就是在3个地方对域名的解析有相关的设置，Godaddy，DNSPOD以及Github上面的CNAME：

1. 买一个公网的域名，比如在Godaddy上买一个，一年50块的样子，然后去DNSPOD（一个国内提供DNS服务的提供商）注册一个账户，进DNSPOD账户里面可以看到两个本地的NS记录域名
2. 进Godaddy的账户里，把系统默认的NS记录修改为刚刚从DNSPOD得到的那两个NS域名
3. 在本地尝试dig username.github.io，可以多dig几次，得到好几个ip地址解析结果
4. 进入DNSPOD的设置页面，建两条A记录，把自己买的域名解析到上一步得到的那几个ip地址上
5. 进入Github上面静态网页的库里面，在根目录下面创建一个CNAME文件，里面输入买的域名（不带http://和WWW）

![DNSPOD](/fengzhichu-theme/img/DNSPOD-Set.png)

然后就搞定了。

具体解析流程应该是 先查询Godaddy的DNS服务器，查询不到然后NS记录查DNSPOD的DNS，DNSPOD反馈Github的ip地址回来，然后尝试使用买到的域名来访问页面，Github服务器得到你的自定义域名后，把页面指向你的静态网页地址，最后一步不知道是怎么实现的，后面再去找机会研究一下。

