---
title: BracketsでPHPデバッグ
author: スフィア
type: post
date: 2018-03-12T11:14:55+00:00
url: /computer_language/php/104/
category_relation:
  - 'n'
  - 'n'
tag_relation:
  - 'n'
  - 'n'
disp_description_relation:
  - 'n'
  - 'n'
menu_view:
  - 'y'
  - 'y'
side:
  - 'y'
  - 'y'
fullscreen_view:
  - 'n'
  - 'n'
index:
  - index
  - index
follow:
  - follow
  - follow
title_view:
  - 'y'
  - 'y'
catch_text:
  - 
  - 
header_image:
  - 
  - 
page_layout:
  - def
toc:
  - def
pvc_views:
  - 415
ampforwp-amp-on-off:
  - default
primary_category:
  - 8
keni_post_fb_time:
  - 1568339632
categories:
  - PHP

---
大前提として、Bracketsの拡張機能のPHP DEBUGGERを追加しておきます。

BracketsでPHPデバッグするには、何らかのローカルサーバー環境（XAMPPやMAMPなど）を動かし、PHPへのパスを通し、且つ、xdebugも使える状態にした上で、

<pre class="lang:vim decode:true ">C:\xampp\htdocs</pre>

に例えば、test1.phpなど配置して、Bracketsでtest1.phpを開き、ブレークポイントを設定した状態で、以下の様にブラウザから呼び出す。

（URLの末尾に**?XDEBUG\_SESSION\_START=xdebug**を付加する必要あり）

<pre class="lang:xhtml decode:true">http://localhost/test1.php?XDEBUG_SESSION_START=xdebug</pre>

<a href="https://okanemochi.tk/wp-content/uploads/2018/03/c1151933609ecbcb89e5d4f18410a31f.png" target="_blank" rel="noopener"><img class="alignnone wp-image-106 size-medium" src="https://okanemochi.tk/wp-content/uploads/2018/03/c1151933609ecbcb89e5d4f18410a31f-300x262.png" alt="" width="300" height="262" /></a>

VS CODEでのデバッグではURL末尾への「**?XDEBUG\_SESSION\_START=xdebug」の付加は必要なかったと記憶しております。**

&nbsp;

参考URL

<blockquote class="wp-embedded-content" data-secret="I0UxXlXWLq">
  <p>
    <a href="https://arrown-blog.com/brackets-phpdebugger/">BracketsでPHPデバッグがサクサク捗る！PHP debuggerの設定方法</a>
  </p>
</blockquote>

<iframe class="wp-embedded-content" sandbox="allow-scripts" security="restricted" style="position: absolute; clip: rect(1px, 1px, 1px, 1px);" src="https://arrown-blog.com/brackets-phpdebugger/embed/#?secret=I0UxXlXWLq" data-secret="I0UxXlXWLq" width="600" height="338" title="&#8220;BracketsでPHPデバッグがサクサク捗る！PHP debuggerの設定方法&#8221; &#8212; Arrown" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

&nbsp;

<div class="chat_l ">
  <div class="talker">
    <b><img class="square" src="https://okanemochi.tk/wp-content/uploads/2018/07/%E3%82%AB%E3%83%B3%E3%83%8B%E3%83%B3%E3%82%B0-300x204.png" alt="もし、参考になったならTwitterシェアお願いします" />もし、参考になったならTwitterシェアお願いします </b>
  </div>
  
  <div class="bubble_wrap">
    <p>
    </p>
  </div>
</div>