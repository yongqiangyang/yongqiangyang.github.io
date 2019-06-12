---
layout: page
title: Links
description: 没有链接的博客是孤独的
keywords: 友情链接
comments: true
menu: 链接
permalink: /links/
---

> God made relatives. Thank God we can choose our friends.
> 若有我的朋友想挂自己的博客在此处，请联系我！^\_^


{% for link in site.data.links %}
* [{{ link.name }}]({{ link.url }})
{% endfor %}
