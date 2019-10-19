---
title: Chatwork APIによる指定場所への書き込み
author: スフィア
type: post
date: 2018-06-01T22:14:49+00:00
url: /computer_language/gas/265/
featured_image: https://okanemochi.tk/wp-content/uploads/2018/06/6185878460_81212fcc99_q.jpg
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
  - 94
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
  - 1566495282
  - 1566495282
  - 1566495282
categories:
  - GAS

---
<pre class="lang:js decode:true ">// チャットワークAPIのAPIトークン
var api_token = 'チャットワークのAPIトークン';

// 送信先のチャットのID
var room_id = 送信先のチャットのID;

//メール送信先のアドレス
var toEmail = "メール送信先のアドレス";

//チャットワーク＆メールの本文
var txtbody = "処理が完了しました。インポートをお願いします。";

//チャットワーク＆メールのタイトル
var ss = SpreadsheetApp.getActiveSpreadsheet();
var subject = "【" + ss.getName() + "】";

function main() {

var cw = ChatWorkClient.factory({
token: api_token
});
var body = "[info][title]" + subject + "[/title]" + txtbody + "[/info]";
cw.sendMessage({
room_id: room_id,
body: body
});
sendMailForm();
Browser.msgBox('チャットワークへのメッセージ送信完了しました。');
}

/************************************************************************************
【関数概要】sendMailForm

メールを送信する。
引数のresultDataはメールのボディーに当たる内容

【引数】resultData

【戻り値】なし
***********************************************************************************/
function sendMailForm() {

// メール送信
try {
MailApp.sendEmail(toEmail, subject, txtbody);
} catch (e) {
var error = e;
Logger.log("message:" + error.message + "\nfileName:" + error.fileName + "\nlineNumber:" + error.lineNumber + "\nstack:" + error.stack);
}

}</pre>

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