---
title: VPS(Conoha SSD)でKUSANAGIに感嘆
author: スフィア
type: post
date: 2018-06-24T05:24:10+00:00
url: /web_tecnology/vps/429/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/06/kusanagi.png
category_relation:
  - 'y'
tag_relation:
  - 'y'
disp_description_relation:
  - 'n'
menu_view:
  - 'y'
side:
  - 'n'
fullscreen_view:
  - 'n'
index:
  - index
follow:
  - follow
title_view:
  - 'y'
page_layout:
  - col1
toc:
  - def
primary_category:
  - 12
ampforwp-amp-on-off:
  - default
pvc_views:
  - 467
keni_layout_post:
  - layout-basic
keni_layout_post_sidebar:
  - layout-sidebar-basic
keni_layout_post_navigation:
  - layout-navigation-show
keni_relation_post:
  - 'a:0:{}'
keni_post_fb_time:
  - 1568046588
categories:
  - VPS
  - wordpress

---
wordPress用の超高速仮想環境であるKUSANAGIを導入して３日目です。最初は何だか良く分からなかったのですが、少し慣れてくるともう夢中です。KUSANAGI以外の環境でWordPressを使うのはちょっと嫌だと思う様にさえなっています。

## VPSでKUSANAGI

別にVPSを借りなくてもKUSANAGIは使えます。WindowsでもDokerとか使えば大丈夫だと思います。私はCONOHAというVPSを借りてそこでKUSANAGIを使ってWodPressのブログを複数作成して運用を始めています。

### KUSANAGIのイメージ

> ## 仮想マシン構成
> 
> ・WordPress 最新版（KUSANAGI 専用プラグイン同梱）
  
> ・CentOS 7.x
  
> ・Nginx 1.13.x
  
> ・Apache 2.4.x
  
> ・HHVM 3.11.x
  
> ・PHP 7.2.x（php-fpm, Cli）
  
> ・PHP 5.6.x（php-fpm, Cli）
  
> ・MariaDB Galera Server 10.1.x
  
> ・Ruby2.4.x
  
> ・Ruby on Rails最新版
  
> ・PostgreSQL 9.7
  
> ・pgpool-II 3.7.2
  
> ※PHP7.2の利用は、WordPress4.4以上、および対応プラグインが必須です。
> 
> 引用元：https://kusanagi.tokyo/about/

上記の様に、複数の環境を１つの箱にまとめて、その中にインストールされたWordPressを使い自分のブログを作りましょうといった感じの流れです。

<pre class="lang:xhtml decode:true ">kusanagi provision kusanagi_html</pre>

上記の様に「kusanagi provision XXXXX」kusanagi provisionコマンドで新規の「XXXXX」という名前の箱を作り、その箱の中をカスタマイズしてWordPressを運用します。

KUSANAGIを使う目的は色々あると思いますが**最大の理由は「速い」に尽きる**んじゃないかと思います。

### VPSでKUSANAGIを使う利点（理由）

KUSANAGIは何度も触って覚えます。少なくとも自分はそうでした。VPSのサーバー設定も何度もやり直して覚えます。で、それがVPSでなく自宅のサーバーとか、レンタルサーバーだったらと思うと挫折します。

１から１００の設定を完結するのに、１から１０で１回イメージ保存でバックアップ、１から３０まででバックアップ、１～８０まででバックアップの様に途中でも「ここまでは大丈夫」というポイントで環境を保存出来ていれば、失敗しても１からでなく前回保存の最新箇所からのやり直しで済みます。**VPSならこのイメージ保存が簡単にできます。時間にして４GBくらいなら３分前後です。**

要所でこのイメージ保存をする事で毎回１からやり直しがなくなり、挫折する事なくサーバー構築が出来る様になるのです。こうやって文章で書くと当たり前なのですが、実際の作業でこのイメージ保存機能があると最高の保険だと思います。

レンタルサーバーでもイメージバックアップは出来るでしょうが、おそらく数時間レベルの作業になり、その間作業が止まります。最近の格安のVPSならば月額９００円前後からそういった環境が使えるのでとても便利だと思います。

ちょと調べてみると、KUSANAGI搭載のレンタルサーバーはある様ですが月額2000円以上の高額サービスばかりなのです。当方の様の低所得者には格安のVPSが嬉しいです。

##### VPSでKUSANAGIを使って一番嬉しかった利点

###### 1つのVPS（1サーバーで1つのIPアドレス）で幾つでもWordPressのブログを作成可能（複数ドメイン対応）

今まで自分の中の常識がドメインと場所は1対1でした。（例えば、okanemochi.tk＝150.95.149.122）の場所だと。VPS側の150.95.149.122というIPにokanemochi.tkよいうドメインが紐付いた場合に、150.95.149.122というIPアドレスに対して複数のドメインを割り当てられないと思っていました。

