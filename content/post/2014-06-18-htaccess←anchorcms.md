---
title: .htaccess←AnchorCMS
author: スフィア
type: post
date: 2019-09-10T15:00:00.000Z
categories:
  - 設定
tags:
  - さくらサーバー
thumbnailImagePosition: left
thumbnailImage: ''
---
<pre><code class="html">#Options -indexes
&lt;IfModule mod_rewrite.c&gt;
RewriteEngine On
RewriteBase /

# Allow any files or directories that exist to be displayed directly

RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d

# Rewrite all other URLs to index.php/URL

RewriteRule ^(.*)$ index.php?/$1 \[L]
&lt;/IfModule&gt;
&lt;IfModule !mod_rewrite.c&gt;
ErrorDocument 404 index.php
&lt;/IfModule&gt;
</code></pre>

**\#Options -indexes**

_<span style="color: #ff0000;" data-blogger-escaped-style="color: red;">さくらサーバーはOptionが使えない</span>からコメントアウト_
