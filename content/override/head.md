---
date: '2026-01-19T01:56:27-08:00'
draft: true

weight: 3

title: 'Head'
---

Anything that needs to go in the `<head>` of the page can be included using the block named `head`.

In your HTML template, include anything you want in `<head>` like this:

```gotemplate
{{ define "head" }}
    <style>...</style>
{{ end }}
```
