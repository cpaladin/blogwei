---
title: 分布式 Session
date: 2016-03-25 10:38:00

tags:
- Session
- 分布式 Session

categories:
- 技术文章
---

  Web 容器（比如tomcat等）已经实现了会话的基本管理。但是，如果你的服务部署在多个容器上（或者多台服务器），那么就不能再依赖容器自身的 Session 管理了，
  因为用户可能请求任何一台服务器，但是用户的会话却只存在于其中一台服务器上。除非服务器之间能共享或同步彼此的 Session。
  
  解决方案是把对 Session 的管理从容器中分离出来，把 Session 统一存储到诸如缓存（比如 memcached、redis等）、数据库上去，并维护 Session 的有效期。
  
  另一种方式是直接把 Session 信息存储在 Cookie 中，每次请求都会携带 Cookie，这样服务器也能获取到用户的 Seesion 信息。但是，因为 Cookie 是存储在浏览器客户端的，必须
  考虑到其中的安全性问题。