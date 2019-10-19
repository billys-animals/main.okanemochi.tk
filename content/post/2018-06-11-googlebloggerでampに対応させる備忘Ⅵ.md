---
title: GoogleBloggerでAMPに対応させる備忘禄
author: スフィア
type: post
date: 2018-06-11T05:34:42+00:00
url: /web_tecnology/google-amp/311/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/06/24811613230_26133b99b8_q.jpg
category_relation:
  - 'y'
  - 'y'
tag_relation:
  - 'y'
  - 'y'
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
ampforwp-amp-on-off:
  - default
pvc_views:
  - 287
use_ampforwp_page_builder:
  - yes
amp-page-builder:
  - '{"rows":[],"totalrows":"1","totalmodules":"1","settingdata":{"front_class":"","front_css":""}}'
primary_category:
  - 2
keni_layout_post:
  - layout-basic
keni_layout_post_sidebar:
  - layout-sidebar-basic
keni_layout_post_navigation:
  - layout-navigation-show
keni_primary_category_post:
  - 2
keni_relation_post:
  - 'a:0:{}'
keni_post_fb_time:
  - 1568382265
  - 1568382265
categories:
  - AMP
  - Google Blogger

---
GoogleBloggerはAMPに対応していません。何でなんだろう？素朴な疑問（文句ではありません、Google神様）

### WordPressでなくGoogleBloggerを選ぶ理由

WordPressはこのブログも使っているけど量産しようと思った時にまともなレンサバを借りるとお金たくさんかかります。
  
ドメインの取得や更新にもお金がかかります。ブログはじめてからアクセスが流れるのも時間がかかります。AMPに対応させるにはこのブログでもやっている様にプラグイン一つで簡単なのでお金に糸目を付けなければWordPress一択でも良いのですが、現実的にそうもいかないので、全ての面で最も経済的なBloggerになって訳です。

#### BloggerのAMP対応テーマ

これは当初予想していたよりも多くあります。
  
素に今お使いのテーマをAMP化したいならば以下の沿ってお試し下さい。

<pre class="lang:vim decode:true ">https://amprandom.blogspot.com/p/amp-blogger.html</pre>

以下は当方がテンプレートを探す際に利用したBingの検索キーワードです。

<pre class="lang:vim decode:true ">https://www.bing.com/search?q=google+blogger+amp+theme++language%3Aes&qs=n&form=QBRE&sp=-1
&pq=google+blogger+amp+theme+language%3Aes&sc=0-36&sk=
&cvid=E847C74DEF784AF2AF014738AE6AB5D9

こちらは色々なダウンロードリンクです。

https://amptemplates.com/downloads/
</pre>

スペインではGoogleBloggerは人気なのでしょうか？

<pre class="lang:vim decode:true">https://ampblogbuild.blogspot.com/

ただ、何処を探してもテンプレートソースの公開場所が分かりません。一旦は探してダウンロードしたはずなのですがね。

このテンプレートを元にテストブログを1つ作成して、そこから本番への適用しました。
以下がテストブログです。

https://testbloggeramp2018.blogspot.com/

</pre>

↑のテンプレートを使わせて頂き作業を進めました。

#### Blogger AMP テンプレートの設置

以下の手順で進めます。

先ず、↑で試したいBloggerのテーマをダウンロードしておきます。

<img class="alignnone size-full wp-image-315" src="https://okanemochi.tk/wp-content/uploads/2018/06/blogger001.png" alt="" width="880" height="592" />

<img class="alignnone size-large wp-image-316" src="https://okanemochi.tk/wp-content/uploads/2018/06/blogger002-1024x489.png" alt="" width="1024" height="489" />

&nbsp;

<img class="alignnone size-large wp-image-317" src="https://okanemochi.tk/wp-content/uploads/2018/06/blogger003.png" alt="" width="602" height="412" />

テーマをダウンロードすれば今のテーマをローカルにバックアップ（ダウンロード）出来ます。

新しいテーマを適用するにはファイルを選択してアップロードすればOKです。

&nbsp;

 <img class="alignnone size-large wp-image-318" src="https://okanemochi.tk/wp-content/uploads/2018/06/blogger004.png" alt="" width="946" height="533" /><img class="alignnone size-large wp-image-319" src="https://okanemochi.tk/wp-content/uploads/2018/06/blogger005-1024x728.png" alt="" width="1024" height="728" />

&nbsp;

#### AMP化について行った事

今回利用させて頂いた「AMP Blogger design」が他と比べて何が優れていたのか？と言えば、レイアウトの工夫です。GoogleBloggerがAMPに対応していない理由というか、何処がどういう風に対応していないのか？その部分について「AMP Blogger design」は見事にクリアしていたのです。

具体定には、

ガジェットを構成する「画面上でのデータの見せ方」と「コードの定義し直し」です。

