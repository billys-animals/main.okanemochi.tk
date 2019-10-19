---
title: UrlFetchApp.fetch時のオプション値一覧
author: スフィア
type: post
date: 2018-05-31T21:44:55+00:00
url: /computer_language/gas/256/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/06/12456439485_40f1cba05d_q.jpg
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
  - 455
ampforwp-amp-on-off:
  - default
keni_layout_post:
  - layout-basic
keni_layout_post_sidebar:
  - layout-sidebar-basic
keni_layout_post_navigation:
  - layout-navigation-show
keni_primary_category_post:
  - 6
keni_relation_disp_post:
  - show
keni_category_relation_post:
  - 1
keni_tag_relation_post:
  - 1
keni_relation_post:
  - 'a:0:{}'
keni_post_fb_time:
  - 1568355613
categories:
  - GAS

---
GASでURLなどにアクセスして情報取得する際などに良く利用するUrlFetchApp.fetchを使うオプション値を貼り付けておきます。

#### パラメーター

<div class="devsite-table-wrapper">
  <table class="function param">
    <tr>
      <th>
        名
      </th>
      
      <th>
        タイプ
      </th>
      
      <th>
        説明
      </th>
    </tr>
    
    <tr>
      <td>
        <code>url</code>
      </td>
      
      <td>
        <code>String</code>
      </td>
      
      <td>
        フェッチするURL
      </td>
    </tr>
    
    <tr>
      <td>
        <code>params</code>
      </td>
      
      <td>
        <code>Object</code>
      </td>
      
      <td>
        以下に定義されている高度なパラメータを指定するオプションのJavaScriptオブジェクト
      </td>
    </tr>
  </table>
</div>

#### 高度なパラメータ

<div class="devsite-table-wrapper">
  <table class="function advancedparam">
    <tr>
      <th>
        名
      </th>
      
      <th>
        タイプ
      </th>
      
      <th>
        説明
      </th>
    </tr>
    
    <tr>
      <td>
        <code>contentType</code>
      </td>
      
      <td>
        <code>String</code>
      </td>
      
      <td>
        コンテンツタイプ（デフォルトは &#8216;application / x-www-form-urlencoded&#8217;）。コンテンツタイプの別の例は &#8216;application / xml; charset = utf-8 &#8216;となります。
      </td>
    </tr>
    
    <tr>
      <td>
        <code>headers</code>
      </td>
      
      <td>
        <code>Object</code>
      </td>
      
      <td>
        要求のHTTPヘッダーのJavaScriptキー/値マップ
      </td>
    </tr>
    
    <tr>
      <td>
        <code>method</code>
      </td>
      
      <td>
        <code>String</code>
      </td>
      
      <td>
        HTTPリクエストのための方法：<code>get</code>、<code>delete</code>、 <code>patch</code>、<code>post</code>、または<code>put</code>。デフォルトは<code>get</code>です。
      </td>
    </tr>
    
    <tr>
      <td>
        <code>payload</code>
      </td>
      
      <td>
        <code>String</code>
      </td>
      
      <td>
        リクエストのペイロード（POST本体など）。特定のHTTPメソッド（GETなど）はペイロードを受け入れません。文字列、バイト配列、またはJavaScriptオブジェクトにすることができます。JavaScriptオブジェクトは、フォームフィールド名から値へのマップとして解釈されます。値は、文字列またはブロブのいずれかです。
      </td>
    </tr>
    
    <tr>
      <td>
        <code>useIntranet</code>
      </td>
      
      <td>
        <code>Boolean</code>
      </td>
      
      <td>
        推奨されていません。これは、（推奨されない）<a href="http://code.google.com/securedataconnector/">SDCを</a>介してドメインにリンクされたイントラネット内の指定されたURLを解決するためにフェッチを指示します
      </td>
    </tr>
    
    <tr>
      <td>
        <code>validateHttpsCertificates</code>
      </td>
      
      <td>
        <code>Boolean</code>
      </td>
      
      <td>
        これをfalseに設定すると、フェッチはHTTPS要求の無効な証明書をすべて無視します。デフォルトはtrueです。
      </td>
    </tr>
    
    <tr>
      <td>
        <code>followRedirects</code>
      </td>
      
      <td>
        <code>Boolean</code>
      </td>
      
      <td>
        これがfalseに設定されている場合、フェッチはHTTPリダイレクトに自動的に従わない。元のHTTP応答を返します。デフォルトはtrueです。
      </td>
    </tr>
    
    <tr>
      <td>
        <code>muteHttpExceptions</code>
      </td>
      
      <td>
        <code>Boolean</code>
      </td>
      
      <td>
        これに設定されている場合<code>true</code>、応答コードが失敗を示す場合に例外をスローされませんフェッチし、代わりに返されます <code>&lt;a href="https://developers.google.com/apps-script/reference/url-fetch/http-response.html">HTTPResponse&lt;/a></code>（デフォルト：<code>false</code>）
      </td>
    </tr>
    
    <tr>
      <td>
        <code>escaping</code>
      </td>
      
      <td>
        <code>Boolean</code>
      </td>
      
      <td>
        これがに設定されている場合は<code>false</code>、URL内の予約文字（デフォルト：エスケープされません<code>true</code>）
      </td>
    </tr>
  </table>
</div>

<div class="chat_l ">
  <div class="talker">
    <b><img class="square" src="https://okanemochi.tk/wp-content/uploads/2018/07/%E3%82%AB%E3%83%B3%E3%83%8B%E3%83%B3%E3%82%B0-300x204.png" alt="もし、参考になったならTwitterシェアお願いします" />もし、参考になったならTwitterシェアお願いします </b>
  </div>
  
  <div class="bubble_wrap">
    <p>
    </p>
  </div>
</div>