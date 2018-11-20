---
title: "Getting Started with Hugo"
date: 2014-04-02
tags: ["go", "golang", "hugo", "development"]
draft: false
---

## Hugo

Hugo 

### How to override CSS

```
[params]
    custom_css = ["css/foo.css", "css/bar.css"]
```
You can reference as many stylesheets as you want. Their paths need to be relative to the static folder.

Inside the header partial you can include every custom stylesheet from above beside the original one:

```
{{ range .Site.Params.custom_css -}}
    <link rel="stylesheet" href="{{ . | absURL }}">
{{- end }}
```


