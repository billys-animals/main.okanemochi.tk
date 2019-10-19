---
title: Visual studio Code の日本語化に困惑
author: スフィア
type: post
date: 2018-09-08T11:02:10+00:00
url: /computer_language/767/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/09/vsc_nihongo1-246x177.png
category_relation:
  - 'y'
tag_relation:
  - 'y'
disp_description_relation:
  - 'n'
menu_view:
  - 'y'
side:
  - 'y'
fullscreen_view:
  - 'n'
index:
  - index
follow:
  - follow
title_view:
  - 'y'
page_layout:
  - def
toc:
  - def
primary_category:
  - 125
pvc_views:
  - 96
keni_post_fb_time:
  - 1567516927
categories:
  - 開発言語

---
愛用のThinkPadをWindows10 32bitから64bitに載せ替えました。その影響でOSからクリーンインストールすることになり、VS CODEも新規で入れ直しをしました。

最新版をダウンロードしてインストール、そして、Ctl + Shift + P でコマンドを開き、Configure Languageなどのキーを打ち、locate.jsonを編集し、locale:&#8221;ja&#8221;として保存すればOK！というのが一般的にネット検索で得られる回答でした。

でも、そのままだと何も変化ないです。

正常に動いているデスクトップはVersion  1.24.0だった。最新版は1.27.1でした。

正常に動いているバージョンをダウンロードしてインストールしてみた。

## 結果

普通にメニューも日本語かされていましたが、以下の様なダイアログが表示されました。

<img class="alignnone wp-image-768" src="https://okanemochi.tk/wp-content/uploads/2018/09/vsc_nihongo1-300x115.png" alt="" width="518" height="199" srcset="https://okanemochi.tk/wp-content/uploads/2018/09/vsc_nihongo1-300x115.png 300w, https://okanemochi.tk/wp-content/uploads/2018/09/vsc_nihongo1.png 460w" sizes="(max-width: 518px) 100vw, 518px" />

どうやら、1.24.0から1.27.1の間のバージョンでこういう風に日本語化の仕組みが変わってきているのですね。

拡張機能の「Japanese Language for Visual Stuio Code」が必要という事なのでちゃんと入れておきましょうね！

一件落着！