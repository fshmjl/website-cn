---
title: 安装
next:
  title: 配置编辑器
  path: /docs/get-started/editor
---

请选择您要安装Flutter的操作系统：

{{site.alert.note}}
  **您使用的是Chrome操作系统吗？**

如果是，请参阅官方 [Chrome OS Flutter安装文档！](/docs/get-started/install/chromeos)
{{site.alert.end}}

<div class="card-deck mb-8">
{% for os in site.os-list %}
  <a class="card" href="/docs/get-started/install/{{os | downcase}}">
    <div class="card-body">
      <header class="card-title text-center m-0">
        {{os}}
        <i class="fab fa-{{os | downcase}}"></i>
      </header>
    </div>
  </a>
{% endfor %}
</div>

{{site.alert.important}}
  如果您在中国，请阅读 [如何在中国使用Flutter](/community/china).
{{site.alert.end}}

