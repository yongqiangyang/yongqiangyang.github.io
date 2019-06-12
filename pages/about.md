---
layout: page
title: contact
description:
keywords: yongqiangyang,杨永强
comments: true
menu: 联系
permalink: /contact/
---

我是谁呢？你猜猜看呀！

## 联系

{% for website in site.data.social %}
* {{ website.sitename }}：[@{{ website.name }}]({{ website.url }})
{% endfor %}

<!-- ## Skill Keywords -->

<!-- {% for category in site.data.skills %}
### {{ category.name }}
<div class="btn-inline">
{% for keyword in category.keywords %}
<button class="btn btn-outline" type="button">{{ keyword }}</button>
{% endfor %}
</div>
{% endfor %} -->
