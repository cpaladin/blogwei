---
title: linux通过mail命令发送邮件失败的问题
date: 2018-06-14 15:00:00

tags:
- linux
- mail
- 邮件
- Ip frequency limited

categories:
- 学习笔记
---

  最近使用linux上的mail命令，每天晚上定时发送邮件给客户，刚开始好好的，后面就发现有些邮件发不出去，然后在自己的发送邮箱内收到 Mail Delivery System 的邮件，标题为 Mail delivery failed: returning message to sender
![](images/mail1.jpg)
  打开附件，找到内容 550 Ip frequency limited，这个大概意思就是说发送邮件频繁，被腾讯服务器限制了（我们用的是腾讯企业邮，用自己的公司邮箱名发的邮件）。但是，我也就每天凌晨发了几封邮件，ip被限明显不科学。
  后来在网上查找问题的过程中，无意中看到设置账号密码云云，想到会不会是因为没有设置邮箱账号密码直接发送邮件容易受限。于是找到配置文件/etc/mail.rc，配置了以下内容，发现就可以发送邮件了！
```
  set from=
  set smtp=smtp.exmail.qq.com
  set smtp-auth-user=
  set smtp-auth-password=
```
 应该是设置了账号密码后，相当于登录到自己的邮箱，去发送邮件，这样当然就不会那么容易ip受限了。
