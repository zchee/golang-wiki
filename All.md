---
title: All Wiki Pages
template: true
---

(See [the wiki home page](/wiki/) for a less mechanical overview of the Go wiki.)

<div id="wikiindex">

<ul>
{{- range pages "/wiki/*.md" -}}
{{- if and .title (ne .URL "/wiki/") -}}
<li class="wikititle">{{$short := strings.TrimPrefix .URL "/wiki/"}}<a href="{{.URL}}">{{$short}}{{if ne $short .title}} (“{{.title}}”){{end}}</a>
{{end -}}
{{- end -}}
</ul>

</div>
