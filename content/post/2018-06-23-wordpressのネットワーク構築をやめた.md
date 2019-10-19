---
title: WordPressのネットワーク構築をやめた
author: スフィア
type: post
date: 2018-06-23T05:18:49+00:00
url: /wordpress/422/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/06/wordpress1.png
category_relation:
  - 'n'
tag_relation:
  - 'n'
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
  - 12
ampforwp-amp-on-off:
  - default
pvc_views:
  - 127
keni_layout_post:
  - layout-basic
keni_layout_post_sidebar:
  - layout-sidebar-basic
keni_layout_post_navigation:
  - layout-navigation-show
keni_primary_category_post:
  - 12
keni_relation_post:
  - 'a:0:{}'
keni_post_fb_time:
  - 1566563501
categories:
  - wordpress

---
このブログですがこの２日くらいで色々と引っ越しを繰り返し、今の状態になりました。その内容を詳しく書くのはこの後の記事で書きますが、今日はその中で体験したWordPressのネットワーク作成からのマルチサイト運営をやめた理由を詳細に書こうと思います。

<h1 id="firstHeading" class="firstHeading" lang="ja">
  <a href="http://wpdocs.osdn.jp/%E3%83%8D%E3%83%83%E3%83%88%E3%83%AF%E3%83%BC%E3%82%AF%E3%81%AE%E4%BD%9C%E6%88%90" target="_blank" rel="noopener">ネットワークの作成</a>
</h1>

概要は↑のリンクを見て頂ければと思います。

以下に一度は構築したネットワークを真っ新にした大きな原因（理由）を書いていきます。

## プラグインやテーマはサイト全体で共有する。
  
＝＞サイト毎の個別の設定が出来ない（アクセス解析とか全サイト分貼れません）

他にも色々ありましたが、これだけは譲れないと思い、マルチサイト運営（ディレクトリ型）をやめました。Wordpressフォルダの下位層にwp-adminやwp-contentsが１つしかない為にサイト数分の設定がリアルに出来ないのです。

使いかってが悪いとか、出来る事が少ないとか、そういうのは大丈夫なのですが、サイト個別の設定が残せないのはやはり自分の中では×印がついてしまいました。

&nbsp;