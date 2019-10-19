---
title: AMP対応ページでのMatomoアクセス解析 by Google Blogger
author: スフィア
type: post
date: 2018-06-17T07:06:09+00:00
url: /web_tecnology/google-amp/368/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/06/4517201939_10217eee03_q.jpg
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
  - 282
primary_category:
  - 83
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
  - 1568363937
categories:
  - AMP
  - Google Blogger

---
Google アナリティクスに関しては以下の様にすれば、WordPressでもGoogleBloggerでも機能します。

<pre class="lang:xhtml decode:true">&lt;!-- Google Analytics --&gt;
&lt;amp-analytics id='analytics1' type='googleanalytics'&gt;
&lt;script type='application/json'&gt;
{
  &quot;vars&quot;: {
    &quot;account&quot;: &quot;UA-xxxxxxxxx-x&quot;
  },
  &quot;triggers&quot;: {
    &quot;trackPageview&quot;: {
      &quot;on&quot;: &quot;visible&quot;,
      &quot;request&quot;: &quot;pageview&quot;
    }
  }
}
&lt;/script&gt;
&lt;/amp-analytics&gt;</pre>

↑の様にアナリティクスIDを設定したタグを貼り付ければOKです。

（通常に生成されるアナリティクスコードとは異なるので注意が必要です）

&nbsp;

WordPressならばプラグインの「AMPforWP 」を使えば、通常のjavascript解析（例えば、https://matomo.jp/）のタグも機能しています。

ですがGoogleBloggerの場合はWordPressの様な便利なプラグインは無いのでそのままでは機能しません。

調査したらここに答えがありました。

https://forum.matomo.org/t/how-to-add-piwik-to-amp-pages/18424/4

<pre class="lang:xhtml decode:true ">&lt;script async src="https://cdn.ampproject.org/v0/amp-analytics-0.1.js" custom-element="amp-analytics"&gt;&lt;/script&gt;</pre>

↑のコードをヘッダに貼り付けます。

<pre class="lang:xhtml decode:true ">&lt;amp-analytics&gt;&lt;script type="application/json"&gt;
{
    "triggers": {
        "trackPageview": {
            "on": "visible",
            "request": "pageview"
        }
    },
    "requests": {
        "base": "<strong>https://piwik.example.org/</strong>piwik.php?idsite=1&rec=1&action_name=${title}&url=${sourceUrl}&rand=${random}&apiv=1&urlref=
        ${documentReferrer}&res=${screenWidth}x${screenHeight}&lang=${browserLanguage}
        &gt_ms=${serverResponseTime}&cs=${documentCharset}
        &_cvar={\"1\":[\"errorName\",\"${errorName}\"],\"2\":[\"errorMessage\",\"${errorMessage}\"]}",
        "pageview": "${base}"
    }
}
&lt;/script&gt;&lt;/amp-analytics&gt;</pre>

↑のコードをbodyタグ直下付近に貼ります。

但し、↑の「https://piwik.example.org」の部分が自分でインストールしたMatomoの環境に合わせて書き換えが必要です。

コード内の&記号を&に書き換える必要がある場合もあります。

加えて、通常のMatomoのコードはheadタグの終わりに書くのですが、こちらはBodyタグ内なので注意が必要です。

Googleアナリティクスは凄いとは思いますがリアルタイム解析が苦手です、Matomoであればそのあたりも充実しているので大変便利に使わさせて頂いております。

&nbsp;

<a href="https://px.a8.net/svt/ejp?a8mat=2ZH6XJ+E4HG5E+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fudemy-images.udemy.com%2Fcourse%2F240x135%2F647944_cb57_2.jpg" target="_blank" rel="nofollow noopener">今日から実践で使える！Google アナリティクス講座</a>
  
<img src="https://www12.a8.net/0.gif?a8mat=2ZH6XJ+E4HG5E+3L4M+BW8O2" alt="" width="1" height="1" border="0" />

&nbsp;