---
title: '郑州大学宿舍电量监控部署方法'
published: 2025-02-21
description: ''
image: ''
tags: [tutorial]
category: TEC
draft: false
---

:::tip
原文地址：https://rimrose.top/Tutorial_for_ZZU_Dorm_Electricity_Balance/
:::

本文主要是为了介绍如何部署 [Elykia](https://github.com/elykia-cn) 同学的 [ZZU-Dorm-Electricity-Balance](https://github.com/elykia-cn/ZZU-Dorm-Electricity-Balance) 项目，如果你只想单独设置低电量提醒，可以自己进行修改

他在博客里发了一篇 [郑州大学宿舍电量监控：ZZU-Dorm-Electricity-Balance](https://blog.elykia.cn/posts/22.html)，但是看完这个博客并不能正确部署，所以我写了这篇博文来讲一下如何操作


## 详细步骤

首先你得有一个 Github 账号；如果没有的话请自行注册；如果 Github 都打不开的话建议还是不要继续往下看了

点开下面这个链接

::github{repo="rimrose/ZZU-Dorm-Electricity-Balance-Base"}

然后点击页面上的 "Fork"

![](https://img.rimrose.work/QQ截图20250224021209.png)

然后点击 "Create fork"

![](https://img.rimrose.work/QQ截图20250224021306.png)

Fork 完后点击 "Action" 选项卡

![](https://img.rimrose.work/QQ截图20250224021438.png)

然后点击 "I understand my workflows, go ahead and enable them"

![](https://img.rimrose.work/QQ截图20250224021610.png)

启用之后，点击左边的 "Update"

![](https://img.rimrose.work/20250224022139247.png)

然后点击 "Enable workflow"

![](https://img.rimrose.work/20250224022301566.png)

之后点击 "Settings" 选项卡

![](https://img.rimrose.work/20250224022419572.png)

然后按照下图顺序，将 "Pages" 的构建和部署源由 "Deploy from a branch" 改为 "GitHub Actions"

![](https://img.rimrose.work/20250224022633332.png)

之后在 Security 设置中选择 "Secrets and variables" → "Actions"

![](https://img.rimrose.work/20250224023101941.png)

然后点击 "New repository secret"

![](https://img.rimrose.work/20250224023304386.png)

依次添加下边这些 Secrets:


|      Name |       Secret |
|----------|-------------|
|   ACCOUNT | 郑州大学移动校园登录账户 |
|  PASSWORD | 郑州大学移动校园登录密码 |
|   lt_room |     照明电量房间代码 |
|   ac_room |     照明电量房间代码 |

> 这几个 Secrets 是必须添加的，否则会无法运行
>
> lt_room 和 ac_room 的格式一般应该是 "area-building--unit-room"，其中，area 是校区编号，building 是楼栋编号，unit 是单元编号（照明/空调），room 是房间编号
>
> 具体的编号请由文末的查询器查找
>
>（请注意，lt_room 的第一个字母是小写 L，不是大写的 i，其实也就是 light 的缩写）


| Name               | Secret             |
|--------------------|--------------------|
| EMAIL              | GitHub 邮箱          |
| TELEGRAM_BOT_TOKEN | Telegram Bot Token |
| TELEGRAM_CHAT_ID   | 	Telegram Chat ID  |
| SERVERCHAN_KEY     | Server 酱 API 密钥    |
| EMAIL              | 用来发送通知的邮箱          |
| SMTP_CODE          | 邮箱 SMTP 的 授权码             |
| SMTP_SERVER        | 邮箱的 SMTP 服务器地址            |

> 这几个 Secrets 是可选添加的
> 
> - Server 酱 API 密钥获取方法：
>  用微信登录 [Server 酱](https://sct.ftqq.com/) 之后点击上方的 "Key&API"，SendKey 即为生成的 API 密钥
> - SMTP_CODE 获取方法：
>  [获取主流邮箱授权码及配置SMTP服务器163/QQ/Aliyun/Gmail等](https://1aha.com/%E9%82%AE%E7%AE%B1%E6%8E%88%E6%9D%83%E7%A0%81smtp%E6%9C%8D%E5%8A%A1%E5%99%A8/)
> - SMTP_SERVER 获取方法：
>  [常用邮箱SMTP服务器地址大全](https://blog.csdn.net/ning521513/article/details/79217203)


例如：
![](https://img.rimrose.work/20250224023421268.png)

配置完之后 be like：
![](https://img.rimrose.work/QQ截图20250306152928.png)

一切就绪之后，你可以点击这个仓库主页上的齿轮图标，将仓库简介里的网页链接改为你自己的
![](https://img.rimrose.work/20250224024852663.png)