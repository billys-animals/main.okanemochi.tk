---
title: .htaccess←AnchorCMS
author: スフィア
type: post
date: 2019-09-10T15:00:00.000Z
categories:
  - 設定
tags:
  - さくらサーバー
---
さくらサーバーはOptionが使えないからコメントアウト_
**\#Options -indexes**
```html
#Options -indexes
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /

# Allow any files or directories that exist to be displayed directly

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d

# Rewrite all other URLs to index.php/URL

RewriteRule ^(.*)$ index.php?/$1 \[L]
</IfModule>
<IfModule !mod_rewrite.c>
ErrorDocument 404 index.php
</IfModule>
```