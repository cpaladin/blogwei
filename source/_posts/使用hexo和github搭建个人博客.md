---
title: 使用 hexo 和 github 搭建个人博客
date: 2016-03-12 12:37:27
banner: http://cpaladin.github.io/blogwei/images/default.jpeg

tags:
- hexo
- github
categories:
- 技术文章
---

# 一、安装 hexo
  hexo 官网： https://hexo.io/

  hexo 中文安装文档： https://hexo.io/zh-cn/docs/index.html

1. 安装 `node.js`： https://nodejs.org/en/
2. 安装 `git`： http://git-scm.com/ ，**并配置好环境变量**
3. 安装 `hexo`
``` bash
$ npm install hexo-cli -g
$ hexo init blog
$ cd blog
$ npm install
$ hexo server	启动服务器，可以在本地 http://localhost:4000 浏览博客，搭建成功。
```
4. 配置_config.yml
	
	根据个人需要修改博客配置，参考 https://hexo.io/zh-cn/docs/configuration.html

# 二、修改主题
  hexo 主题： https://hexo.io/themes/

  我选择了 `icarus` 主题，然后找到了主题的 github 项目 `https://github.com/ppoffice/hexo-theme-icarus`，如何安装主题，请以你选择的主题为准。

** icarus 主题安装：**
1. 进入博客根目录，执行以下命令：
``` bash
$ git clone https://github.com/ppoffice/hexo-theme-icarus.git themes/icarus
```
2. 修改博客配置 `_config.yml`，修改 `theme` 为 `icarus`。
3. 重新生成静态网页:
```
$ hexo g
```
4. 打开博客，查看新安装的主题。

`icarus` 主题的配置，请参考： https://github.com/ppoffice/hexo-theme-icarus/wiki

	
# 三、发布到 github
  详情参考： https://hexo.io/zh-cn/docs/deployment.html
  **请先在 github 新建一个仓库，用于个人博客；然后把本机的 ssh public key 添加到仓库中**
1. 修改博客配置 `_config.yml`：
```  
deploy:
  type: git
  repo: git@github.com:cpaladin/blogwei.git
```
2. 安装 hexo-deployer-git :
``` bash
$ npm install hexo-deployer-git --save
```
3. hexo 自动发布到 github gh-page 分支：
``` bash
$ hexo g
$ hexo d
```
  github 自动为 gh-pages 分支分配了地址，作为项目主页展示，形如： http://cpaladin.github.io/blogwei ，请在仓库的设置菜单里查看自己的地址。关于 github pages 请参考 https://help.github.com/categories/github-pages-basics/ 。

# 四、在其他机器上发布博客
  主要是利用 github 在博客仓库下新建一个 master 分支保存博客的原始文件。 
1. 在原来的博客根目录下，执行：
``` bash
$ git init	初始化 git 仓库
$ git remote add origin git@github.com:cpaladin/blogwei.git
$ git remote set-url origin git@github.com:cpaladin/blogwei.git
$ git add -f scaffolds source themes _config.yml package.json .gitignore		请注意将 /themes/icarus 下面的 .git 目录删掉，否则添加时icarus内的文件会被 git 忽略掉
$ git commit -m "message"
$ git push origin master:master	将本地master推送到远程，github 上会自动创建 master 分支
```

**在其他机器上只需要操作：**
1. 请先安装 node.js 和 git 。
2. 新建一个 blog 目录，并在 blog 目录下执行：
``` bash 
$ git clone git@github.com:cpaladin/blogwei.git
$ npm install
```
4. 之后就可以正常写博客，并发布了。记得最后把修改的内容再次提交到 master。


