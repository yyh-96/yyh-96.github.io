---
layout: page
title: About
description: 编程改变世界
keywords: yyh, 尹耀辉
comments: true
menu: 关于
permalink: /about/
---

是程序员，但不仅是程序员


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
