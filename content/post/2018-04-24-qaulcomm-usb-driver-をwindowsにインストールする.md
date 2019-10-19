---
title: Qaulcomm USB Driver をWindowsにインストールする
author: スフィア
type: post
date: 2018-04-24T06:05:07+00:00
url: /mov_smaho/zenfone/154/
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
  - 386
ampforwp-amp-on-off:
  - default
primary_category:
  - 13
keni_post_fb_time:
  - 1568318128
categories:
  - ZenFone
  - 文鎮化

---
①Qaulcomm USB Driver のダウンロード

<blockquote class="wp-embedded-content" data-secret="RnxAqlAPqe">
  <p>
    <a href="http://www.99mediasector.com/install-qualcomm-drivers-pc-wxp-w7-w8-w10/">How To Install Qualcomm Drivers On Pc WXP/ W7 /W8 /W10</a>
  </p>
</blockquote>

<iframe class="wp-embedded-content" sandbox="allow-scripts" security="restricted" style="position: absolute; clip: rect(1px, 1px, 1px, 1px);" src="http://www.99mediasector.com/install-qualcomm-drivers-pc-wxp-w7-w8-w10/embed/#?secret=RnxAqlAPqe" data-secret="RnxAqlAPqe" width="600" height="338" title="&#8220;How To Install Qualcomm Drivers On Pc WXP/ W7 /W8 /W10&#8221; &#8212; 99Media Sector" frameborder="0" marginwidth="0" marginheight="0" scrolling="no"></iframe>

「Download Qualcomm Driver For Pc」のリンクよりダウンロード

ファイルを解凍し「Qualcomm\_USB\_Driver_V1.0.exe」を取り出し実行すればよいのですが、そのままでは失敗します。

証明証がない無署名のドライバーなのでインストールできない

仕方がないので、仮証明証ファイルをダウンロードしました。

②Qualcomm+2012

https://androidfilehost.com/?fid=24052804347806026

Qualcomm+2012を解凍すると以下の様な階層になっているので環境に合わせたWindowsの中のinfをインストールします。cer証明証書もインストールします。

<pre class="lang:default decode:true">-adb_driver_windows
-chk
　　-Windows7
　　-Windows8
　　　　　-qcmdm.inf
　　-XP-Vista
-fre
　　-Windows7
　　-Windows8
　　　　　-qcmdm.inf
　　-XP-Vista
-TestCertificate
　　-Windows7
　　-Windows8
　　　　　-qcusbtest.cer
　　-XP-Vista
</pre>

ですが、これも全て正常にインストールさせてくれません。署名がないドライバーはトコトン弾かれます。

 <img class="alignnone size-medium wp-image-164" src="https://okanemochi.tk/wp-content/uploads/2018/04/img01-1-203x300.png" alt="" width="203" height="300" /><img class="alignnone size-medium wp-image-165" src="https://okanemochi.tk/wp-content/uploads/2018/04/img02-1-217x300.png" alt="" width="217" height="300" />

一旦は作業し終えた状態でも、Testモード以外で、署名なしドライバーモード以外の通常の起動時に当方のZenfone5 A500KL LTEモデルを接続すると↑の様にドライバーが動作しません。

なので、↑の②番目の処理は環境が整った後で行います。

そうすると以下の様に動作可能状態になります。

<img class="alignnone size-full wp-image-167" src="https://okanemochi.tk/wp-content/uploads/2018/04/img03.png" alt="" width="251" height="199" />

 <img class="alignnone size-medium wp-image-168" src="https://okanemochi.tk/wp-content/uploads/2018/04/img04-223x300.png" alt="" width="223" height="300" /><img class="alignnone size-medium wp-image-169" src="https://okanemochi.tk/wp-content/uploads/2018/04/img05-279x300.png" alt="" width="279" height="300" />

最終的には以下の様にツールでも認識するところまでこぎ着けました。

<img class="alignnone size-medium wp-image-174" src="https://okanemochi.tk/wp-content/uploads/2018/04/img06-300x232.png" alt="" width="300" height="232" />

【手順】

<pre class="lang:default decode:true ">①windowsをTestModeにする
コマンドプロンプトを管理者権限で立ち上げ以下のコマンドを実行

bcdedit /set TESTSIGNING ON

②USB Driverのインストールや作業
１．Windowsを再起動するが、「&lt;a href="https://freesoft.tvbok.com/win10/testmode.html" target="_blank" rel="noopener" data-mce-href="https://freesoft.tvbok.com/win10/testmode.html"&gt;署名なしドライバ&lt;/a&gt;」で立ち上げる
　具体的には、Shiftキーを押しながら再起動を選び、再起動オプション画面に推移するまで「Shiftキー」を押し続ける。

２．Qualcomm_USB_Driver_V1.0.exeを実行してUSBドライバーをインストールする

３．↑のInfのインストールやcer証明証のインストールを行う

４．デバイスを接続して「デバイスドライバー一覧で確認する」

③windowsをTestModeから通常モードへ解除する
コマンドプロンプトを管理者権限で立ち上げ以下のコマンドを実行

bcdedit.exe -set TESTSIGNING OFF

※上記は環境構築時の手順ですが、実際にQualcomm&nbsp;CPUを使ったスマホの操作などする場合も同様に、Testモードで入り、
署名なしドライバモードで立ち上げ直し処理を行います。実際に今回の当方の処理はA500KLのアンブリック処理のためです。未成功ですが、、、。
</pre>

&nbsp;