##### 画面上でのデータの見せ方

例えば、アーカイブガジェットは「フラットリスト」の一択です。階層とかブルダウンにするとコードに画像参照やエラーを引き起こすタグが侵入します。なので、フラットリストのみ選択させ、6月 2018 (10)などをクリックすると、その一覧のリストがメイン画面に表示されます。

ラベルに関しては同じでクリック動作は全てメイン画面に対して行います。このあたりを徹底的にやっているのではじめてまともに100％AMP対応のBloggerが作成出来ました。

##### コードの定義し直し

こちらは当方もこれから勉強するところなのですが、Bloggerはエリアを細かく定義する事が可能です。

<pre class="lang:vim decode:true">body#layout #Gadget-menu-1{*****************************************************}
body#layout #Gadget-social {****************************************************}</pre>

例えばこんな感じに定義していきます。

Gadget-menu-1とかGadget-socialはレイアウトで色々と設定出来るあのガジェットの名前とその定義です。

このあたりを上手に定義する事でAMPにエラーを出さない様にガジェットを定義していきます。

&nbsp;

### 実際に記事を書く時に注意する事

  1. アイキャッチ画像は必ず挿入する
  2. 対応しているタグ以外は使わない

要はこの2つなのですがなかな大変です。

<pre class="lang:vim decode:true ">&lt;div class="separator" style="clear: both; text-align: center;"&gt;
&lt;a href="https://2.bp.blogspot.com/-J-chVT1S0kA/WxY3YZCuN_I/AAAAAAAABnI/XHy1pLVWhys0Mt8ciCGMo_v8YyAf5U4VQCPcBGAYYCw
/s1600/6191634300_da7eab2476_m.jpg"
 imageanchor="1" style="margin-left: 1em; margin-right: 1em;"&gt;&lt;img border="0" data-original-height="240" 
data-original-width="240" 
src="https://2.bp.blogspot.com/-J-chVT1S0kA/WxY3YZCuN_I/AAAAAAAABnI/XHy1pLVWhys0Mt8ciCGMo_v8YyAf5U4VQCPcBGAYYCw/
s1600/6191634300_da7eab2476_m.jpg" /&gt;
&lt;/a&gt;&lt;/div&gt;
&lt;br /&gt;</pre>

普通にBloggerで記事に画像挿入すると↑の様になります。これを↓の様に修正します。

<pre class="lang:vim decode:true">&lt;noscript&gt;
&lt;a href="https://2.bp.blogspot.com/-J-chVT1S0kA/WxY3YZCuN_I/AAAAAAAABnI/XHy1pLVWhys0Mt8ciCGMo_v8YyAf5U4VQCPcBGAYYCw/
s1600/6191634300_da7eab2476_m.jpg"&gt;
&lt;img height="240" width="240" 
src="https://2.bp.blogspot.com/-J-chVT1S0kA/WxY3YZCuN_I/AAAAAAAABnI/XHy1pLVWhys0Mt8ciCGMo_v8YyAf5U4VQCPcBGAYYCw/
s1600/6191634300_da7eab2476_m.jpg" /&gt;&lt;/a&gt;
&lt;/noscript&gt;</pre>

画像はアイキャッチ専用となり記事エリアには表示されません。

もし、アイキャッチと記事内の両方に画像を表示するなら↑にコードでなく、

<pre class="lang:vim decode:true ">&lt;amp-img height="240" width="240" 
src="https://2.bp.blogspot.com/-J-chVT1S0kA/WxY3YZCuN_I/AAAAAAAABnI/
XHy1pLVWhys0Mt8ciCGMo_v8YyAf5U4VQCPcBGAYYCw/s1600/6191634300_da7eab2476_m.jpg"&gt;&lt;/amp-img&gt;
</pre>

&nbsp;

こう書きます。

  1. aタグを使う場合はnoscriptで囲む
  2. 画像を単に表示するならamp-imgタグを使う

基本的にjavascriptが使えません。なのでアクセス解析ツールもGoogle Analyticsもコードを成形したかたちでないと使えない様です。

### まとめ

Googleがこれだけ推奨しているAMPをWordPressで実装するのは簡単なので興味のある人が試すと良いかも知れません。それにしても、AMP環境でアフィリエイトするなら圧倒的にBloggerよりもWordPressの方が比べられない程、楽な事を、この記事を書きながら思い知りました（あちゃ～！！）

でも、GoogleBloggerなら無料でSEOにもかなり強く、カスタマイズさえしっかりすれば何とかなりそうな気もしています。WordPressで量産出来る様になるまではBloggerでのAMP化を継続してやっていこうと思います。

それではありがとうございました。

&nbsp;

## 追記（カスタマイズ Knowhow)

