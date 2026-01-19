---
date: '2026-01-19T02:01:17-08:00'
draft: true

weight: 1

title: 'Body'
---

There are two Hugo blocks to include content in the `<body>` of your site. 

One is named `main` and is where the majority of the content should go. This content will be inserted inside a `<main>` 
tag.

The other block is named `body`. This is for things like navigation, or other parts of the page that are outside of the
main content.

In your HTML template, include your content like this:

```gotemplate
{{ define "main" }}
    {{ .Content }}
{{ end }}

{{ define "body" }}
    {{ partial "nav.html" . }}
{{ end }}
```

