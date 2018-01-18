---
title: 支持Kubernetes版本
---

{% capture overview %}

这个文档包含Kubernetes当前版本的文档，还有这个版本之前的四个版本。

{% endcapture %}

{% capture body %}

## 当前版本

当前版本是
[{{page.version}}](/).

## 之前版本

{% for v in page.versions %}
{% if v.version != page.version %}
* [{{ v.version }}]({{v.url}})
{% endif %}
{% endfor %}

{% endcapture %}

{% include templates/concept.md %}