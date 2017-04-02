---
layout: page
title: About
description: Jarlonyan
keywords: Jarlonyan
comments: true
menu: 关于
permalink: /about/
---

我是Jarlonyan。

兴趣：数据挖掘、深度学习

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

## Skill Keywords

{% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %}
