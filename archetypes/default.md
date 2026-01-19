---
date: '{{ .Date }}'
draft: true

weight: 1000

title: '{{ replace .File.ContentBaseName "-" " " | title }}'
---
