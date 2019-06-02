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
然后在需要的页面添加代码，对于本站，我在 `_layouts/post.html` 中添加了一个容器：
```             
{% if site.gitalk %}
<!-- Gitalk 评论 start -->
<div id="gitalk-container"></div>
<!-- Gitalk 评论 end -->
{% endif %}
```
并添加了一段 JavaScript 代码：
```
{% if site.gitalk.enable %}
<!-- Link Gitalk 的支持文件  -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
<script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>
    <script type="text/javascript">
    var gitalk = new Gitalk({
    // gitalk的主要参数
        clientID: '{{ site.gitalk.clientID }}',
        clientSecret: '{{ site.gitalk.clientSecret }}',
        repo: '{{ site.gitalk.repo }}',
        owner: '{{ site.gitalk.owner }}',
        admin: ['{{ site.gitalk.owner }}'],
        id: '{{ page.url }}',
        distractionFreeMode: false  // Facebook-like distraction free mode
    });
    gitalk.render('gitalk-container');
</script>
{% endif %}
<!-- Gitalk end -->
```
「关于」「链接」页面中，这两段代码可以放在一起。

之后授权登录 GitHub，并逐一进入各页面，Gitalk 就配置完成了。