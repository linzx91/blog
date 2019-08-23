---
layout: post
title: "在个人博客中添加网易云音乐"
date: 2019-06-17 17:15:00 +0800
categories: Living
tags: music iframe
img: https://aligege-1259468288.file.myqcloud.com/img/2019-06-17-cloud-music.jpg
key: 2019-06-17-cloud-music
themecolor: "#fff"
themetextcolor: "#000"
describe: 
---

> 利用网易云音乐生成的 iframe 外链，插入到 Jekyll 博客文章中，只需要几行代码就能够实现。

<!--more-->

首先需要在 `_include` 目录下创建一个 `cloud-music.html` 文件，然后在文件中添加以下代码：

```html{% raw %}
<iframe frameborder="no" border="0" marginwidth="16px" marginheight="16px" width="100%" height="86"
src="//music.163.com/outchain/player?type=2&id={{ page.music-id }}&auto=1&height=66">
</iframe>
```
{% endraw %}

将整个 `cloud-music.html` 嵌入 `post.html` 具体位置根据个人需求，具体代码如下：

```liquid{% raw %}
<!-- cloud music -->
{% if page.music-id %}
{% include cloud-music.html %}
{% endif %}
```
{% endraw %}

然后在需要添加音乐的文章开头的 YAML 配置项添加`music-id: // 网易云音乐的歌曲id` 如下所示：

```yml
---
music-id: 1355089626
---
```

---

**效果就是这样：**
<iframe frameborder="no" border="0" marginwidth="16px" marginheight="16px" width="100%" height="86"
src="//music.163.com/outchain/player?type=2&id=1355089626&auto=0&height=66">
</iframe>

---

> 另外还有一种方法就是直接在 `_layouts/post.html` 文件中添加以下代码：

```html{% raw %}
{% if page.music-id %}
<iframe frameborder="no" border="0" marginwidth="16px" marginheight="16px" width="100%" height="86"
src="//music.163.com/outchain/player?type=2&id={{ page.music-id }}&auto=1&height=66">
</iframe>
{% endif %}
```
{% endraw %}

同样在需要添加音乐的博客文章开头的 YAML 配置项添加`music-id: // 网易云音乐的歌曲id`