<pre class="lang:xhtml decode:true ">【その１】
テンプレートのカスタマイズ時に新規ガジェットと追加すると、ガジェットの編集アイコンの絵が
表示されて、これがAMPのエラーになります。その解消方法です。

&lt;b:include name='quickedit'/&gt;
　　　　　　　↓
&lt;!-- &lt;b:include name='quickedit'/&gt; --&gt;

コメントアウトする事で編集アイコンの表示を無効に出来る

【その２】
Error:
The text inside tag 'style amp-custom' contains 'html comments', which is disallowed.

この場合はCSS領域にHTMLコメント記述が混入している場合に起こるエラーの様

&lt;!-- .header-AdSense{float:right;width:563px;height:90px} --&gt;
CSS領域で↑の様に書いたら怒られるらしい。
/* .header-AdSense{float:right;width:563px;height:90px} */
こうすればOK

【その３】
今回利用させていただいたGoogleBlogger用のAMP対応テンプレートは「https://www.ayudadeblogger.com/」よりダウンロードさせていただいております。
無料版と有料版があり、無料版は一見何の遜色もない様に見受けられますが、カスタマイズしていくと色々と壁ぶち当たります。

各テンプレートのより「？」と思う箇所が異なるのですが、「アーティクルのタイトルが入らない（h3で投稿者と日時だけ）」とか、ページを開いた際にはヘッダスペースががら空きになって見栄えが極端に悪くなったりします。

無料でお試しなので気にったら有料を買ってね！って事なのでこれはこれで良いのです。なので、カスタマイズして思うようにリメイクするには努力と根気が必要そうです。

当方も有料を買おうと思ったのですが、お相手はスペインの人で、まずはメールで連絡して、その後に何らかの送金手段で購入する様に感じます。paypalで払えるなら直ぐに購入するのですが、、、、。
</pre>

<pre class="lang:xhtml decode:true">偏差値 公立高校名     種別
74     大宮         （理数）
73     県立浦和     （普通）
72     浦和第一女子 （普通）

↑の様なTSV形式をBloggerに表として記載する場合、簡単なのが、GoogleDocsやGoogleSpredsheetに
表として作成してコピーし、ブロガー上で貼り付ければテーブルが完成します。

ところがそれだとAMPには未対応のタグなどたくさん入り使えません。


http://styleme.jp/tool/xls2html/#close
こちらのサービスを利用させて頂く事で、ほぼAMPで使えるTABLEタグが生成されます。
（先頭のstyle定義に部分はカットします）

&lt;style&gt;
table {
border-collapse: collapse;
}
th {
border: solid 1px #666666;
color: #000000;
background-color: #ff9999;
}
td {
border: solid 1px #666666;
color: #000000;
background-color: #ffffff;
}
&lt;/style&gt;
&lt;table&gt; &lt;thead&gt;
&lt;tr&gt; &lt;th&gt;
偏差値&lt;/th&gt; &lt;th&gt;
公立高校名&lt;/th&gt; &lt;th&gt;
種別&lt;/th&gt; &lt;/tr&gt;
&lt;/thead&gt; &lt;tbody&gt;
&lt;tr&gt; &lt;th&gt;
74&lt;/th&gt; &lt;td&gt;
大宮（理数）&lt;/td&gt; &lt;td&gt;
（理数）&lt;/td&gt; &lt;/tr&gt;
&lt;tr&gt; &lt;th&gt;
73&lt;/th&gt; &lt;td&gt;
県立浦和（普通）&lt;/td&gt; &lt;td&gt;
（普通）&lt;/td&gt; &lt;/tr&gt;
&lt;tr&gt; &lt;th&gt;
72&lt;/th&gt; &lt;td&gt;
浦和第一女子（普通）&lt;/td&gt; &lt;td&gt;
（普通）&lt;/td&gt; &lt;/tr&gt;
&lt;/tbody&gt; &lt;/table&gt;

素晴らしいです。</pre>

<pre class="lang:xhtml decode:true ">構造化テストツールのエラー

datePublished   
6:00:00 (値「6:00:00」は日時として解析できません。詳しくは、日時形式についての説明をご覧ください。)
canceldateModified  
6:00:00 (値「6:00:00」は日時として解析できません。詳しくは、日時形式についての説明をご覧ください。)

対応策は、

テーマ-&gt;HTML編集より
datePublishedを検索する

出てきた箇所、
itemprop='datePublished'&gt;&lt;data:post.timestamp/&gt;&lt;/abbr&gt;

などを、

itemprop='datePublished'&gt;&lt;data:post.timestampISO8601/&gt;&lt;/abbr&gt;
と変更する、出てきた箇所は全て(4箇所前後）変更した方が良い。

この変更をすると日時の表示が和暦から西暦表示になってしまうが、現状では構造化データのテストでエラーを出さない方法は
これ以外見つかっておりません。
</pre>

&nbsp;

&nbsp;