---
title: Visual Studio Commuinty 2017でC言語の学習1
author: スフィア
type: post
date: 2018-05-03T12:02:26+00:00
url: /computer_language/c_lang/179/
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
  - 91
ampforwp-amp-on-off:
  - default
keni_post_fb_time:
  - 1566690703
categories:
  - C言語

---
今更ながら過去に何度も挫折したC言語の学習を始めました。昔（20年前や10年前や5年前）とは学習環境も劇的に良くなっているし、自身の知識やスキルもそれなりに上がっていつので今ならやりきれそうな予感がします。なにより、これからの時代を生き抜くには何らかんらでCやC++言語のスキルはやぱっり必修かと考え覚悟を決めました。

<a href="https://www.microsoft.com/ja-jp/dev/products/community.aspx" target="_blank" rel="noopener">Visual Studio Comminuty 2017 のインストール</a>

<img class="alignnone wp-image-180" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic1-300x196.png" alt="" width="531" height="347" />

基本的に**「C++によるデスクトップ開発」だけ選べば大丈夫**です。

後々諸々に言語や機能が必要になるかも知れませが必要になった時に必要な機能を追加すれば良いかと思います。インストールしましょう。

&nbsp;

以下、新規プロジェクトファイルを作成してコンソールにHello,World.を表示させるまでのキャプチャーです。

<img class="alignnone wp-image-181" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic2-300x169.png" alt="" width="525" height="296" />

<img class="alignnone wp-image-182" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic3-300x208.png" alt="" width="526" height="365" />

<img class="alignnone wp-image-183" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic4-300x237.png" alt="" width="527" height="416" />

<img class="alignnone wp-image-184" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic5-300x208.png" alt="" width="531" height="368" />

ソースファイルは明示的に拡張子を.cとする。.cppではCファイルでなくC++ファイルとなってしまう。

<img class="alignnone wp-image-185" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic6-300x261.png" alt="" width="533" height="464" />

<img class="alignnone wp-image-186" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic7-300x277.png" alt="" width="534" height="493" />

もし、「デバッグなしで実行」メニューが表示されない場合は、Ctl + F9で実行可能です。

とりあえずCファイルを実行してみる

<img class="alignnone wp-image-187" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic8-300x276.png" alt="" width="539" height="496" />

<img class="alignnone wp-image-188" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic9-284x300.png" alt="" width="542" height="573" />

一瞬、何か画面が揺れて何も起こりません。以下の設定が必要です。

以下の設定はソースファイルが存在していないと有効でないので上記の様にソースファイルを書いた後で設定します。

<img class="alignnone wp-image-189" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic10-258x300.png" alt="" width="543" height="631" />

<img class="alignnone wp-image-190" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic11-300x215.png" alt="" width="544" height="390" />

<img class="alignnone wp-image-191" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic12-300x215.png" alt="" width="546" height="391" />

コンソールアプリである事や、C/C++のSDLチェックをなしにする設定が必要らしいです。

<img class="alignnone wp-image-192" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic13-300x264.png" alt="" width="550" height="484" />

<img class="alignnone wp-image-193" src="https://okanemochi.tk/wp-content/uploads/2018/05/pic14-300x300.png" alt="" width="549" height="549" />

めでたく、コンソールが立ち上がり「Hello,World.」が表示されました。

これで学習を開始する事が出来ます。

<div class="chat_l ">
  <div class="talker">
    <b><img class="circle" src="https://okanemochi.tk/wp-content/uploads/2018/07/%E7%AC%91%E3%81%84%E6%81%90%E7%AB%9C1-300x300.png" alt="気に入ってくれたら下のボタンで広めて下さいね" />気に入ってくれたら下のボタンで広めて下さいね </b>
  </div>
  
  <div class="bubble_wrap">
    <p>
    </p>
  </div>
</div>