要は**<span style="color: #008000;">IPアドレスが唯一、サーバーの場所を示す目印で、ドメインのレジストラとそこで1対1に紐付くものだと理解していました。それだ正しい理解です。</span>**

厳密に言えばローカルセグメント化を行い、1つのIPアドレスを内部的に複数の場所に区切りマルチドメインを実現出来る方法はありますが、ちょと今の当方には荷が重い作業でした。

なので、2つ目のドメインを利用しようと思い、1つのサーバーの2つ目のIPアドレスを追加しました。でも、結果的には不要でした。

現状はこの1つのIPアドレス（1つのサーバー）に対して複数のドメインを割り当てて運用を始めています。

&nbsp;

<img class=" wp-image-434 alignleft" src="https://okanemochi.tk/wp-content/uploads/2018/06/domain1-300x146.png" alt="" width="438" height="213" srcset="https://okanemochi.tk/wp-content/uploads/2018/06/domain1-300x146.png 300w, https://okanemochi.tk/wp-content/uploads/2018/06/domain1-768x374.png 768w, https://okanemochi.tk/wp-content/uploads/2018/06/domain1-1024x499.png 1024w, https://okanemochi.tk/wp-content/uploads/2018/06/domain1.png 1245w" sizes="(max-width: 438px) 100vw, 438px" />

この写真の様に他のドメイン（サブドメイン）をレジストラから150.95.149.122に割り当ててVPSで運用出来ています。

つまりは、150.95.149.122というIPに複数のドメインを割り当てていると「いう事です。

レンタルサーバーなどでは、<span style="color: #ff0000;"><strong>「ドメインをこのフォルダに割り当てる様な機能」</strong></span>があるのでそれで実現出来ているのですが、VPSではそういう機能はないと思うので無理だと考えていました。

ですが、KUSANAGIを利用する事でこれが簡単にできる事が分かりました。上で説明したセグメント化をKUSANAGIが片代わりしてくれている様な格好になっています。

↑で説明したprovision が1つの識別要素になっているので、言い方を変えれば<span style="color: #008000;"><strong>「provision 毎にドメインの特定が出来る」のです。</strong></span>

つまり、VPSの容量やスペックが許容する範囲内であれば、1つのサーバーで複数のドメインを割り当てて複数のWordPressをKUSANAGI環境で動作させる事が可能なのです。もう、この環境以外は使いたくありません。（サーバーによりセグメントの数や1サーバー内に追加出来るIPアドレスの制限があります）

###### 1つのKUSANAGIのprovision の中に他のアプリを設置してKUSANAGI環境で利用可能

これは良い面と悪い面があります。先ずは悪い面を紹介します。

↑の方法で**1つのサーバー内に複数のprovision で複数のWordPressを稼働されるので、MySqlデータベースは各provision 毎に作成します。**なので、phpMyAdminなどでVPS内のデータベースを一カ所集中でメンテするなどの処理は出来ません。必要であれば各provision 毎にphpMyAdminを配置するしかありません。これは仕方ないですがちょと残念です。

次に良い面です。

当方はアクセス解析にGoogleアナリティクス以外にも、PIWIK(現MATOMO)を使っています。今まではKUSANAGI以外のサーバーに配置していましたが、1つのサーバーでKUSANAGIのみの運用になりMATOMOを設置する事が出来ない状態になりました。過去記事など検索するとKUSANAGI環境でもインストール出来る様な事がありましたが現環境で簡単に通用する方法は見つかりませんでした。

でも、答えは凄く簡単な場所にありました。

kusanagi provisionで作成した個人の備忘禄的な検索エンジンに公開しないWordPressがあったので、そのprovision内のDocumentRootフォルダにpiwikを仕込み、その環境内のKUSANAGIに同居させてもらい、MySQLデータベースも使わせてもらう感じでMATOMOをインストールしました。つまり、<span style="color: #008000;"><strong>MATOMOを使う目的で空のWordPress環境をKUSANAGIで作成するという手法でOKという事です。</strong></span>

順序が遅れましたが、<span style="color: #008000;"><strong>上のphpMyAdminも入れるのであればこのMATOMOと同じ様にそのprovision内のDocumentRootフォルダに仕込みインストールします。</strong></span>

これで、<span style="color: #ff0000;">当方が毎月680円で借りているconohaで、WordPress環境＋「KUSANAGI環境でのPIWIK（MATOMO）やphpMyAdminを稼働させる」事が可能になります。</span>
  
conohaのVPS：SSDタイプでメモリ2GB容量50GBだと月額1,750円ですね。当方はメモリ512MBで容量50GBで月額680円の一番安いサーバーでテスト運用中です。十分早いです。

<a href="https://px.a8.net/svt/ejp?a8mat=2ZGZ31+26LTGQ+50+4YSWE9" target="_blank" rel="nofollow noopener"><br /> <img src="https://www22.a8.net/svt/bgt?aid=180510877132&wid=028&eno=01&mid=s00000000018030032000&mc=1" alt="" width="336" height="280" border="0" /></a>