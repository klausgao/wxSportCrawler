# wxSportCrawler
一套抓取微信运动真实数据、并将微信运动数据用于活动/场景的程序

关键字：微信运动、微信步数、运动步数、wechat sport、wechat step、微信硬件

Demo：http://node.mzdol.com/wxSportDemo/

### 功能描述
**1、抓取个人的微信运动数据，形成实时数据、日数据、累计数据和其他按照需求进行统计的数据**

具体可以看Demo截图

(1)当前时间的步数实时显示

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E5%BD%93%E5%89%8D%E6%97%B6%E9%97%B4%E7%9A%84%E6%AD%A5%E6%95%B0%E5%AE%9E%E6%97%B6%E6%98%BE%E7%A4%BA.jpg)


(2)月步数按日显示

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E6%97%A5%E6%AD%A5%E6%95%B0%E6%8C%89%E6%9C%88.jpg)


(3)日实时步数排行榜

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E6%97%A5%E5%AE%9E%E6%97%B6%E6%AD%A5%E6%95%B0%E6%8E%92%E8%A1%8C%E6%A6%9C.jpg)


(4)累计步数排行榜

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E7%B4%AF%E8%AE%A1%E6%AD%A5%E6%95%B0%E6%8E%92%E8%A1%8C%E6%A6%9C.jpg)


**2、每日定时由个人号机器人提示日步数，加强活动粘性**

Demo截图

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E6%97%A5%E7%BE%A4%E5%8F%91.jpg)

### 各种流程图

**1、个人微信端报名流程图**

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E5%BE%AE%E4%BF%A1%E8%BF%90%E5%8A%A8%E6%8A%A5%E5%90%8D%E6%B5%81%E7%A8%8B.png)


**2、客户服务器拉取数据流程图**

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E5%AE%A2%E6%88%B7%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%8B%89%E5%8F%96%E6%95%B0%E6%8D%AE%E6%B5%81%E7%A8%8B%E5%9B%BE.png)


**3、群发日提醒到个人微信端流程图**

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E7%BE%A4%E5%8F%91%E6%97%A5%E6%8F%90%E9%86%92%E5%88%B0%E4%B8%AA%E4%BA%BA%E5%BE%AE%E4%BF%A1%E7%AB%AF%E6%B5%81%E7%A8%8B%E5%9B%BE.png)


### 技术综述和难点

(1)如何抓取微信运动数据

通过抓取微信PC客户端的Cookie，攻克抓取微信运动数据的技术难点。

看下图，通过fiddler抓取到微信PC端的https的登陆cookie。

![](https://github.com/klausgao/wxSportCrawler/raw/master/fiddler%E6%8A%93%E5%8C%85.jpg)


(2)服务器端程序，模拟登陆到微信PC客户端，轮询各个微信号的微信运动数据，抓取到本地数据库。

这步没有多少难点，只要熟悉模拟登陆即可完成。

但是程序的**稳定性**是一个很大的考验。实际开发中遇到了cookie过期、抓取超时等问题，花了很长时间一一解决。

(3)服务器端程序需对外提供Restful接口（需认证），给用户调取微信运动数据。

这步没有难点，就在于如何设计这个认证的接口。

(4)与微信个人Bot相关的开发

下面简称“微信个人号Bot”为“Bot”。

这里解释一下，因为按照流程图1和3，都需要用到一个微信个人号（就是普通的微信号）来实现报名和群发功能，所以这个Bot必须是一个实现了全功能的微信模拟登陆模拟操作的Bot。思路其实和github上已经有的不少项目是一样的。

我这里实现的Bot，在稳定性方面要稍微强一点。实际开发上，会遇到无规律掉线（这个最恐怖）、群发控制等问题，需要一点一点解决。

Bot的报名成功提示图：

![](https://github.com/klausgao/wxSportCrawler/raw/master/%E6%8A%A5%E5%90%8D%E6%88%90%E5%8A%9F%E6%8F%90%E7%A4%BA.jpg)


### 商务合作

这里已经实现了一个可用的API，可提供有限的试用。

具体请联系我，QQ 14707685，注明“微信运动数据”。

请关注这个项目，https://github.com/klausgao/wxSportCrawler/
