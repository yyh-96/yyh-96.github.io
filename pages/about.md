---
layout: page
title: About
description: 编成改变世界
keywords: yyh, 尹耀辉
comments: true
menu: 关于
permalink: /about/
---

机械转行入IT

是程序员，但不仅是程序员

坚信熟能生巧，努力改变人生。

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
