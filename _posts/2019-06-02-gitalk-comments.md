---
layout: post
title: "评论框"
author: "K. HWANG"
header-mask: 0.4
tags:
  - General
---

本站有了评论框。

基于 GitHub Issues 的 [Gitalk](https://github.com/gitalk/gitalk)，配置过程并不复杂，比较适合基于 GitHub Pages 的站点。

至此，本站初期的建设就告一段落了。

## 配置

**以下内容仅针对本站。**

首先要 [申请一个 OAuth Application](https://github.com/settings/applications/new)

`Authorization callback URL` 填写使用插件页面的域名。之后你会得到一个 `Cilent ID` 和 `Client Secret`。

然后在 `_config.yml` 添加以下内容：
```
# Gitalk
gitalk:
  enable: true
  repo: khwang9883.github.io		# Issues 所在的仓库
  owner: KHwang9883			# 仓库所有者
  admin: KHwang9883			# 对仓库有写权限的用户
  clientID: 'cilentID'			# GitHub Application Client ID
  clientSecret: 'cilentSecret'		# GitHub Application Client Secret
```
然后在需要的页面添加代码，对于本站，我在 `_layouts/post.html` 中添加了一个容器，并添加了一段 JavaScript 代码。由于这段代码在文中显示异常，我把它放到了评论区（顺便测试一下评论框的功能），也可以 [直接查看](https://github.com/KHwang9883/khwang9883.github.io/blob/master/_layouts/post.html)。

「[关于](https://github.com/KHwang9883/khwang9883.github.io/blob/master/about.html)」「[链接](https://github.com/KHwang9883/khwang9883.github.io/blob/master/friends.html)」页面中，这两段代码可以放在一起。

之后授权登录 GitHub，并逐一进入各页面，Gitalk 就配置完成了。