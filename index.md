---
title: Index
---

<div id="wikiindex">

<ul>
{{- range pages "/wiki/*.md" -}}
{{- if and .title (ne .URL "/wiki/") -}}
<li class="wikititle"><a href="{{.URL}}">{{.title}}</a></p>
{{end -}}
{{- end -}}
</ul>

</div>
